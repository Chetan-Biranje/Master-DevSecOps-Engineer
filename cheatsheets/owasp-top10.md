# OWASP Top 10 Cheatsheet (2021)

Quick reference for exploitation + fix for each vulnerability. Every item links to a PortSwigger lab to do hands-on.

---

## A01 — Broken Access Control

**What it is:** Users can act outside their intended permissions (IDOR, privilege escalation, path traversal).

**Attack vectors:**
- IDOR: `GET /api/user/1234` → change to `/api/user/1235`
- Path traversal: `../../../../etc/passwd`
- Force browsing to `/admin` without authentication

**Detection:** Test every object reference — replace your ID with another user's ID. Try accessing endpoints without auth tokens.

**Fix:**
- Enforce server-side authorization on every request
- Use indirect object references (random UUIDs, not sequential IDs)
- Deny by default — only whitelist what's allowed

**Lab:** https://portswigger.net/web-security/access-control

---

## A02 — Cryptographic Failures

**What it is:** Sensitive data exposed due to weak/missing encryption.

**Attack vectors:**
- HTTP instead of HTTPS → network sniffing
- MD5/SHA1 password hashing → crackable with rainbow tables
- Hardcoded secrets in source code
- Weak JWT secret → brute-forceable

**Detection:** Check response headers for `Strict-Transport-Security`. Test if HTTP redirects to HTTPS. Look for JWTs — decode with jwt.io.

**Fix:**
- Always HTTPS (HSTS)
- Argon2id / bcrypt for passwords (never MD5/SHA1)
- Use secrets manager — never hardcode
- Strong JWT secrets (256-bit minimum)

**Lab:** https://portswigger.net/web-security/jwt

---

## A03 — Injection

**What it is:** Untrusted data sent to an interpreter as part of a command/query.

### SQL Injection
```
' OR '1'='1
' UNION SELECT username, password FROM users--
```

**Detection:** `sqlmap -u "https://target.com/item?id=1" --dbs`

**Fix:** Parameterized queries / prepared statements. ORM. Input validation.

### Command Injection
```
; ls -la
| cat /etc/passwd
```

**Detection:** Try semicolons, pipes, backticks in any input that might be passed to shell.

**Fix:** Avoid shell calls. Use library functions instead of `os.system()`. Whitelist input.

### SSTI (Server-Side Template Injection)
```
{{7*7}}  → renders 49? Vulnerable.
```

**Lab:** https://portswigger.net/web-security/sql-injection

---

## A04 — Insecure Design

**What it is:** Fundamental design flaws — not implementation bugs.

**Examples:**
- Password reset via secret questions (guessable)
- "Remember me" tokens that never expire
- No rate limiting on authentication endpoints

**Fix:** Threat model during design. Use secure design patterns. Defense in depth.

---

## A05 — Security Misconfiguration

**What it is:** Insecure default configs, unnecessary features enabled, missing hardening.

**Attack vectors:**
- Default credentials (`admin:admin`, `admin:password`)
- Directory listing enabled
- Debug mode in production
- Verbose error messages revealing stack traces

**Detection:**
```bash
nikto -h https://target.com
curl -I https://target.com  # check headers
```

**Fix:** Minimal attack surface. Disable unused features. Security headers. Automated config review.

**Key security headers:**
```
Strict-Transport-Security: max-age=31536000; includeSubDomains
Content-Security-Policy: default-src 'self'
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
```

---

## A06 — Vulnerable and Outdated Components

**What it is:** Using components with known CVEs.

**Detection:**
```bash
trivy image myapp:latest         # container scan
safety check -r requirements.txt # Python deps
npm audit                        # Node deps
```

**Fix:** Dependabot / Renovate for automated updates. Pin versions. SCA in CI pipeline.

---

## A07 — Identification and Authentication Failures

**What it is:** Broken auth — weak passwords, session management flaws.

**Attack vectors:**
- Credential stuffing (breached lists + same passwords)
- Brute force (no rate limiting)
- Session token in URL
- Session not invalidated on logout

**Detection:**
```
hydra -l admin -P /usr/share/wordlists/rockyou.txt target.com http-post-form "..."
```

**Fix:**
- MFA everywhere
- Rate limit login (5 attempts → lockout)
- Secure session cookies (`HttpOnly`, `Secure`, `SameSite=Strict`)
- Invalidate tokens on logout

**Lab:** https://portswigger.net/web-security/authentication

---

## A08 — Software and Data Integrity Failures

**What it is:** Code and infrastructure not protected against integrity violations (supply chain attacks).

**Attack vectors:**
- Unsigned software updates
- Malicious CI/CD plugins
- Dependency confusion attacks

**Fix:**
- Sign artifacts (Cosign/Sigstore)
- Verify checksums
- Restrict CI/CD pipeline permissions (OIDC, not long-lived tokens)
- Lock dependency versions + hash verification

---

## A09 — Security Logging and Monitoring Failures

**What it is:** Insufficient logging to detect and respond to breaches.

**What to log:**
- Authentication events (success and failure)
- Authorization failures
- Input validation failures
- All admin actions

**What NOT to log:**
- Passwords (even failed attempts)
- PII in logs
- Full credit card numbers

**Fix:** Centralized logging (ELK/Splunk). Alerts on anomalies. Log retention policy.

---

## A10 — Server-Side Request Forgery (SSRF)

**What it is:** Attacker tricks server into making requests to internal resources.

**Attack vectors:**
```
https://target.com/fetch?url=http://169.254.169.254/latest/meta-data/
https://target.com/fetch?url=http://internal-db:5432
```

**Detection:** Look for any URL parameter, webhook URL, image import, PDF generators.

**Fix:**
- Allowlist outbound domains
- Block metadata IPs at network level
- Disable redirects on server-side HTTP clients

**Lab:** https://portswigger.net/web-security/ssrf

---

*Last updated: 2026-07-02*
