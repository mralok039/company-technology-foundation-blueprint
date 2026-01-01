# Common Outages and Fixes — Real Failure Scenarios

This document describes common infrastructure failures, their root causes, and how they were resolved.
These scenarios represent real-world issues that frequently occur in cloud environments.

---

## Outage 1: Website Not Loading Due to Firewall Misconfiguration

### What Happened
The web server was running, but the website was not accessible from the browser.

### Root Cause
The inbound firewall rule allowing HTTP (port 80) traffic was missing from the Security Group.

### How It Was Fixed
- Verified instance and service were running
- Reviewed Security Group inbound rules
- Added HTTP (port 80) rule
- Confirmed website accessibility

### Prevention
- Use a checklist when modifying firewall rules
- Open only required ports
- Verify access after changes

---

## Outage 2: Website Down After Server Reboot

### What Happened
After a server reboot, the website did not come back online automatically.

### Root Cause
The web service was not configured to start automatically at boot time.

### How It Was Fixed
- Checked service status
- Enabled the service to start at boot
- Rebooted the server to verify recovery

### Prevention
- Run production applications as services
- Enable auto-start for critical services
- Always verify behavior after reboots

---

## Outage 3: Website Unreachable Despite Correct Configuration

### What Happened
The server had a public IP and correct firewall rules, but the website was unreachable.

### Root Cause
The subnet route table was missing a route to the Internet Gateway.

### How It Was Fixed
- Reviewed subnet route table
- Added route to Internet Gateway
- Verified traffic flow

### Prevention
- Validate routing during network setup
- Check routes before changing application settings

---

## Outage 4: Data Loss After Instance Termination

### What Happened
An EC2 instance was terminated, and all application data was lost.

### Root Cause
The root EBS volume was deleted automatically during termination.

### How It Was Fixed
- Instance was recreated
- Data had to be restored from backups (if available)

### Prevention
- Understand storage lifecycle behavior
- Use snapshots and backups
- Never assume data persists after termination

---

## Outage 5: Private Server Unable to Access the Internet

### What Happened
A private subnet server could not download updates or install packages.

### Root Cause
No NAT Gateway was configured for outbound internet access.

### How It Was Fixed
- Added a NAT Gateway in a public subnet
- Updated private subnet route table
- Verified outbound connectivity

### Prevention
- Plan outbound access for private resources
- Never attach private subnets directly to the Internet Gateway

---

## Engineering Takeaway
Most outages are not caused by complex failures.
They occur due to misunderstandings of fundamentals.

Strong foundations, careful planning, and verification prevent the majority of incidents.

