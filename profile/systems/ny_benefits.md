# System Profile: New York State Benefits

*[PRIVATE — Contains sensitive system and status information. Do not commit populated versions of this file to public repositories.]*

---

## Active Benefits

| Benefit | Agency | Status | Last Verified | Notes |
|---|---|---|---|---|
| SNAP | NYS OTDA / HRA | Active | [date] | [case number in private config] |
| Medicaid | NYS DOH / HRA | Active | [date] | [case number in private config] |
| Cash Assistance | NYS OTDA / HRA | Active | [date] | Increasing this year |
| Housing Assistance | [agency TBD] | Active | [date] | Covers rent; income-based contribution |

---

## Known Threat Landscape

### Federal Level (Current — as of Q1 2026)
- Executive orders targeting SNAP eligibility and work requirements
- Proposed Medicaid block grant or per-capita cap structures (would shift risk to states)
- Federal funding freezes and clawbacks affecting state-administered programs
- DOGE-driven cuts to USDA, HHS creating administrative disruption

### State Level
- NYS has historically pushed back on federal cuts, but is budget-constrained
- State-level communication to clients about changes is notoriously opaque and delayed

### Observed Pattern (Personal / Community)
- Cases "winking out" — losing active status without prior notification to client
- Re-certification windows closing without adequate warning
- System errors treated as client errors
- Health consequences for sudden loss of coverage (documented in affective network)

---

## Monitoring Targets

The agent should watch and alert on changes to:

- [ ] NYC HRA ACCESS HRA portal — case status changes
- [ ] NYS OTDA website — policy and regulatory updates
- [ ] Federal Register — SNAP and Medicaid rule changes (30-day comment periods are the early warning)
- [ ] NY state legislature — budget bills affecting benefits
- [ ] Legal aid and advocacy org feeds (e.g., MFY Legal Services, Empire Justice Center, Mobilization for Justice)
- [ ] News sources covering SNAP/Medicaid cuts with state-specific detail

---

## Alert Thresholds

| Trigger | Alert Level | Response |
|---|---|---|
| Any case status change | Immediate | User notification + document screenshot |
| Re-certification date within 60 days | Warning | Draft re-cert checklist; calendar reminder |
| Federal rule change affecting program | Informational | Summary + likely impact analysis |
| Executive order affecting program | High | Summary + timeline + action options |
| Friend's case affected | High | User notification + relevant process documentation |

---

## Key Contacts & Resources

*(Populated in private config — template below)*

- **HRA ACCESS HRA**: [login credentials in private config]
- **HRA Infoline**: 718-557-1399
- **SNAP Hotline**: 1-800-342-3009
- **Medicaid Helpline**: 1-800-541-2831
- **Legal Aid Society (NYC)**: 212-577-3300
- **Empire Justice Center**: Benefits advocacy and legal help
- **Mobilization for Justice**: NYC benefits legal aid
- **NY Benefits Cliff Calculator**: For modeling income vs. benefit loss
- **Executive Order tracker**: [to be built]

---

## Process Documentation

### Re-certification (SNAP)
- Frequency: typically every 6 or 12 months
- Method: online via ACCESS HRA, phone, or in-person
- Required: income verification, identity, residence
- Consequence of missing: case closes; reapplication required (slower)

### Medicaid (MAGI)
- Annual renewal via NY State of Health or HRA
- Automatic renewal attempted; not always successful
- If income changes significantly, report within 30 days

### Cash Assistance
- Monthly reporting may be required depending on case type
- Work activity requirements may apply (check current case conditions)

### Housing Assistance
- Lease renewal coordination with case worker
- Income changes can affect rent contribution calculation
- Document all communications with housing agency

---

## Incident Log

| Date | What Happened | Source | Impact | Resolution |
|---|---|---|---|---|
| [date] | Affective network member lost case without notice | Case closed in system | Health crisis, significant anxiety | Case reopened; full benefits restored |

*(Continue logging all notable incidents)*

---

## Notes on System Opacity

These systems are built on the assumption that clients are in crisis and therefore won't be paying close enough attention to catch errors or policy changes before they cause harm. This is a design choice, not an accident.

The monitoring layer of the ODS exists specifically to close this information gap — to know about changes at the same time as or before the caseworkers who implement them.
