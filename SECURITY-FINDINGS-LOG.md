# Security Findings Log

> Maintained automatically by the **BMAD Security Advisor** agent.
> Do NOT edit manually — changes will be overwritten on the next agent run.
> Last updated: _Never (no runs yet)_

---

## Summary Dashboard

| Metric | Count |
|--------|-------|
| Total Runs | 0 |
| Open (Critical) | 0 |
| Open (High) | 0 |
| Open (Medium) | 0 |
| Open (Low) | 0 |
| Fixed (All Time) | 0 |
| Regressions (All Time) | 0 |

---

## How This Log Works

The BMAD Security Advisor agent runs on every Pull Request and:

1. **Reads** this file to load all prior findings into memory.
2. **Scans** only the files changed in the current PR (incremental analysis).
3. **Classifies** each finding as `NEW`, `PERSISTED`, `REGRESSED`, or `FIXED`.
4. **Appends** new rows and updates existing status entries.
5. **Posts** a delta-only PR comment showing only what changed.

### Finding Status Definitions

| Status | Meaning |
|--------|---------|
| `NEW` | First detected in this run |
| `PERSISTED` | Was open in a prior run and still open |
| `REGRESSED` | Was marked FIXED but reappeared |
| `FIXED` | Was open in a prior run, no longer detected |

### Severity Levels (BMAD / CVSS-aligned)

| Severity | CVSS Range | Action Required |
|----------|------------|----------------|
| CRITICAL | 9.0 – 10.0 | Block merge immediately |
| HIGH | 7.0 – 8.9 | Block merge |
| MEDIUM | 4.0 – 6.9 | PR comment, fix before release |
| LOW | 0.1 – 3.9 | PR comment, fix in backlog |

---

## Findings Log

> _No findings recorded yet. The BMAD Security Advisor will populate this table on the first PR scan._

| Run ID | PR # | Date (UTC) | File | Line | Rule | Severity | Status | Description |
|--------|------|------------|------|------|------|----------|--------|-------------|
| — | — | — | — | — | — | — | — | Awaiting first scan |

---

## Run History

| Run ID | PR # | Date | New | Regressed | Fixed | Persisted | Net Open |
|--------|------|------|-----|-----------|-------|-----------|----------|
| — | — | — | 0 | 0 | 0 | 0 | 0 |

---

## OWASP Coverage Tracker

> Tracks which OWASP Top 10 (2021) categories have been triggered historically.

| OWASP Category | Total Found | Currently Open | Ever Fixed |
|----------------|-------------|----------------|------------|
| A01 Broken Access Control | 0 | 0 | 0 |
| A02 Cryptographic Failures | 0 | 0 | 0 |
| A03 Injection | 0 | 0 | 0 |
| A04 Insecure Design | 0 | 0 | 0 |
| A05 Security Misconfiguration | 0 | 0 | 0 |
| A06 Vulnerable Components | 0 | 0 | 0 |
| A07 Auth & Session Failures | 0 | 0 | 0 |
| A08 Software Integrity Failures | 0 | 0 | 0 |
| A09 Logging & Monitoring Failures | 0 | 0 | 0 |
| A10 SSRF | 0 | 0 | 0 |
| Secrets & Credential Leakage | 0 | 0 | 0 |
| IaC Misconfiguration | 0 | 0 | 0 |
| Container Hardening | 0 | 0 | 0 |
