### DAX Measures

Measure Domains
- Sales: Revenue, Units, Margin, Target, Variance, % to Target, YoY
- Web Funnel: Sessions, Users, Conversions, CVR, Drop-off by step
- CX/Support: Tickets, SLA Met %, Backlog, Resolution Time
- Surveys: NPS, CSAT, Response Rate
- Inventory: On-Hand, Coverage Days, Stockout Rate
- Executive: Composite KPIs, What-If parameters

Patterns
- Time intelligence with `DimDate` (YTD, MTD, YoY)
- Selector-insensitive KPIs using `REMOVEFILTERS`/`ALLSELECTED`
- Safe divisions: `DIVIDE(numerator, denominator)`
- Targets vs Actuals with `TREATAS`/mapping tables when needed

Example Snippets
```
Revenue := SUM(FactSales[Revenue])

Revenue YoY := 
VAR CurrentPeriod = [Revenue]
VAR PriorPeriod = CALCULATE([Revenue], DATEADD(DimDate[Date], -1, YEAR))
RETURN DIVIDE(CurrentPeriod - PriorPeriod, PriorPeriod)

NPS := 
VAR Promoters = CALCULATE(COUNTROWS(FactSurveys), FactSurveys[Score] >= 9)
VAR Detractors = CALCULATE(COUNTROWS(FactSurveys), FactSurveys[Score] <= 6)
VAR Total = COUNTROWS(FactSurveys)
RETURN DIVIDE(Promoters - Detractors, Total)
```

Governance
- Use calculation groups for time intelligence where available
- Organize measures in display folders; prefix with domain (e.g., `Sales | ...`)
