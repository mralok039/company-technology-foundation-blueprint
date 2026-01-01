# Subnet Design — Public and Private Subnets

## Why a VPC Is Split into Subnets
A VPC represents a private network, but placing all resources into a single network is unsafe and difficult to manage.

Subnets are created to:
- Separate resources by role
- Reduce the impact of security incidents
- Control traffic paths
- Enforce architectural boundaries

This separation is a core security and reliability principle.

---

## What Is a Subnet?
A subnet is a smaller network created within a VPC using a subset of the VPC’s IP address range.

Each subnet:
- Has its own IP range
- Is associated with a route table
- Follows specific traffic rules

Subnets allow fine-grained control over network behavior.

---

## What Makes a Subnet Public?
A subnet is considered **public** if:
- Its route table contains a route to an Internet Gateway
- Resources inside the subnet can send traffic to the internet
- Internet traffic can reach resources (if allowed by security rules)

Public subnets are typically used for:
- Web servers
- Load balancers
- Bastion hosts

A public subnet is not insecure by default — it is simply internet-reachable by design.

---

## What Makes a Subnet Private?
A subnet is considered **private** if:
- It does not have a route to an Internet Gateway
- Internet traffic cannot directly reach resources inside it

Private subnets are typically used for:
- Databases
- Internal backend services
- Application components that should not be exposed

Private subnets provide strong isolation and reduce attack surface.

---

## Where Different Resources Should Live
Correct placement of resources is critical:

- Web servers:
  - Public subnet
  - Internet-facing by design

- Application backends:
  - Private subnet
  - Accessed only by internal services

- Databases:
  - Private subnet
  - Never directly exposed to the internet

Incorrect placement can lead to serious security vulnerabilities.

---

## Common Beginner Mistakes
Some common mistakes include:
- Placing databases in public subnets
- Assigning public IPs to private resources
- Using overly permissive network access rules

These mistakes have caused real-world data breaches.

---

## Real-World Engineering Perspective
Experienced engineers design networks by asking:
- Does this resource need internet access?
- What is the blast radius if this is compromised?
- Can this be isolated further?

Subnet design is one of the most important early architecture decisions.

---

## Key Takeaway
Public and private subnets exist to enforce separation of concerns.
Correct subnet design improves security, reliability, and long-term scalability.

