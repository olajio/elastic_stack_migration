# Removing a Node from an Elasticsearch Cluster

## 1. Confirm cluster health first
Before touching anything, check cluster health and confirm status is `green` with `unassigned_shards: 0`. Never start a node removal against a yellow or red cluster.

```
GET _cluster/health
```

## 2. Exclude the node from shard allocation
Tell Elasticsearch to start moving the node's shards elsewhere without stopping anything yet.

```
PUT _cluster/settings
{
  "transient": {
    "cluster.routing.allocation.exclude._name": "<node-name>"
  }
}
```

## 3. Watch shards drain off the node
Poll until the node shows 0 shards. For a data-heavy node this can take a while depending on shard size and network throughput between nodes.

```
GET _cat/shards?v
GET _cat/allocation?v
```

## 4. If it's a master-eligible node, add a voting exclusion
Skip this step for data-only/ingest nodes. This lets the remaining masters safely drop the node from the voting configuration without risking a quorum problem.

```
POST /_cluster/voting_config_exclusions?node_names=<node-name>
```

## 5. Stop Elasticsearch on the node
Once the node holds zero shards (and the voting exclusion is in place, if applicable):

```
systemctl stop elasticsearch
```

Immediately re-check cluster health — it should stay `green`.

## 6. Verify the node is gone and cluster is stable
- `GET _cat/nodes?v` should no longer list it.
- For a master node, check `GET _cat/master` to confirm a leader is still elected.
- Confirm node count and master-eligible count match what you expect.

## 7. Clean up voting exclusions (masters only)
Once the master node is confirmed gone, remove the exclusion so future master changes aren't blocked by a stale entry.

```
DELETE /_cluster/voting_config_exclusions
```

## 8. Remove from LB, DNS, and monitoring
- Pull the node from any load balancer upstream pool it was in
- Remove its DNS/Infoblox record
- Drop it from alerting/dashboards
- Power off or reclaim the VM

---

**Notes for the current migration:**
- Master-eligible nodes (e.g. `evelkmnn01`/`evelkmnn03`) need the voting-exclusion step (4 and 7).
- Data-only nodes (e.g. `evelkwkn01`/`evelkwkn02`) can skip straight from allocation exclusion → drain → stop.
- Hold off removing additional masters until `evelkmnn02`'s absence and `evelkwkn03`'s disabled state are understood — avoid draining a third master while a fourth is unexplained.
