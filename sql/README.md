# SQL Scripts

Place SQL Server scripts in this folder, separated by purpose when the project files are available.

Suggested naming:
- `01_create_database_and_schemas.sql`
- `02_create_staging_tables.sql`
- `03_create_warehouse_dimensions.sql`
- `04_create_fact_table.sql`
- `05_load_dimensions.sql`
- `06_load_fact_sales.sql`
- `07_validation_queries.sql`

These are suggested filenames, not existing scripts. Update the list to match the actual files committed.

Scripts should be safe to rerun where practical, document dependencies, and avoid embedding credentials or machine-specific secrets.