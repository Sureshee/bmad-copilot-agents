# BMAD Copilot Agents

> **Build More Architect Dreams (BMAD) Framework** automated agents for GitHub Copilot:
> - **Security Advisor**: Incremental security analysis with persistent findings log
> - **QA Auditor**: Requirements traceability matrix with automated test generation

[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/Sureshee/bmad-copilot-agents/copilot-bmad-orchestrator.yml?branch=main)](https://github.com/Sureshee/bmad-copilot-agents/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## Overview

This repository implements two specialized GitHub Copilot custom agents using the **BMAD (Build More Architect Dreams)** framework to automate security reviews and QA traceability in your development workflow.

### Key Innovations

1. **Incremental Security Analysis**: Unlike traditional scans that re-report everything, the Security Advisor maintains a persistent `SECURITY-FINDINGS-LOG.md` that tracks findings across PRs, classifying each as NEW, PERSISTED, REGRESSED, or FIXED.

2. **Automated Requirements Traceability**: The QA Auditor reads `docs/requirements.md`, audits the `QA-MATRIX.md` for gaps, auto-generates missing test cases, and updates the matrix — ensuring every requirement has mapped tests.

3. **BMAD First Principles**: Both agents apply BMAD methodology:
   - **Adversarial Review** (Security): Simulate attacker mindset
   - **Context-Engineered Development** (QA): Embed requirement context in every test
   - **Definition-of-Done Enforcement**: Block PRs that violate quality gates

---

## Repository Structure

```
bmad-copilot-agents/
├── .github/
│   ├── agents/
│   │   ├── security-advisor.agent.md     # Security Advisor agent definition
│   │   └── qa-auditor.agent.md           # QA Auditor agent definition
│   └── workflows/
│       └── copilot-bmad-orchestrator.yml # Workflow orchestrating both agents
├── docs/
│   └── requirements.md                   # Software requirements specification
├── SECURITY-FINDINGS-LOG.md              # Persistent security findings log
├── QA-MATRIX.md                          # Requirements traceability matrix
└── README.md                             # This file
```

---

## Agent Capabilities

### 🛡️ Security Advisor

**Mission**: Enforce security quality gates on every PR through incremental, log-driven analysis.

#### Features
- **OWASP Top 10 (2021) detection**: A01-A10 plus secrets, CVEs, IaC misconfigurations
- **Incremental scanning**: Only analyzes changed files in PR diffs
- **Delta reporting**: PR comments show only NEW/REGRESSED/FIXED findings
- **Severity-based blocking**: Blocks merge for CRITICAL/HIGH findings
- **OWASP Coverage Tracker**: Histogram of which categories have been triggered
- **Architectural recommendations**: Suggests systemic fixes for recurring issues

#### How It Works

1. **INITIALISE**: Reads `SECURITY-FINDINGS-LOG.md` into memory
2. **SCOPE**: Identifies changed files in PR (git diff)
3. **ANALYSE**: Scans for vulnerabilities (OWASP, secrets, CVEs)
4. **DELTA**: Compares against prior log; classifies as NEW/PERSISTED/REGRESSED/FIXED
5. **UPDATE**: Appends new findings to log with Run ID and PR number
6. **REPORT**: Posts PR comment with delta summary only

**Example PR Comment**:
```markdown
## BMAD Security Advisor — Run 2026-03-10-R42 | PR #123

### Delta Summary
| Status    | Critical | High | Medium | Low |
|-----------|----------|------|--------|-----|
| NEW       | 0        | 1    | 2      | 0   |
| REGRESSED | 1        | 0    | 0      | 0   |
| FIXED     | 0        | 2    | 1      | 3   |

### New & Regressed Findings
**[HIGH] A03-Injection — SQL Injection in user query**
- File: `api/users.js:42`
- Status: NEW
- Description: Unsanitized user input concatenated into SQL query
- Impact: Attacker can exfiltrate database contents
- Remediation: Use parameterized queries or ORM
...
```

---

### ✅ QA Auditor

**Mission**: Ensure 100% requirements coverage through automated traceability and test generation.

#### Features
- **Multi-source requirement reading**: `docs/requirements.md` + GitHub Issues labelled `requirement`
- **TC-01 to TC-06 traceability checks**: Validates test mapping, file existence, annotations, test types
- **Auto-generated test cases**: Creates Unit/Integration/E2E tests for uncovered requirements
- **MoSCoW priority enforcement**: Blocks merge if MUST-priority requirements uncovered
- **Framework-agnostic**: Auto-detects Jest, Pytest, JUnit, etc.
- **Test case annotations**: Every generated test references its REQ-ID

#### How It Works

1. **INITIALISE**: Loads `docs/requirements.md` and `QA-MATRIX.md`
2. **SCOPE**: Identifies NEW/MODIFIED/UNCOVERED requirements
3. **AUDIT**: Runs TC-01 to TC-06 checks on each requirement
4. **GENERATE**: Writes test files for gaps (AAA pattern: Arrange/Act/Assert)
5. **UPDATE**: Updates matrix with new test case IDs and file paths
6. **REPORT**: Posts coverage delta to PR

**Example PR Comment**:
```markdown
## BMAD QA Auditor — Traceability Report | PR #123

### Coverage Dashboard
| Metric          | Before PR | After PR | Delta |
|-----------------|-----------|----------|-------|
| Total Reqs      | 7         | 7        | 0     |
| Covered         | 3         | 5        | +2    |
| Not Covered     | 4         | 2        | -2    |
| Coverage %      | 43%       | 71%      | +28%  |

### Test Cases Generated This PR
| TC-ID       | REQ-ID  | Type        | File                          | Status |
|-------------|---------|-------------|-------------------------------|--------|
| TC-REQ-001-01 | REQ-001 | Unit        | tests/unit/security-advisor.test.js | Added  |
| TC-REQ-002-01 | REQ-002 | Integration | tests/int/qa-auditor.test.js  | Added  |
...
```

---

## Setup & Usage

### Prerequisites
- GitHub repository with Actions enabled
- GitHub Copilot subscription (for future agent runtime integration)
- Write access to repository

### Installation

1. **Copy agent files to your repo**:
```bash
mkdir -p .github/agents .github/workflows docs
curl -o .github/agents/security-advisor.agent.md https://raw.githubusercontent.com/Sureshee/bmad-copilot-agents/main/.github/agents/security-advisor.agent.md
curl -o .github/agents/qa-auditor.agent.md https://raw.githubusercontent.com/Sureshee/bmad-copilot-agents/main/.github/agents/qa-auditor.agent.md
curl -o .github/workflows/copilot-bmad-orchestrator.yml https://raw.githubusercontent.com/Sureshee/bmad-copilot-agents/main/.github/workflows/copilot-bmad-orchestrator.yml
```

2. **Initialize log files**:
```bash
curl -o SECURITY-FINDINGS-LOG.md https://raw.githubusercontent.com/Sureshee/bmad-copilot-agents/main/SECURITY-FINDINGS-LOG.md
curl -o QA-MATRIX.md https://raw.githubusercontent.com/Sureshee/bmad-copilot-agents/main/QA-MATRIX.md
```

3. **Add your requirements** to `docs/requirements.md` (see example in this repo)

4. **Commit and push** — the workflow will trigger on the next PR

### Manual Trigger

Run agents manually via GitHub Actions:
1. Go to **Actions** tab
2. Select **BMAD Copilot Agents Orchestrator**
3. Click **Run workflow**
4. Choose agent: `security`, `qa`, or `both`

---

## Configuration

### QA Coverage Threshold
Edit `docs/qa-config.yml` (create if needed):
```yaml
coverage_threshold: 80  # Default 80%
```

### Security Severity Levels
Defined in `SECURITY-FINDINGS-LOG.md`:
- **CRITICAL** (9.0–10.0): Block merge immediately
- **HIGH** (7.0–8.9): Block merge
- **MEDIUM** (4.0–6.9): Comment only
- **LOW** (0.1–3.9): Comment only

---

## Integration Roadmap

**Current State (v1.0)**: Agents are fully defined but run as placeholder simulations in the workflow.

**Future Integration** (when GitHub Copilot CLI supports custom agents):
```yaml
# Replace placeholder steps with:
- name: Run Security Advisor
  run: |
    gh copilot agent run \
      --agent .github/agents/security-advisor.agent.md \
      --context SECURITY-FINDINGS-LOG.md \
      --context changed_files.txt
```

---

## Contributing

Contributions welcome! Focus areas:
- Additional OWASP checks (e.g., A11: SSRF expansions)
- Integration with Polarion/Jira for requirements sync
- Custom test framework templates (Mocha, RSpec, etc.)
- Performance optimizations for large repos

---

## License

MIT License — see LICENSE file

---

## Acknowledgments

- **BMAD Framework**: [Build More Architect Dreams methodology](https://github.com/bmad-framework)
- **OWASP Top 10**: [2021 Web Application Security Risks](https://owasp.org/Top10/)
- **GitHub Copilot**: [Custom agents documentation](https://docs.github.com/en/copilot)

---

**Maintained by**: Sureshee  
**Repository**: [github.com/Sureshee/bmad-copilot-agents](https://github.com/Sureshee/bmad-copilot-agents)  
**Version**: 1.0.0
