# Global Digital Health BI Dashboard

Executive-ready Power BI solution providing an end-to-end view across Sales, Web Funnel, CX/Support, Inventory, Targets vs Actuals, and Executive KPIs. Built with robust data prep, a clean star schema, governed DAX measures, RLS, and performance best practices.

## Highlights
- Executive summary with KPIs and drillthroughs
- Deep dives: Sales, Web Analytics Funnel, CX/Support, Inventory, Targets vs Actuals
- Governed semantic layer: reusable DAX measures and field parameters
- Robust data prep in Power Query with standards-based foldering
- Star schema with conformed dimensions and RLS for region-level security
- Performance: aggregations, optimization, and incremental refresh readiness

## Repo Contents
- `project.pbix`: Main Power BI report
- `Dashboard.xlsx`: Sample/reference data workbook
- `LICENSE`: License
- `docs/` (to be added): Detailed documentation for modeling, measures, performance, and ops

## Quickstart
1) Open `project.pbix` in Power BI Desktop (May 2023 or later recommended).
2) Update data source paths if prompted. Use `Dashboard.xlsx` as sample input if needed.
3) Refresh preview in Power Query, then apply changes and refresh the model.
4) Explore report pages. Use slicers and drillthrough to navigate analyses.

## Data Model Overview
Star schema centered on transactional fact tables with shared conformed dimensions:
- Facts: `FactSales`, `FactWebAnalytics`, `FactSupportTickets`, `FactSurveys`, `FactInventory`, `FactTargets`
- Dimensions: `DimDate`, `DimProduct`, `DimCustomer`, `DimGeography`, plus security table `RLS_RegionUsers`

Relationships are primarily many-to-one from facts to dimensions. Handle M2M using bridge or composite models where required.

## DAX Measure Domains
- Sales performance and targets, variances, YoY/period-over-period
- Web funnel conversion and drop-off
- CX KPIs: NPS/CSAT, ticket volume, SLA, backlog
- Inventory availability and coverage
- Executive rollups and What-If parameters

## Security
Row-Level Security (RLS) enforced using `RLS_RegionUsers` to filter by geography/region. Test with "View as" in Desktop and workspace roles in Service.

## Documentation
Detailed docs are in `docs/`:
- Data Prep (`docs/data-prep.md`)
- Data Modeling (`docs/data-modeling.md`)
- Measures (`docs/measures.md`)
- Report UX (`docs/report.md`)
- Security & RLS (`docs/security-rls.md`)
- Performance (`docs/performance.md`)
- Deployment (`docs/deployment.md`)
- Accessibility (`docs/accessibility.md`)
- Data Dictionary (`docs/data-dictionary.md`)

## Contact
BOGHRAT, Senior BI Specialist — Join@boqrat.com
Estimated delivery: 5–7 days
