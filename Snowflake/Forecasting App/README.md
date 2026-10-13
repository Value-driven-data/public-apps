# Forecasting App

A standalone, **forecasting-only** Snowflake Native App. Clients connect one of their Snowflake
databases, pick a table, and train, compare and run time-series forecast models on it — no custom
code. Runs on **Snowpark Container Services (SPCS)**: a FastAPI backend + a React frontend as two
containers, with all training/prediction executed as Snowpark Python stored procedures on the
consumer's warehouse (the container itself has no ML libraries).

This app was carved out of the larger "021" app. Everything non-forecasting was removed:
BI/dashboards, Integria, the general assistant, the connector helper, nexus, and the regression /
classification / clustering features. Only forecasting remains.

## How it works
1. Connect a data source (database + schema) via the selector.
2. Ingest a dataset — upload a CSV or reference an existing table.
3. The app profiles the table on the warehouse and (optionally) proposes column mapping + a feature plan.
4. Train a model on the warehouse (fast baseline or a full AutoML sweep).
5. Pick and save a candidate, then generate a forecast out to a table.

## Data

No data is shipped in or out of the app. All data is read natively on the customers own account via the native app, hosted on the same account.
