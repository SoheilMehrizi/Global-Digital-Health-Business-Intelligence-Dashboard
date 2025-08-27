### Data Modeling (Star Schema)

Design
- Star schema with conformed dimensions: Date, Product, Customer, Geography
- Facts: Sales, WebAnalytics, SupportTickets, Surveys, Inventory, Targets
- Relationships: many-to-one from facts to dimensions; single direction by default
- Handle M2M via bridge tables or composite models when required

Keys
- Dimensions have surrogate integer keys
- Facts store corresponding foreign keys
- Date uses an integer date key (YYYYMMDD) for performance

Notable Tables
- `DimDate`: calendar + fiscal attributes (Year, Quarter, Month, ISOWeek, YTD/MTD flags)
- `DimProduct`: product hierarchy, category, brand
- `DimCustomer`: segment, lifecycle status
- `DimGeography`: Region, Country, State/Province, City
- `RLS_RegionUsers`: maps UserPrincipalName to authorized Region(s)

Relationships
- One-to-many: `Dim*` → `Fact*`
- Bridge examples: `Product ↔ Inventory` where granularity differs

Modeling Standards
- Hide foreign keys and technical columns
- Expose only curated columns and measures
- Use display folders for measures and field parameters
