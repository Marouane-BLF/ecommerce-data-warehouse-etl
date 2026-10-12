# E-commerce Data Warehouse & Business Intelligence

An end-to-end Business Intelligence portfolio project using the Microsoft data platform. The project is designed around an e-commerce transaction dataset and brings together ETL development with **SQL Server Integration Services (SSIS)**, dimensional data warehousing in SQL Server, analytical modeling with **SQL Server Analysis Services (SSAS)**, and reporting with **Power BI**.

> **Project status:** Documentation and repository structure are being prepared. The original Visual Studio solution files, PBIX reports, and source CSV have been provided, but the complete SSIS/SSAS project folders and packages still need to be added before this repository can be reproduced end to end.

## Objectives

- Ingest e-commerce transaction data from a CSV source.
- Use SSIS to build repeatable extract, transform, and load workflows.
- Separate raw/staging data from the dimensional data warehouse.
- Organize transactions for analysis using a star-schema approach.
- Provide an analytical layer with SSAS and dashboards with Power BI.
- Track data-quality issues and validate loaded data before reporting.

## Architecture Overview

```text
E-commerce transaction CSV
          |
          v
SSIS / Flat File Source
          |
          v
Data Conversion & validation
          |
          v
SQL Server staging schema (stg)
          |
          v
Dimensional data warehouse (dw)
  |       |       |       |
  v       v       v       v
Product Customer Date  Country
             |   /
          FactSales
              |
              v
          SSAS model
              |
              v
          Power BI reports
```

The architecture diagram reflects the workflow described in the project report. Confirm exact package tasks, SSAS model type, relationships, and report connections from the project files before treating every component as fully implemented.

## Technology Stack

| Technology | Role |
|---|---|
| SQL Server | Relational storage, staging, and data warehouse |
| SQL Server Integration Services (SSIS) | CSV ingestion, conversions, and ETL orchestration |
| SQL Server Management Studio (SSMS) | Database setup, SQL scripts, and validation queries |
| SQL Server Analysis Services (SSAS) | Analytical model / semantic layer |
| Power BI Desktop | Interactive reporting and data visualization |
| Visual Studio / SSIS and SSAS extensions | Development environment |
| CSV | Source-data format |

## Data Model

The project report describes a star schema with a central `FactSales` table and four dimensions:

- `DimProduct` — product code and description.
- `DimCustomer` — customer identifiers and attributes.
- `DimDate` — date attributes for time-based analysis.
- `DimCountry` — geographic analysis by country.

The described fact table includes invoice reference, dimension keys, quantity, unit price, and a total amount calculated from quantity and unit price. Verify actual SQL definitions and load logic in the scripts before relying on the model details.

## Source Dataset

The report identifies the input as an e-commerce transactions CSV with fields such as `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, and `Country`.

The exact upstream dataset URL and license should be recorded after confirming the original source. Do not assume that a Kaggle hosting page alone guarantees any particular data license.

## Repository Structure

```text
ecommerce-data-warehouse-etl/
├── README.md
├── docs/
│   ├── architecture.md
│   ├── data-dictionary.md
│   ├── etl-workflow.md
│   └── setup-and-validation.md
├── sql/
│   └── README.md
├── ssis/
│   └── README.md
├── ssas/
│   └── README.md
├── powerbi/
│   └── README.md
├── data/
│   ├── raw/
│   │   └── README.md
│   └── sample/
│       └── README.md
└── screenshots/
    └── README.md
```

## Getting Started

1. Install compatible versions of SQL Server, Visual Studio, the SSIS Projects extension, and any SSAS extension required by the supplied projects.
2. Create the database and staging/warehouse schemas using the SQL scripts provided in `sql/` once added.
3. Update local file paths and SQL Server connection settings in the SSIS project.
4. Run the source-to-staging package and review row counts and rejected records.
5. Load dimensions before loading the fact table, respecting the dimension-key dependencies.
6. Deploy or process the SSAS model, then connect Power BI to the configured analytical source.
7. Validate KPI totals against SQL queries and the source data.

These steps are a general execution outline. Exact commands and the required order may change when the full project files are added.

## Data Quality & Validation

The accompanying project report discusses:
- Data type conversion for quantities, prices, and text fields.
- Handling missing customer information and invalid dates.
- Treating negative quantities as potential returns rather than automatically assuming they are invalid sales.
- Tracking rejected rows for review.
- Checking staging loads using SQL queries.
- Validating warehouse keys and aggregate sales totals.

Data cleaning decisions should follow the real business rules and source dataset. In particular, do not remove negative quantities without verifying whether they represent product returns or credit transactions.

## Reports & Screenshots

Add screenshots of the actual SSAS model, SSIS control/data flows, and Power BI report pages in `screenshots/`. Use filenames documented in the folder README and avoid screenshots containing credentials or private server details.

## Limitations & Reproducibility

- This repository currently starts with documentation; the full source project folders must still be committed.
- Local server names, absolute file paths, and credentials must be replaced with configurable local settings.
- The source dataset license and precise version must be confirmed.
- Validate all KPI formulas and row counts from the executable project before publishing numerical findings.

## Author

**Marouane Boulifa**  
[GitHub profile](https://github.com/Marouane-BLF)
