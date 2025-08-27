### Security & Row-Level Security (RLS)

Approach
- Centralize user-to-region mapping in `RLS_RegionUsers`
- Filter `DimGeography` (and downstream facts) by authorized regions
- Use USERPRINCIPALNAME() for identity mapping

Role Definition (example)
```
-- Role: RegionUser
VAR UserEmail = USERPRINCIPALNAME()
RETURN
CALCULATE(
    TRUE(),
    TREATAS(
        FILTER(RLS_RegionUsers, RLS_RegionUsers[UserEmail] = UserEmail)[Region],
        DimGeography[Region]
    )
)
```

Testing
- Desktop: Model view → Manage roles → View as role
- Service: Assign roles in workspace/app; validate with test accounts

Best Practices
- Deny by default; grant via explicit mapping
- Avoid bi-directional relationships in security paths
- Do not expose security tables to end users
