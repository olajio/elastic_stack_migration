# Runtime Service Registry: Setup Instructions

Run these in order, in Kibana Dev Tools.

## Step 1: Create the index

```
PUT /service-registry-source
{
  "mappings": {
    "properties": {
      "service_name":        { "type": "keyword" },
      "application_service": { "type": "keyword" },
      "service_owner":       { "type": "keyword" },
      "routing_team":        { "type": "keyword" },
      "service_tier":        { "type": "keyword" },
      "product":             { "type": "keyword" }
    }
  }
}
```

## Step 2: Insert the Cards data

Note: `routing_team` and `service_tier` are `TBD` placeholders, not final values.

```
POST /service-registry-source/_bulk
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-acquisitions-client" } }
{ "service_name": "omf-cards-acquisitions-client", "application_service": "omf-cards-experience", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-application-service" } }
{ "service_name": "omf-cards-application-service", "application_service": "omf-cards-application-processing", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-astra-service" } }
{ "service_name": "omf-cards-astra-service", "application_service": "omf-cards-application-processing", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-axis-service" } }
{ "service_name": "omf-cards-axis-service", "application_service": "omf-cards-fraud-identity", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-bff-service" } }
{ "service_name": "omf-cards-bff-service", "application_service": "omf-cards-experience", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-ck-bff-service" } }
{ "service_name": "omf-cards-ck-bff-service", "application_service": "omf-cards-experience", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-cms-service" } }
{ "service_name": "omf-cards-cms-service", "application_service": "omf-cards-servicing", "service_owner": "Cards - Servicing", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-collection-decision-service" } }
{ "service_name": "omf-cards-collection-decision-service", "application_service": "omf-cards-collections", "service_owner": "Card Collections & Recovery Digital Engineering", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-collection-delivery-service" } }
{ "service_name": "omf-cards-collection-delivery-service", "application_service": "omf-cards-collections", "service_owner": "Card Collections & Recovery Digital Engineering", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-collections-settlement-service" } }
{ "service_name": "omf-cards-collections-settlement-service", "application_service": "omf-cards-collections", "service_owner": "Card Collections & Recovery Digital Engineering", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-communication-service" } }
{ "service_name": "omf-cards-communication-service", "application_service": "omf-cards-communications", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-creation-service" } }
{ "service_name": "omf-cards-creation-service", "application_service": "omf-cards-application-processing", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-credit-decision-service" } }
{ "service_name": "omf-cards-credit-decision-service", "application_service": "omf-cards-decisioning", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-customer-service" } }
{ "service_name": "omf-cards-customer-service", "application_service": "omf-cards-servicing", "service_owner": "Cards - Servicing", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-data-access-service" } }
{ "service_name": "omf-cards-data-access-service", "application_service": "omf-cards-servicing", "service_owner": "Cards - Servicing", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-dsa-bff-service" } }
{ "service_name": "omf-cards-dsa-bff-service", "application_service": "omf-cards-collections", "service_owner": "Card Collections & Recovery Digital Engineering", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-dsa-settlements-service" } }
{ "service_name": "omf-cards-dsa-settlements-service", "application_service": "omf-cards-collections", "service_owner": "Card Collections & Recovery Digital Engineering", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-ecm-bff-service" } }
{ "service_name": "omf-cards-ecm-bff-service", "application_service": "omf-cards-servicing", "service_owner": "Cards - Servicing", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-enterprise-integration-service" } }
{ "service_name": "omf-cards-enterprise-integration-service", "application_service": "omf-cards-application-processing", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-fraud-decision-service" } }
{ "service_name": "omf-cards-fraud-decision-service", "application_service": "omf-cards-fraud-identity", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-fraud-service" } }
{ "service_name": "omf-cards-fraud-service", "application_service": "omf-cards-fraud-identity", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-id-verification-service" } }
{ "service_name": "omf-cards-id-verification-service", "application_service": "omf-cards-fraud-identity", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-integration-api-service" } }
{ "service_name": "omf-cards-integration-api-service", "application_service": "omf-cards-integration", "service_owner": "Cards Integration Services", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-management-service" } }
{ "service_name": "omf-cards-management-service", "application_service": "omf-cards-servicing", "service_owner": "Cards - Servicing", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-mfr-service" } }
{ "service_name": "omf-cards-mfr-service", "application_service": "omf-cards-fraud-identity", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-nexus-service" } }
{ "service_name": "omf-cards-nexus-service", "application_service": "omf-cards-application-processing", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-orbit-service" } }
{ "service_name": "omf-cards-orbit-service", "application_service": "omf-cards-application-processing", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-otp-service" } }
{ "service_name": "omf-cards-otp-service", "application_service": "omf-cards-fraud-identity", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-plaid-connect-service" } }
{ "service_name": "omf-cards-plaid-connect-service", "application_service": "omf-cards-bank-account-connectivity", "service_owner": "Cards Integration Services", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-plaid-service" } }
{ "service_name": "omf-cards-plaid-service", "application_service": "omf-cards-bank-account-connectivity", "service_owner": "Cards Integration Services", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-prospect-service" } }
{ "service_name": "omf-cards-prospect-service", "application_service": "omf-cards-experience", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-rules-engine-service" } }
{ "service_name": "omf-cards-rules-engine-service", "application_service": "omf-cards-decisioning", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-sentilink-service" } }
{ "service_name": "omf-cards-sentilink-service", "application_service": "omf-cards-fraud-identity", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-simulation-service" } }
{ "service_name": "omf-cards-simulation-service", "application_service": "omf-cards-nonprod-tooling", "service_owner": "Cards Engineering", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-sirius-service" } }
{ "service_name": "omf-cards-sirius-service", "application_service": "omf-cards-fraud-identity", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-starlink-service" } }
{ "service_name": "omf-cards-starlink-service", "application_service": "omf-cards-fraud-identity", "service_owner": "Cards - Acquisition", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
{ "index": { "_index": "service-registry-source", "_id": "omf-cards-test-data-service" } }
{ "service_name": "omf-cards-test-data-service", "application_service": "omf-cards-nonprod-tooling", "service_owner": "Cards Engineering", "routing_team": "TBD", "service_tier": "TBD", "product": "Cards" }
```

## Step 3: Confirm it worked

```
GET /service-registry-source/_count
```

Should return 37.
