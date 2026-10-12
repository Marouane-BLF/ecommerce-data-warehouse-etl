# SQL Server Integration Services (SSIS)

Place the SSIS Visual Studio project and all required packages in this folder. The uploaded solution file references `DW_Ecommerce_ETL.dtproj`; include that project file and its `.dtsx` package files to make the repository reproducible.

## Workflow Described in the Project Report

- Flat File Connection Manager reads the e-commerce CSV.
- A Data Flow Task named `Load CSV to Staging` performs source-to-staging ingestion.
- Data Conversion handles numeric and text metadata differences.
- OLE DB Destination inserts rows into `stg.Transactions_Stg`.
- Errors are intended to be captured for review; verify whether the package uses a SQL error table, redirected file output, or both.

## Before Publishing

Remove machine-specific paths, check project parameters and connection managers for secrets, and document how to configure a local SQL Server connection. Add package names and screenshots after confirming the actual project contents.