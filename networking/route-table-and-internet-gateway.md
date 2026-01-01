# Route Tables and Internet Gateway — How Traffic Moves

## What Is a Route? (Simple Meaning)
A route is an instruction that tells network traffic where it should go next.

Every networked system needs routing rules.
Without routes, traffic has no direction and cannot reach its destination.

---

## What Is a Route Table?
A route table is a collection of routing rules that determine how traffic is forwarded.

Each route consists of:
- Destination (where traffic is going)
- Target (how traffic should get there)

Every subnet must be associated with a route table.

---

## Why Subnets Need Route Tables
Subnets do not automatically know how to reach other networks.

Route tables explicitly define:
- Internal communication within the VPC
- External communication to the internet
- Which paths are allowed or denied

Without correct routes, resources become unreachable even if everything else is configured correctly.

---

## The Local Route (Internal Traffic)
Every route table contains a default local route.

This route allows:
- Communication between resources inside the same VPC
- Private IP connectivity across subnets

This enables internal services to function properly.

---

## What Is an Internet Gateway?
An Internet Gateway (IGW) is a component that connects a VPC to the public internet.

Important characteristics:
- Attached to a VPC, not a subnet
- Provides a path for internet-bound traffic
- Enables inbound and outbound internet communication

Without an Internet Gateway, internet access is impossible.

---

## The Critical Internet Route
A subnet becomes public when its route table contains the following route:

0.0.0.0/0 → Internet Gateway

This rule means:
- Any traffic destined outside the VPC should be sent to the internet

This single route is what enables public internet access.

---

## Why Public Subnets Work
A public subnet works only when all of the following exist:
- A route to the Internet Gateway
- A public IP address on the resource
- Security Group rules allowing traffic

If any one of these is missing, the resource will not be reachable.

---

## Why Private Subnets Do Not Have Direct Internet Access
Private subnets do not include a route to the Internet Gateway.

As a result:
- Resources cannot be reached from the internet
- Outbound internet access is blocked unless explicitly allowed via other mechanisms

This design provides strong isolation and security.

---

## Common Failure Scenario
A frequent outage occurs when:
- An instance has a public IP
- Security Groups are correctly configured
- The subnet route table is missing the Internet Gateway route

The result is a service that appears healthy but is unreachable.

---

## Real-World Engineering Perspective
Experienced engineers always verify routing when debugging connectivity issues.

If traffic is not reaching a resource:
- Routes are checked before changing application code
- Network paths are traced logically
- Assumptions are avoided

Routing errors are one of the most common causes of cloud outages.

---

## Key Takeaway
Route tables define how traffic flows.
Internet Gateways enable internet access.
Correct routing is required before any service can be reachable.

