# Data Dictionary

This initial dictionary lists fields named in the project report. Confirm spelling, types, nullability, and business meaning against the actual CSV and SQL schemas before using it as a formal contract.

## Source Transaction Fields

| Field | Report-described meaning | Validation notes |
|---|---|---|
| `InvoiceNo` | Invoice or transaction reference | Confirm uniqueness and whether cancellation/return invoices have special prefixes |
| `StockCode` | Product code | Confirm product-key rules |
| `Description` | Product description | May be empty or inconsistent; preserve source value for audit where possible |
| `Quantity` | Quantity on the transaction row | Negative values may represent returns; validate source semantics |
| `InvoiceDate` | Transaction date/time | Confirm parsing format, locale, and timezone assumptions |
| `UnitPrice` | Unit price | Confirm decimal precision and treatment of zero/negative prices |
| `CustomerID` | Customer identifier | Missing values may occur; document the adopted unknown-customer rule |
| `Country` | Customer/order country label | Standardize only with documented mapping rules |

## Warehouse Tables Described

| Table | Intended role | Candidate attributes / measures |
|---|---|---|
| `dw.DimProduct` | Product dimension | Product key, stock code, description |
| `dw.DimCustomer` | Customer dimension | Customer key, customer identifier, customer attributes |
| `dw.DimDate` | Date dimension | Date key and calendar attributes |
| `dw.DimCountry` | Country dimension | Country key and country name |
| `dw.FactSales` | Transaction fact | Invoice reference, dimension keys, quantity, unit price, total amount |

## Add Confirmed Schema Details

After adding the SQL scripts, record the real data types, primary keys, foreign keys, identity columns, constraints, calculated fields, and default values. Distinguish source columns from derived columns and measures.