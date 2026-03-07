# Requirements Traceability Matrix (RTM)

> Maintained automatically by the **BMAD QA Auditor** agent.
> Do NOT edit manually — agent will overwrite on next run.
> Last updated: _Never (no runs yet)_

---

## Coverage Dashboard

| Metric | Count |
|--------|-------|
| Total Requirements | 0 |
| Fully Covered (all tests pass) | 0 |
| Partially Covered (tests exist, gaps remain) | 0 |
| Not Covered (no test cases) | 0 |
| Deprecated Requirements | 0 |
| Coverage % | 0% |
| Coverage Threshold | 80% |
| Threshold Status | ⚠️ NOT MET (no requirements yet) |

---

## How This Matrix Works

The BMAD QA Auditor agent runs on every Pull Request and:

1. **Reads** `docs/requirements.md` and GitHub Issues labelled `requirement`.
2. **Compares** against this matrix to find new, modified, or uncovered requirements.
3. **Audits** traceability checks (TC-01 through TC-06) for each requirement.
4. **Generates** new test cases for any gaps and writes them into `tests/`.
5. **Updates** this matrix with new test case IDs, file paths, and status.
6. **Posts** a coverage delta report as a PR comment.

### Requirement Status Values

| Status | Meaning |
|--------|---------|
| `COVERED` | All traceability checks pass; test cases exist and mapped |
| `PARTIAL` | Some test cases exist but not all checks pass |
| `NOT_COVERED` | No test cases mapped to this requirement |
| `DEPRECATED` | Requirement was removed from source |

### Traceability Checks (TC-01 to TC-06)

| Check | Requirement |
|-------|-------------|
| TC-01 | At least one test case mapped to REQ-ID |
| TC-02 | All mapped test files exist in repository |
| TC-03 | All tests reference REQ-ID via annotation |
| TC-04 | Unit + Integration tests for MUST-priority reqs |
| TC-05 | Dedicated test types for Non-Functional reqs |
| TC-06 | Regulation clause verified for Compliance reqs |

---

## Traceability Table

> _No requirements registered yet. Add requirements to `docs/requirements.md`_
> _or create GitHub Issues labelled `requirement` to populate this matrix._

| REQ-ID | Title | Priority | Category | TC-01 | TC-02 | TC-03 | TC-04 | TC-05 | TC-06 | Test Case IDs | Test File(s) | Status | Last PR |
|--------|-------|----------|----------|-------|-------|-------|-------|-------|-------|---------------|-------------|--------|---------|
| — | Awaiting first scan | — | — | — | — | — | — | — | — | — | — | — | — |

---

## Test Case Registry

> _All generated test cases are registered here for cross-reference._

| TC-ID | REQ-ID | Type | Description | File | Auto-Generated | Status |
|-------|--------|------|-------------|------|----------------|--------|
| — | — | — | Awaiting first scan | — | — | — |

---

## Change Log

| Run Date | PR # | Reqs Added | Reqs Updated | TCs Added | TCs Updated | Coverage Before | Coverage After |
|----------|------|------------|--------------|-----------|-------------|-----------------|----------------|
| — | — | 0 | 0 | 0 | 0 | 0% | 0% |

---

## Uncovered Requirements Queue

> _Requirements that still need test cases assigned. Agent will process on next PR._

| REQ-ID | Title | Priority | Days Uncovered | Assigned To |
|--------|-------|----------|----------------|-------------|
| — | — | — | 0 | — |
