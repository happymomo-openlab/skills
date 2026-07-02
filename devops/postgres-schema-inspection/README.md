Explore any PostgreSQL database — list tables, discover columns, estimate row counts, and find indexes. Works even with restricted read-only users that can't access `information_schema`.

## What It Does

- **Lists all tables** across every schema using `pg_class`, bypassing `information_schema` restrictions
- **Shows column details** — names, types, nullability, and default values per table
- **Estimates row counts** using `pg_stat_user_tables` for accurate live counts
- **Finds indexes** — which columns are indexed and how
- **Works with read-only users** that lack full catalog access

## How to Use

Share your database credentials with your agent and ask it to "inspect the schema" or "show me what tables exist." The agent connects, queries the catalog, and produces a structured report.

## When Not to Use

- For schema modifications, use a migration tool
- For performance profiling, use `pg_stat_statements` or an APM
