---
name: DBT/Dagster Project Changes
about: Template for changes Dagster and DBT projects
title: "[Sandworm] "
labels: dbt, dagster
assignees:
paths:
  - 'projects/**'
  - 'pipelines/**
---

## DBT
See documentation about the DBT transformation workflow [here](../dbt_overview_and_setup.md).

- [ ] If adding a new schema, update the [DBT Project](../services/dbt/projects/primary/dbt_project.yml) in the relevant DBT subproject.
- [ ] If adding a new schema, see [Scheduling Models](../dbt_overview_and_setup.md#scheduling-models) for instructions on creating a dagster job
- [ ] New models are documented
- [ ] Screenshot of successful `dbt build` for models affected by this PR (or `dbt test` and `dbt run` separately)
  - [ ] If adding incremental models, include screenshot for both `full-refresh` and incremental runs
  - [ ] If column names, order, or `unique_key` are changed re-run models with --full-refresh
- [ ] Autogen the relevant docs and DBT models using one of the autogen [scripts](../../utils/).
- [ ] If adding a model that materializes in a [location with lightdash tags](../services/dbt/projects/primary/dbt_project.yml), it must have a [config file for lightdash](../lightdash.md#adding-tables)
- [ ] (_optional_) Screenshot of Lightdash Preview if changing a dashboard

## Dagster
- [ ] Screenshot of successful Dagster run. Figure out optimal job concurrency.
- [ ] Link or screenshot of Snowflake data if applicable
- [ ] Create necessary IaC [Snowpipes](../../infra/warehouse/databases.ts) and push data to dev pipes.
- [ ] Add secrets to Infra repo and Env [Template](../../.env.template) or the [AWS secrets manager](https://us-west-2.console.aws.amazon.com/secretsmanager/listsecrets?region=us-west-2#).
- [ ] If Python requirements are modified, re-run Docker Build and ensure all code locations build
