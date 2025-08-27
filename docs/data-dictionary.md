### Data Dictionary

Facts
- `FactSales`: TransactionDateKey, ProductKey, CustomerKey, GeographyKey, Units, Revenue, Margin
- `FactWebAnalytics`: DateKey, Sessions, Users, Step, Conversions
- `FactSupportTickets`: DateKey, TicketId, Category, SLASeconds, ResolvedFlag
- `FactSurveys`: DateKey, CustomerKey, Score (0–10), Channel
- `FactInventory`: DateKey, ProductKey, OnHandQty, StockoutFlag
- `FactTargets`: DateKey, ProductKey/GeographyKey, TargetRevenue/Units

Dimensions
- `DimDate`: DateKey, Date, Year, Quarter, Month, ISOWeek, FiscalYear, YTDFlag, MTDFlag
- `DimProduct`: ProductKey, SKU, Name, Category, Brand
- `DimCustomer`: CustomerKey, Name, Segment, Status
- `DimGeography`: GeographyKey, Region, Country, State, City
- `RLS_RegionUsers`: UserEmail, Region

Conventions
- Keys are integers; business IDs stored as text where needed
- Amount columns are Decimal Number; counts are Whole Number
- Dates use `Date` data type; time in `DateTime` where applicable
