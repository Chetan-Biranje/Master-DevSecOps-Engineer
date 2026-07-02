# 365-Day Roadmap — Master DevSecOps Engineer

Rule: a week is only checked off when its **deliverable** exists and is linked. Studying without shipping doesn't count.

---

## Phase 1 — AppSec Fundamentals + Python for Security (Days 1–60)

**Goal:** Close the Python gap. Beginner-level Python is not acceptable for a security engineering role — this phase fixes that.

| Weeks | Focus | Deliverable |
|---|---|---|
| 1–2 | Python fundamentals (data structures, OOP, error handling) | 5 solved automation scripts |
| 3–4 | Python for security: `requests`, `socket`, `argparse`, threading | Custom recon script (add to `security-recon-toolkit`) |
| 5–6 | OWASP Top 10 deep dive (hands-on, not just reading) | Write 2 technical blog posts explaining exploitation + fix |
| 7–8 | Burp Suite mastery (Repeater, Intruder, Extensions) | Document 3 manual test cases against a lab target (e.g. PortSwigger Academy) |

**Phase 1 Exit Criteria:** ⬜ 5+ PortSwigger Web Security Academy labs solved and documented, ⬜ Python automation script merged into an existing repo

---

## Phase 2 — Web/API Exploitation + Bug Bounty (Days 61–120)

**Goal:** Convert study into published, verifiable findings — not private notes.

| Weeks | Focus | Deliverable |
|---|---|---|
| 9–10 | API security testing (BOLA, mass assignment, JWT attacks) | 1 API-focused report submitted to a live program |
| 11–12 | Recon at scale (subdomain enum, JS analysis, endpoint discovery) | Automate recon for Flipkart/Myntra scope, log findings |
| 13–14 | Publish backlog | **Publish the Meesho WAF bypass writeup** — this is overdue, do it first |
| 15–16 | HackerOne profile | **Make HackerOne profile public**, populate with resolved reports |
| 17 | Report writing quality pass | Rewrite 3 old reports to professional disclosure standard |

**Phase 2 Exit Criteria:** ⬜ Meesho writeup published, ⬜ HackerOne profile public, ⬜ 3 new valid reports submitted

---

## Phase 3 — DevOps Foundations (Days 121–180)

**Goal:** Docker, CI/CD, and IaC fluency — the "Dev" half of DevSecOps.

| Weeks | Focus | Deliverable |
|---|---|---|
| 18–19 | Docker (multi-stage builds, security scanning with Trivy) | Dockerize an existing tool from your toolchain |
| 20–21 | GitHub Actions CI/CD basics | Working pipeline: build → test → deploy for a sample app |
| 22–23 | Terraform + Ansible fundamentals | IaC module for a small cloud environment |
| 24–25 | Secrets management (Gitleaks, Vault basics) | Add secret scanning to an existing CI pipeline |
| 26 | Review + consolidate | Write architecture diagram for what you built |

**Phase 3 Exit Criteria:** ⬜ One working CI/CD pipeline in production use, ⬜ Terraform module deployed and destroyed cleanly

---

## Phase 4 — DevSecOps Pipeline Integration (Days 181–240)

**Goal:** Ship the flagship project: **Secure Python App Pipeline**.

| Weeks | Focus | Deliverable |
|---|---|---|
| 27–28 | SAST integration (Bandit, SonarQube/SonarCloud) | SAST stage in pipeline with enforced quality gate |
| 29–30 | DAST integration (OWASP ZAP) | ZAP scan stage against a staging deployment |
| 31–32 | SCA + dependency scanning (Trivy, Snyk/Dependabot) | SCA stage blocking builds on critical CVEs |
| 33–34 | Findings triage workflow | Automated report → ticket pipeline (JSON/HTML output) |
| 35 | Documentation | Professional README for Secure Python App Pipeline repo |

**Phase 4 Exit Criteria:** ⬜ Secure Python App Pipeline repo complete with SAST+DAST+SCA gates, ⬜ README published with badges and results

---

## Phase 5 — Cloud Security (Days 241–300)

**Goal:** AWS/Azure security fundamentals applied to real infrastructure.

| Weeks | Focus | Deliverable |
|---|---|---|
| 36–37 | IAM security, least privilege, policy auditing | Audit script for IAM misconfig detection |
| 38–39 | Cloud network security (VPC, security groups, WAF) | Documented secure VPC architecture |
| 40–41 | Container security in the cloud (ECS/EKS or ACI/AKS) | Deploy hardened container workload |
| 42–43 | Cloud posture scanning (Prowler / equivalent) | Full posture report on a test AWS account |
| 44 | Cost + cleanup discipline | Teardown checklist, no orphaned resources |

**Phase 5 Exit Criteria:** ⬜ One cloud security audit report published, ⬜ Hardened deployment documented with before/after

---

## Phase 6 — Capstone: Zero-Trust CI/CD + Portfolio Publish (Days 301–365)

**Goal:** Finish the **Zero-Trust Secure CI/CD Pipeline** project and consolidate the portfolio for Google/Microsoft security engineering applications.

| Weeks | Focus | Deliverable |
|---|---|---|
| 45–47 | Zero-Trust CI/CD architecture design + build | Full pipeline: identity-aware access, signed artifacts, policy-as-code |
| 48–49 | Authentication Break & Bypass Lab — finish and document | Public lab repo with attack scenarios + fixes |
| 50–51 | Resume + LinkedIn refresh with real numbers from this year | Updated Abey George template resume (structure preserved) |
| 52 | Portfolio review | All repos have professional READMEs, all findings published |

**Phase 6 Exit Criteria:** ⬜ Zero-Trust CI/CD Pipeline complete and public, ⬜ Auth Break & Bypass Lab complete and public, ⬜ Resume updated with this year's shipped work

---

## Non-Negotiables Throughout

- No new "roadmap" or "resource collection" repos until this one is at 100%
- Every phase's deliverable must be **public and linkable** — private notes don't count as done
- Weekly entry required in [`progress-log.md`](progress-log.md), even if the entry is "did nothing this week, here's why"
