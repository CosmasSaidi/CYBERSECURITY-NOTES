# Web Fundamentals Reference (DNS, HTTP, Architecture, Security)

Compact notes from web fundamentals study with defensive and offensive context.

---

## DNS Quick Reference

```bash
nslookup website.com
nslookup --type=MX website.com
nslookup --type=TXT website.com
```

Record purpose:
- `A` → domain to IP
- `MX` → mail routing
- `TXT` → text/verification metadata
- `CNAME` → alias mapping

---

## ICMP / Connectivity

```bash
ping 8.8.8.8
```

Observe:
- reachability
- RTT/latency
- packet loss

---

## Network Topologies

- **Star**: central switch/hub, easier management
- **Ring**: circular path, failure impact on path continuity
- **Bus**: shared backbone, simple but less fault tolerant

---

## OSI 7-Layer Snapshot

1. Application
2. Presentation
3. Session
4. Transport
5. Network
6. Data Link
7. Physical

Use this model to map where failures or security controls apply.

---

## HTTP Essentials

Request format:
```http
GET /index.html HTTP/1.1
Host: example.com
```

Response format:
```http
HTTP/1.1 200 OK
Content-Type: text/html
```

Methods:
- `GET`, `POST`, `PUT`, `DELETE`

Status codes:
- `200`, `301`, `403`, `404`, `500`

Common headers:
- `Host`, `User-Agent`, `Content-Type`, `Authorization`, `Cookie`

---

## Cookies

Example:
- `sessionid=abc123`

Typical use:
- session state
- user preferences
- request context continuity

---

## HTML / JavaScript Security Context

- HTML defines document structure and rendered content.
- JavaScript controls interactive browser behavior.

Risk themes:
- **Sensitive data exposure** in source/client-visible code
- **HTML injection** from unsanitized rendering
- **XSS** from unsafe JavaScript/HTML handling

---

## Tooling

- **Wireshark**: inspect packets and protocol behavior
- **Burp Suite**: intercept and analyze HTTP traffic
- **Browser source/dev tools**: inspect client-side exposure

---

## Secure Development Reminders

- Avoid exposing secrets in client-side code
- Validate and sanitize user input
- Encode output by context (HTML/attribute/JS)
- Enforce server-side authorization checks
- Use layered controls (WAF, monitoring, logging)

---

*Reference notes only. No challenge solutions.*
