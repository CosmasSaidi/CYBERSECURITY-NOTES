# HTTP Fundamentals

## Why It Matters
HTTP is the foundation of web communication. Understanding raw HTTP requests is essential for web exploitation, bug bounties, and penetration testing.

## HTTP Request Structure

```
GET /path HTTP/1.1
Host: example.com

```

| Part | Meaning |
|------|---------|
| GET | HTTP method |
| /path | Resource requested |
| HTTP/1.1 | Protocol version |
| Host | Target domain |

**Rule:** Empty line must end every HTTP request.

## Headers

```bash
# Correct format
Host: example.com

# Wrong format
Host=example.com
```

Headers use `:` not `=`

## Tools for HTTP Requests

### Netcat (raw requests)
```bash
nc target.com 80
GET / HTTP/1.1
Host: target.com

```

### Curl
```bash
# Basic request
curl http://target.com/path

# Custom header
curl -H "Host: example.com" http://target.com

# Debug mode (shows full request/response)
curl -v http://target.com
```

### Python requests
```python
import requests

headers = {"Host": "example.com"}
r = requests.get("http://target.com/path", headers=headers)
print(r.text)
print(r.headers)  # Response headers
```

## Host Header

The Host header tells the server which domain is requested.

Multiple domains can share one IP:
```
IP: 10.10.10.10
- admin.company.com
- api.company.com
- dev.company.com
```

Server routes based on Host header value.

## Virtual Host Enumeration

Discover hidden subdomains:
```bash
ffuf -H "Host: FUZZ.target.com" -u http://10.10.10.10
```

## Response Headers

Data can be hidden in headers:
```
HTTP/1.1 200 OK
X-Flag: sensitive_data
```

Check with:
- `curl -v` 
- `r.headers` in Python

## Security Relevance
- Virtual host enumeration reveals hidden sites
- Host header manipulation for access control bypass
- Response headers may leak sensitive info
- Understanding raw HTTP enables manual exploitation
