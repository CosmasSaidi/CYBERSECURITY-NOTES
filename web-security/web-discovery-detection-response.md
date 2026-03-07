# Web Discovery Detection & Response

Practical notes from TryHackMe: **Offensive Security Intro** and **Defensive Security Intro**.

---

## Attack Pattern: Directory Enumeration

Attackers probe common paths to discover hidden functionality:

```bash
dirb http://fakebank.thm
```

Wordlist commonly used:
- `/usr/share/dirb/wordlists/common.txt`

Typical responses to monitor:
- `200` successful path discovered
- `301` redirect (often still interesting)
- `404` path not found

---

## Why It Matters

Hidden endpoints can expose sensitive business functions without proper authorization checks.

Example risk observed:
- discovered endpoint: `/bank-deposit`
- unauthorized action possible on arbitrary account

This is a **business logic access-control failure**.

---

## SOC/SIEM Investigation Flow

1. Detect alert category (e.g., **Web Discovery Attack**)
2. Identify source IP and affected service
3. Confirm scanning pattern (high request volume, patterned paths)
4. Contain attacker activity
5. Add preventive controls
6. Monitor for recurrence

---

## Core Defensive Controls

### 1) Block Source IP
Temporary containment while analysis continues.

### 2) Apply Rate Limiting
Limit requests/sec to slow or stop brute-force endpoint discovery.

### 3) Tune WAF Rules
Block common directory brute-force patterns and suspicious request signatures.

---

## Practical Indicators

- Spike in 404 responses from one source
- Sequential or dictionary-like path requests
- High request rate with low normal browsing behavior
- Repeated probing of admin/bank/config-like routes

---

## Hardening Checklist

- Enforce authentication/authorization on all sensitive actions
- Remove or protect unused internal routes
- Normalize and log URI patterns
- Alert on abnormal 404/401/403 ratios
- Apply WAF + rate limiting + monitoring together (defense in depth)
- Periodically test exposure using controlled enumeration

---

## Tooling Encountered

- `dirb` (offensive enumeration)
- browser and terminal
- SIEM dashboard and SOC workflow

---

## Summary

Understanding offensive enumeration helps improve defensive detection quality. Detect early, contain quickly, and harden systematically.
