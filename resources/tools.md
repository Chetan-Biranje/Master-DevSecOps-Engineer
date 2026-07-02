# Toolchain Reference

Single source of truth for all tools used across the roadmap. Add new tools here as they're adopted — don't scatter tool mentions across repos.

---

## 🔍 Recon & OSINT

| Tool | Purpose | Install | Phase |
|---|---|---|---|
| Amass | Subdomain enumeration | `go install github.com/owasp-amass/amass/v4/...@master` | 2 |
| Subfinder | Passive subdomain discovery | `go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest` | 2 |
| httpx | HTTP probing & tech detection | `go install github.com/projectdiscovery/httpx/cmd/httpx@latest` | 2 |
| nuclei | Template-based vulnerability scanner | `go install github.com/projectdiscovery/nuclei/v3/cmd/nuclei@latest` | 2 |
| ffuf | Web fuzzer (dirs, endpoints, params) | `go install github.com/ffuf/ffuf/v2@latest` | 1–2 |
| waybackurls | Historical URL discovery | `go install github.com/tomnomnom/waybackurls@latest` | 2 |
| gau | Get All URLs (Common Crawl + Wayback) | `go install github.com/lc/gau/v2/cmd/gau@latest` | 2 |
| shodan CLI | Internet-wide host discovery | `pip install shodan` | 2 |

---

## 🌐 Web AppSec

| Tool | Purpose | Install | Phase |
|---|---|---|---|
| Burp Suite Community | HTTP proxy, scanner, intruder | Download from PortSwigger | 1–2 |
| OWASP ZAP | DAST — active & passive scanning | Docker: `ghcr.io/zaproxy/zaproxy` | 4 |
| SQLMap | Automated SQL injection | `pip install sqlmap` | 1–2 |
| XSStrike | XSS detection & exploitation | `pip install xsstrike` | 1–2 |
| Nikto | Web server scanner | `apt install nikto` | 1–2 |
| Wapiti | Web vulnerability scanner | `pip install wapiti3` | 2 |

---

## 📱 Mobile Security

| Tool | Purpose | Install | Phase |
|---|---|---|---|
| JADX | APK decompiler (Java/Kotlin) | https://github.com/skylot/jadx | 2 |
| MobSF | Automated mobile app security framework | Docker: `opensecurity/mobile-security-framework-mobsf` | 2 |
| Frida | Dynamic instrumentation / hooking | `pip install frida-tools` | 2 |
| apktool | APK decompile/recompile | `apt install apktool` | 2 |
| objection | Runtime mobile exploration (Frida-based) | `pip install objection` | 2 |

---

## 🐍 Python Security Tooling

| Tool | Purpose | Install | Phase |
|---|---|---|---|
| requests | HTTP library (foundation of most tools) | `pip install requests` | 1 |
| aiohttp | Async HTTP (for concurrent recon) | `pip install aiohttp` | 1 |
| scapy | Packet crafting & network analysis | `pip install scapy` | 1 |
| pwntools | CTF & exploit development framework | `pip install pwntools` | 1 |
| impacket | Windows network protocols | `pip install impacket` | 2 |
| paramiko | SSH library for automation | `pip install paramiko` | 3 |

---

## 🐳 Containers & Orchestration

| Tool | Purpose | Install | Phase |
|---|---|---|---|
| Docker | Container runtime | https://docs.docker.com/get-docker/ | 3 |
| Docker Compose | Multi-container apps | Bundled with Docker Desktop | 3 |
| Kubernetes (kubectl) | Container orchestration | https://kubernetes.io/docs/tasks/tools/ | 5 |
| Helm | Kubernetes package manager | https://helm.sh/docs/intro/install/ | 5 |
| k9s | Terminal Kubernetes UI | https://k9scli.io | 5 |
| Trivy | Container/IaC/dependency vulnerability scanner | `brew install aquasecurity/trivy/trivy` | 3–4 |
| Grype | Container image vulnerability scanner | https://github.com/anchore/grype | 3–4 |
| Dive | Analyze Docker image layers | https://github.com/wagoodman/dive | 3 |

---

## 🔁 CI/CD & IaC

| Tool | Purpose | Use | Phase |
|---|---|---|---|
| GitHub Actions | CI/CD pipelines | YAML workflows in `.github/workflows/` | 3–4 |
| Terraform | Infrastructure as Code | `terraform init && terraform apply` | 3 |
| Ansible | Configuration management | `pip install ansible` | 3 |
| HashiCorp Vault | Secrets management | Docker: `hashicorp/vault` | 3–4 |
| pre-commit | Git hooks for quality gates | `pip install pre-commit` | 3 |

---

## 🔐 Security Scanning (SAST / SCA / Secrets)

| Tool | Type | Purpose | Phase |
|---|---|---|---|
| Bandit | SAST | Python static analysis | 4 |
| Semgrep | SAST | Multi-language static analysis | 4 |
| SonarCloud | SAST | Cloud-based code quality + security | 4 |
| Gitleaks | Secrets | Git history secret scanning | 3–4 |
| TruffleHog | Secrets | Deep secrets scan (entropy + regex) | 3–4 |
| Safety | SCA | Python dependency vulnerability check | 4 |
| Dependabot | SCA | GitHub native dependency alerts | 4 |
| Snyk | SCA | Multi-language dependency + container scan | 4 |
| OWASP Dependency-Check | SCA | Java/Node/Python CVE matching | 4 |

---

## ☁️ Cloud Security

| Tool | Purpose | Install | Phase |
|---|---|---|---|
| AWS CLI | AWS resource management | `pip install awscli` | 5 |
| Prowler | AWS/Azure/GCP security posture scanner | `pip install prowler` | 5 |
| ScoutSuite | Multi-cloud security audit | `pip install scoutsuite` | 5 |
| CloudMapper | AWS environment visualization | https://github.com/duo-labs/cloudmapper | 5 |
| Pacu | AWS exploitation framework | https://github.com/RhinoSecurityLabs/pacu | 5 |

---

## 🛡️ Zero Trust & Identity

| Tool | Purpose | Phase |
|---|---|---|
| OPA (Open Policy Agent) | Policy-as-code engine | 6 |
| Keycloak | Open-source identity provider | 6 |
| Cosign | Container image signing (Sigstore) | 6 |
| in-toto | Software supply chain framework | 6 |

---

## 🧰 General Dev Environment

| Tool | Purpose |
|---|---|
| Kali Linux | Security-focused OS (primary attack lab) |
| VSCode + extensions | Primary IDE (Python, YAML, Docker, Terraform) |
| Git | Version control |
| tmux | Terminal multiplexer for long-running sessions |
| jq | JSON processing in shell |
| curl / httpie | HTTP testing from CLI |

---

**Last updated:** 2026-07-02
