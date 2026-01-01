# Server Restart and Recovery — Preventing Downtime

## What Happens During a Server Reboot
When a server is rebooted, several things happen in sequence:

- The operating system shuts down
- Memory (RAM) is cleared
- The kernel loads again
- System services are started based on configuration
- Network connectivity is restored

A reboot does not guarantee that applications will start automatically.

---

## Process vs Service (Critical Difference)

### Process
- Started manually
- Runs only while the system is active
- Stops during reboot
- Requires manual restart

### Service
- Managed by the operating system
- Can be configured to start automatically
- Monitored and controlled by system tools

Production applications must run as services, not manual processes.

---

## Why Services Fail After Restart
A common outage occurs when:
- An application is started manually
- The server is rebooted for updates
- The application does not restart
- The system appears healthy but the service is down

This is a frequent real-world issue.

---

## How Auto-Start Prevents Downtime
Services can be configured to start automatically at boot time.

When enabled:
- The operating system starts the service during boot
- Manual intervention is not required
- Downtime is minimized after restarts

This is a standard production practice.

---

## Verifying Recovery After Restart
Experienced engineers always verify:

- Instance status (running)
- Service status
- Network accessibility
- Application availability

This verification ensures systems are truly recovered.

---

## Common Recovery Checklist
After a reboot, engineers check:

1. Is the server running?
2. Is the service running?
3. Are firewall rules intact?
4. Is the correct IP or DNS in use?

This checklist prevents prolonged outages.

---

## Real-World Engineering Perspective
Engineers do not assume recovery.
They verify behavior after every restart.

Restart procedures are planned, tested, and documented to ensure reliability.

---

## Key Takeaway
Server restarts are routine, but unplanned downtime is not.
Running applications as services and verifying recovery are essential operational practices.

