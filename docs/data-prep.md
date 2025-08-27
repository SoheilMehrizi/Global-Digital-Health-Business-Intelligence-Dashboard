### Data Prep (Power Query)

This section documents data extraction, cleaning, conformance, and loading in Power Query.

Key principles:
- Consistent foldering: Staging, Standardized, Dimensions, Facts
- Documented transformations with meaningful step names
- Deterministic data types and locale settings
- Handle nulls and outliers; enforce date/calendar conformance

Sources
- Excel/CSV: `Dashboard.xlsx` (sample/reference)
- Other sources: configure in `project.pbix` as applicable

Common Transformations
- Rename columns to semantic names (PascalCase for columns)
- Data types: explicit Date, DateTime, Decimal Number, Whole Number, Text
- Trim/clean text; standardize casing
- Null handling: replace or filter; impute only with business approval
- Keys: generate surrogate keys where needed
- Calendar: derive `DimDate` with fiscal flags, ISO week, YTD/MTD markers

Standards
- Step naming: `Source → PromoteHeaders → ChangedType → FilteredRows → MergedQueries`
- Table naming: `stg_*`, `dim_*`, `fact_*`
- Folders (in PBIX Queries pane): Staging, Standardized, Dimensions, Facts, Helpers

Quality & Governance
- Use `Column quality` and `Column distribution`
- Add sample tests: distinct counts, not-null checks, key uniqueness
- Parameterize source paths for environments

Refresh
- Enable query folding wherever possible
- Partitioning strategy aligned with Incremental Refresh (see performance doc)
