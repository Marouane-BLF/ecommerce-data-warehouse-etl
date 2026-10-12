# Architecture

## End-to-End Flow

The project report describes an on-premises Microsoft BI workflow:

1. **Source:** e-commerce transaction data in CSV format.
2. **Ingestion:** an SSIS Flat File Connection Manager and Flat File Source read the file.
3. **Transformation:** SSIS Data Conversion components normalize selected data types before insertion.
4. **Staging:** SQL Server stores the loaded source rows under the `stg` schema.
5. **Warehouse:** modeled facts and dimensions are stored under `dw`.
6. **Analytics:** SSAS provides the analytical layer described by the project.
7. **Reporting:** Power BI connects to the analytical data to explore sales and customer behavior.

## Logical Data Model

The project report identifies a star schema:

- `dw.FactSales` — measures and dimension keys.
- `dw.DimProduct` — product identifiers and descriptions.
- `dw.DimCustomer` — customer identifier and attributes.
- `dw.DimDate` — date hierarchy/attributes.
- `dw.DimCountry` — country-level geography.

The precise key design, model type, relationships, and deployment settings must be confirmed from the SQL scripts and SSAS project.

## Design Principles

- Keep source ingestion separate from warehouse modeling.
- Explicitly handle string encoding and numeric conversions.
- Preserve a traceable route for rejected data where implemented.
- Load dimensions before facts when fact rows depend on dimension keys.
- Validate row counts and measures at each stage.
- Keep connection settings environment-specific and avoid committing secrets.

## Current Repository State

The architecture is documented from the uploaded project report and solution-file names. Add the actual `.dtproj`, `.dtsx`, `.smproj`, SQL, model, and report files to verify the executable implementation.