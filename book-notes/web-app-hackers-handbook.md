# Book Notes — The Web Application Hacker's Handbook

**Authors:** Dafydd Stuttard & Marcus Pinto
**Edition:** 2nd Edition
**Started:** 2026-07-02
**Status:** 🔄 Reading

---

## How to Use These Notes

- Chapter summaries go below as they're read
- Techniques get tested against a lab (PortSwigger, DVWA, or Juice Shop) — link the test
- Any technique applied in a real engagement or writeup gets noted here

---

## Chapter 1 — Web Application (In)security

**Key ideas:**
- Web apps are uniquely exposed because they're designed to be publicly accessible
- The attack surface grows with every feature added
- Most vulns come from insufficient input validation and broken access controls

**Notes:**
- The "core security problem" = users supply arbitrary input that the application processes
- Three categories of security mechanism: authentication, session management, access control

**Applied:** _Not yet — add link when tested_

---

## Chapter 2 — Core Defense Mechanisms

**Key ideas:**
- Authentication, session management, access control — all three must work together
- Weakest link defines security posture

**Notes:**
- Input handling approaches: reject known bad (blacklist) vs. accept known good (whitelist) — whitelist is stronger
- Whitelist approach: define exact allowed input, reject everything else
- "Defense in depth" — don't rely on a single control

**Applied:** _Not yet_

---

## Chapter 3 — Web Application Technologies

**Key ideas:**
- HTTP is stateless — sessions are bolted on (cookies, tokens)
- URL structure: scheme, host, port, path, query, fragment

**Notes:**
- HTTP methods: GET (idempotent), POST, PUT, DELETE, PATCH, OPTIONS, HEAD
- Status codes to remember:
  - `200 OK`, `201 Created`, `301 Moved`, `302 Found`
  - `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`
  - `500 Internal Server Error`
- Cookies: `HttpOnly` prevents JS access, `Secure` sends only over HTTPS, `SameSite` prevents CSRF

**Applied:** _Not yet_

---

## Chapter 4 — Mapping the Application

**Key ideas:**
- Enumeration before exploitation — map the full attack surface first
- Spidering + manual browsing together

**Techniques to test:**
- [ ] Spider with Burp Suite
- [ ] robots.txt and sitemap.xml review
- [ ] Check for hidden parameters (Arjun / ffuf)
- [ ] Directory bruteforce (ffuf with wordlist)

**Applied:** _Not yet_

---

_Continue adding chapters as you read..._

---

## Summary (fill when done)

**Best techniques learned:**
1. _TBD_

**Applied to:**
- _TBD_

**Would recommend?** _TBD_
