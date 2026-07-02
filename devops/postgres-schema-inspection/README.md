# PostgreSQL Schema Inspection

Explore any PostgreSQL database — list tables, discover columns, estimate row counts, and find indexes. Works even with restricted read-only users that can't access `information_schema`.

## What It Does

When you give your agent PostgreSQL credentials, this skill automatically:

- **Lists all tables** across every schema using `pg_class` (bypasses `information_schema` restrictions)
- **Shows column details** — names, types, nullability, and default values per table
- **Estimates row counts** using `pg_stat_user_tables` for accurate live counts
- **Finds indexes** — which columns are indexed and how
- **Works with read-only users** that lack `information_schema` access

## How to Use

Share your database credentials with your agent and ask it to "inspect the schema" or "show me what tables exist." The agent will connect, query the catalog, and produce a structured report.

No write access needed. The skill only runs read-only catalog queries.

## Why

Most database inspection tools assume full `information_schema` access. Real production setups often give you a restricted read-only user. This skill uses `pg_catalog` directly, which always works as long as you can connect.

## When Not to Use

- If you need to modify the schema, use a migration tool instead
- For performance profiling, use `pg_stat_statements` or an APM
