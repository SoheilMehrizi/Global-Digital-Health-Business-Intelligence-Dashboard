### Performance & Refresh

Model Optimization
- Prefer star schema; avoid snowflaking where possible
- Hide unused columns; reduce cardinality on high-card columns
- Use whole numbers for keys; avoid text relationships
- Avoid bi-directional relationships unless required

DAX Optimization
- Avoid row-by-row iterators over large tables in visuals
- Use variables, `SUMX` only when necessary; leverage pre-aggregations
- Use `KEEPFILTERS`, `REMOVEFILTERS` judiciously

Aggregations & Partitions
- Consider aggregation tables for large facts (Import + DirectQuery composite)
- Partition large tables aligned to refresh windows

Incremental Refresh
- Configure RangeStart/RangeEnd parameters
- Policy example: store 5 years; refresh last 30 days
- Ensure query folding for incremental policy tables

Diagnostics
- Performance Analyzer pane
- DAX Studio: server timings, query plan, VertiPaq Analyzer
