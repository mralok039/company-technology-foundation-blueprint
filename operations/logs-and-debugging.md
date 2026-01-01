# Logs and Debugging — Finding the Root Cause

## What Are Logs? (Simple Meaning)
Logs are recorded events that describe what happened on a system.

They act as a historical record that engineers use to understand:
- What occurred
- When it occurred
- Why it failed

Without logs, troubleshooting becomes guesswork.

---

## Why Logs Exist
Servers handle thousands of events without human supervision.

When an issue occurs:
- No one is watching the screen
- The system must explain itself

Logs provide that explanation.

---

## Where Logs Live in Linux
On Linux systems, most logs are stored under:

/var/log

This directory contains:
- System logs
- Application logs
- Service-specific logs

It represents the operational history of the server.

---

## Nginx Logs (Practical Example)

### Access Log
Location:
/var/log/nginx/access.log

Purpose:
- Records every incoming request
- Shows source IP, request path, and response code
- Confirms whether traffic reached the server

---

### Error Log
Location:
/var/log/nginx/error.log

Purpose:
- Records failures and abnormal behavior
- Shows permission errors, configuration issues, and crashes
- Explains why a request failed

---

## Access Logs vs Error Logs
Access logs answer:
- Did the request arrive?

Error logs answer:
- Why did it fail?

Both are required to understand system behavior.

---

## Common HTTP Status Codes
Some commonly observed status codes include:
- 200: Request successful
- 403: Permission denied
- 404: Resource not found
- 500: Internal server error

These codes guide engineers to the correct investigation path.

---

## How Engineers Debug Issues
Experienced engineers follow a structured approach:

1. Verify the service is running
2. Check access logs for incoming requests
3. Check error logs for failures
4. Identify root cause
5. Apply fix
6. Verify resolution

This process avoids panic and unnecessary changes.

---

## Real-World Debugging Scenario
A website appears down even though the server is running.

Investigation steps:
- Access log shows requests arriving
- Error log shows permission denied
- Root cause identified as incorrect file permissions
- Permissions fixed
- Service restored

Logs made the issue clear and resolvable.

---

## Key Takeaway
Logs are the primary source of truth during incidents.
Engineers do not guess — they read logs, confirm facts, and fix root causes.
