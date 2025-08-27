### Deployment & Operations

Environments
- Dev (Desktop), Test, Prod (Power BI Service)
- Parameterize data sources; use shared datasets where appropriate

Publishing
- Validate model, run full refresh locally
- Publish `project.pbix` to the workspace
- Configure dataset credentials and gateways (if on-prem sources)

Refresh
- Schedule refresh aligned with SLAs
- Incremental refresh for large tables (see performance doc)
- Monitor failures; set alerting

App
- Create an app with audience segments
- Document RLS and expected visibility for each audience

Versioning
- Maintain release notes; export template PBIX if needed
