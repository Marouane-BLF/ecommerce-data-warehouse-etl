# Setup & Validation

## Required Tools

The uploaded solution files indicate Visual Studio 2022-era project formats and SQL Server BI projects. Install versions of SQL Server, Visual Studio, and the relevant SSIS/SSAS project extensions that are compatible with the actual project targets.

Potential tools in the described workflow:
- SQL Server Database Engine
- SQL Server Management Studio (SSMS)
- Visual Studio with SQL Server Integration Services Projects extension
- Analysis Services project extension appropriate to the supplied `.smproj`
- Power BI Desktop

Compatibility may depend on target server versions, project extensions, and whether the SSAS model is multidimensional or tabular. Confirm the model type before configuring deployment.

## Local Configuration

1. Put the source CSV in a local data directory.
2. Update the Flat File Connection Manager to use your local CSV path.
3. Configure the OLE DB connection to the local SQL Server instance and database.
4. Execute the SQL setup scripts after they are added to the repository.
5. Run staging ingestion and verify rejected records.
6. Run dimension loads, then fact loads.
7. Process/deploy the SSAS model and configure the Power BI connection.
8. Refresh and reconcile a sample of figures against SQL queries.

## Security

- Do not commit credentials, passwords, access tokens, or private connection strings.
- Review `.params`, configuration files, package connection managers, and project user files before pushing.
- Replace absolute local paths and machine-specific server names with documented placeholders or configurable parameters.
- Ensure the dataset license permits public redistribution before committing the complete CSV.

## Validation Checklist

- [ ] Database and schemas exist.
- [ ] Source and destination column mappings are correct.
- [ ] No unexpected conversion errors remain.
- [ ] Rejected rows are logged with a reason.
- [ ] Dimension keys are unique.
- [ ] Fact-table foreign keys resolve.
- [ ] Aggregated sales match source-level calculations.
- [ ] SSAS model builds and processes successfully.
- [ ] Power BI refreshes successfully.
- [ ] Screenshots contain no sensitive information.