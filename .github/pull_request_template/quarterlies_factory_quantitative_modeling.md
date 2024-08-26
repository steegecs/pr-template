---
name: Quarterlies Factory - Quantitative Modeling
about: Template for changes to the Quantitative Modeling project
title: "[Sandworm]"
labels: dbt, sandworm
assignees:
paths:
  - 'projects/sandworm/**'
---

## Quarterlies Factory - Quantitative Modeling
- [ ] Create metrics models for data source
    - Only 1 metrics model for each set of primary keys.
    - Model name follows template -> mart_research__<data-source>__metrics_by_<primary-key>_<1d, 1w, 1m, etc>.
    - Materialized as table or incremental
    - ORDER BY <primary-key> in output
    - Includes project_slug, data_source & finer Directus entity mappings (network_slug, protocol_slug, etc.)
    - In DBT config post_hook:
        - -> "ALTER TABLE {{ this }} ADD PRIMARY KEY (…, …);"
        - -> "{{ apply_tags('search_sandworm', 'enabled') }}"
        - -> "{{ utils.set_table_comment(this, '') }}"
        - -> "{{ utils.set_multiple_column_comments(this, {}) }}

- [ ] Create at least 1 viz model for each set of metrics
    - Default to include all metrics for this source from the Protocol Reporting repo.
        - Break down metrics into viz models that make them useful for comparative analysis.
    - Materialized as view.
    - Includes project_slug & data_source at least.
    - Column names follow analyst-friendly conventions: total_usd AS "Total TVL (USD)".
        - See the Protocol Reporting repo for reference.
    - In DBT config post_hook:
        - -> "{{ apply_tags('dataviz', 'chart') }}",
        - -> "{{ apply_tags('mapped_directus_slug', '<DIRECTUS_DATASOURCE_SLUG>') }}",
        - -> "{{ utils.set_table_comment(this, '') }}"
        - -> "{{ utils.set_multiple_column_comments(this, {}) }}
- [ ] Add metrics to the quantitative metrics mastersheet.
