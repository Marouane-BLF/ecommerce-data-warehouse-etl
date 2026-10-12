# SSIS ETL Workflow

## Source-to-Staging Package

The project report describes an SSIS package named `DW_Ecommerce_ETL` and a Data Flow Task named **Load CSV to Staging**.

The workflow described is:

1. Read the source CSV using a Flat File Connection Manager.
2. Apply data conversion to selected numeric and text columns.
3. Map the converted outputs to SQL Server staging columns.
4. Load data to `stg.Transactions_Stg`.
5. Verify the loaded sample and row counts in SSMS.
6. Route or record rejected records for review where configured.

## Data Conversion Described

The report mentions these conversions:
- `Quantity` to a signed 4-byte integer.
- `UnitPrice` to a numeric decimal type.
- Text columns such as `Description` and `Country` to Unicode strings where required by the SQL Server destination.

Confirm final aliases, precision, scale, string lengths, and mappings from the actual SSIS package.

## Error Handling

The report describes a staging error table `stg.Errors` and also mentions redirecting errors to an `errors.csv` file during testing. Confirm which error path is active in the final package and document the rejected-row schema, source task, and reason for each reject.

## Warehouse Load Order

The report describes dimension loads for product, customer, country, and date, followed by the `FactSales` load. Fact loading generally depends on successfully resolving dimension keys. Confirm the real lookup logic and handling for unknown dimension members in the package and SQL.

## Validation Checklist

- [ ] Confirm the source file path and delimiter.
- [ ] Check column names and metadata match the CSV.
- [ ] Confirm conversions and numeric precision.
- [ ] Compare source and staging row counts.
- [ ] Review error outputs and rejected records.
- [ ] Validate dimension uniqueness and key generation.
- [ ] Check fact foreign keys and total amount calculations.
- [ ] Reconcile total amounts against a source-level query.
- [ ] Record package execution outcome and load time.

The report contains a historical test result of 611 loaded rows and 170 rejected rows; treat that only as a run-specific figure from the report, not a guaranteed result for a refreshed dataset.