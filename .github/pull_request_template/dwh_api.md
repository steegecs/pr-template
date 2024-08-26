---
name: DWH API Changes
about: Template for changes to DWH API
title: "[Sandworm] "
labels: dbt, dwh_api
assignees:
paths:
  - 'projects/dwh_api/**'
---

## DWH API
- [ ] Update Data Warehouse (DWH) API [repository](https://github.com/messari/dwh-api-service):
    - Add or modify time-series and screener catalogs to reflect any data model changes made in this Pull Request (PR)
    - Include a link to the corresponding PR in the DWH API repository
- [ ] Verify data types:
    - Ensure all entity IDs are strings
    - Confirm timestamps are in UTC and use TIMESTAMP_NTZ or TIMESTAMP_TZ data types
- [ ] Check model naming conventions:
    - Screener dataset schema named SCREENER_<dataset name>
    - Time-series models suffixed with granularity (e.g., _1D, _30D, _15M)
- [ ] Validate entity model:
    - Includes ENTITY JSON blob with necessary entity information
    - Contains only qualitative information, no metrics
- [ ] For time-series models:
    - Contains an ID field that alone serves as the primary key with TIME.
    - Verify TIME column exists and is properly time-truncated
    - Confirm ENTITY JSON blob is present with relevant entity information
