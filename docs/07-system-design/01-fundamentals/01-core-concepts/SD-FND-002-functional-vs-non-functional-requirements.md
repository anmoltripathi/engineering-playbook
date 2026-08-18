# Functional vs Non-Functional Requirements

> **Module:** System Design Fundamentals  
> **Document ID:** SD-FND-002  
> **Difficulty:** 🟢 Beginner  
> **Reading Time:** 35–45 Minutes

---

## Overview

Before designing a system, you need to understand what the system is expected to do and what constraints it must operate under.

These requirements are broadly divided into two categories:

```text
Requirements
     │
     ├── Functional Requirements
     │
     └── Non-Functional Requirements
```

Functional requirements describe **what the system does**.

Non-functional requirements describe **how well the system must operate**.

This distinction is fundamental to System Design because architecture should be driven by requirements rather than technology preferences.

---

## Prerequisites

Before starting this document, you should understand:

- Basic software development concepts
- Client-server architecture
- APIs
- Databases
- Basic System Design concepts

Recommended:

- [SD-FND-001 — What Is System Design?](SD-FND-001-what-is-system-design.md)

---

## Learning Objectives

After completing this document, you should be able to:

- Define functional requirements.
- Define non-functional requirements.
- Explain the difference between them.
- Identify requirements from a product description.
- Convert vague requirements into measurable constraints.
- Prioritize requirements.
- Understand how requirements influence architecture.
- Apply requirements analysis to a real system.

---

# Concept

## What Are Requirements?

A requirement describes something the system must satisfy.

For example:

> Users should be able to upload profile pictures.

This is a functional requirement.

Another requirement might be:

> The system should support 100,000 concurrent users.

This is a non-functional requirement.

Both affect the system design.

---

# Functional Requirements

Functional requirements describe:

> **What should the system do?**

They represent system capabilities and business behavior.

Examples:

```text
User Registration
User Login
Create Order
Cancel Order
Upload File
Search Products
Send Message
Generate Report
Process Payment
```

These describe actions the system must perform.

---

## Example: E-Commerce System

Suppose we're designing an e-commerce platform.

Functional requirements might include:

```text
User
 │
 ├── Register
 ├── Login
 ├── Search Products
 ├── View Product
 ├── Add Product to Cart
 ├── Place Order
 ├── Make Payment
 └── Track Order
```

Each capability is a functional requirement.

---

# Characteristics of Functional Requirements

Functional requirements are generally:

- Behavior-oriented
- Feature-oriented
- User-facing or business-facing
- Testable through expected behavior

Example:

> A customer can add a product to their shopping cart.

This can be tested.

```text
Given:
Product exists.

When:
Customer clicks "Add to Cart".

Then:
Product appears in the customer's cart.
```

---

# Non-Functional Requirements

Non-functional requirements describe:

> **How well should the system perform its responsibilities?**

They define system qualities and constraints.

Common categories include:

```text
Performance
Scalability
Availability
Reliability
Security
Durability
Consistency
Maintainability
Observability
Cost
```

---

# Example

Functional:

> Users can upload profile pictures.

Non-functional:

> A profile picture upload should complete within 2 seconds for 95% of requests.

The first describes **what the system does**.

The second describes **how well it does it**.

---

# Major Categories of Non-Functional Requirements

## 1. Performance

How quickly should the system respond?

Example:

```text
95th percentile API latency < 200 ms
```

---

## 2. Scalability

How much growth should the system support?

Example:

```text
100,000 requests/second
```

---

## 3. Availability

How often should the system be accessible?

Example:

```text
99.99% availability
```

---

## 4. Reliability

How consistently should the system perform correctly?

Example:

```text
Failed payments should not result
in duplicate charges.
```

---

## 5. Durability

How safely must data survive failures?

Example:

```text
Committed financial transactions
must not be lost after a server failure.
```

---

## 6. Security

How should the system protect data and operations?

Examples:

```text
Authentication
Authorization
Encryption
Audit Logging
Secrets Management
```

---

## 7. Consistency

How quickly should data changes become visible across the system?

For example:

```text
User updates address
        ↓
All subsequent reads
        ↓
Should return the new address
```

The required consistency model depends on the business requirement.

---

## 8. Maintainability

How easily can engineers modify the system?

Consider:

- Code structure
- Service boundaries
- Testing
- Documentation
- Deployment process

---

## 9. Observability

Can engineers understand what the system is doing?

Typical requirements include:

```text
Logs
Metrics
Traces
Alerts
Dashboards
```

---

## 10. Cost

How much should the system cost to operate?

Cost is often overlooked during System Design interviews.

A technically excellent architecture may still be inappropriate if it is unnecessarily expensive.

---

# Functional vs Non-Functional

Consider a ride-sharing application.

| Requirement | Type |
|---|---|
| User can request a ride | Functional |
| Driver can accept a ride | Functional |
| User can cancel a ride | Functional |
| User can track driver location | Functional |
| API response < 200 ms | Non-functional |
| 99.99% availability | Non-functional |
| Support 1M concurrent users | Non-functional |
| Payment data encrypted | Non-functional |
| System recovers automatically from failures | Non-functional |

The distinction becomes clear:

```text
Functional
     ↓
What does the system do?

Non-Functional
     ↓
How well does it do it?
```

---

# Requirements Are Connected

Functional and non-functional requirements should not be treated as independent lists.

They influence each other.

Consider:

> Users can upload videos.

Functional requirement.

Now add:

```text
10 million uploads/day
```

Now the architecture changes.

We may need:

```text
Upload Service
     ↓
Object Storage
     ↓
Message Queue
     ↓
Video Processing Workers
     ↓
CDN
```

The functional requirement tells us **what** the system must do.

The non-functional requirements determine many aspects of **how the system must be designed**.

---

# Why Vague Requirements Are Dangerous

Consider:

> The system should be fast.

What does "fast" mean?

```text
100 ms?
500 ms?
2 seconds?
5 seconds?
```

It cannot directly guide architecture.

Instead:

> 95% of read requests should complete within 200 ms.

Now we have a measurable requirement.

---

# Quantifying Requirements

Good System Design begins by converting vague statements into numbers.

### Vague

```text
High traffic
```

### Better

```text
100,000 requests/second
```

---

### Vague

```text
Highly available
```

### Better

```text
99.99% availability
```

---

### Vague

```text
Fast response
```

### Better

```text
p95 latency < 200 ms
```

---

### Vague

```text
Large storage
```

### Better

```text
500 GB new data/day
```

Numbers allow engineers to reason about capacity.

---

# Percentiles Matter

Latency is often described using percentiles.

For example:

```text
p50 = 80 ms
p95 = 180 ms
p99 = 350 ms
```

This means:

- 50% of requests complete within 80 ms.
- 95% complete within 180 ms.
- 99% complete within 350 ms.

Average latency alone can hide slow requests.

For large systems, p95 and p99 are often more useful for understanding tail latency.

---

# Requirements Priority

Not every requirement has equal importance.

A useful classification is:

```text
Must Have
Should Have
Could Have
Won't Have
```

For example, a payment system:

### Must Have

```text
Correct payment processing
Security
Transaction integrity
```

### Should Have

```text
High availability
Low latency
```

### Could Have

```text
Advanced analytics
```

This helps prevent over-engineering.

---

# Hard vs Soft Requirements

Some requirements are strict.

Example:

> A payment must never be charged twice.

This is a hard business constraint.

Other requirements may be targets.

Example:

> API latency should normally remain below 200 ms.

This may be an engineering objective rather than an absolute guarantee.

Understanding this distinction helps engineers make better trade-offs.

---

# Requirements → Architecture

The most important relationship is:

```text
Requirements
      ↓
Constraints
      ↓
Architecture
```

Consider three systems.

---

## System A — Internal HR Tool

```text
Users:
50

Availability:
99%

Traffic:
Low
```

Possible architecture:

```text
Frontend
   ↓
API
   ↓
Database
```

Simple.

---

## System B — E-Commerce Platform

```text
Users:
Millions

Availability:
99.99%

Traffic:
High

Latency:
Low
```

Possible architecture:

```text
CDN
 ↓
Load Balancer
 ↓
Application Servers
 ↓
Cache
 ↓
Database
```

Additional components may be required.

---

## System C — Global Video Platform

```text
Users:
Hundreds of millions

Traffic:
Massive

Storage:
Petabytes+

Global:
Yes
```

Architecture becomes significantly more complex:

```text
Users
  ↓
Global Traffic Management
  ↓
CDN
  ↓
Regional Services
  ↓
Object Storage
  ↓
Processing Pipeline
  ↓
Distributed Data Stores
```

The architecture is different because the requirements are different.

---

# Example

## Design a URL Shortener

Suppose the product requirement is:

> Users can create short URLs and redirect visitors to the original URL.

### Functional Requirements

```text
Create short URL
       ↓
Store mapping
       ↓
Redirect short URL
```

Additional functional requirements might include:

- Custom aliases
- URL expiration
- User ownership
- URL deletion
- Click tracking

---

## Non-Functional Requirements

Suppose we define:

```text
Read traffic:
100,000 requests/second

Write traffic:
1,000 requests/second

Availability:
99.99%

Redirect latency:
< 100 ms at p95
```

Now architecture decisions become possible.

For example:

```text
High Read Traffic
      ↓
Caching

High Availability
      ↓
Redundant Servers

Low Latency
      ↓
Cache + Optimized Storage

High Traffic
      ↓
Horizontal Scaling
```

Requirements are directly driving architecture.

---

# Diagram

```text
                    Requirements
                         │
                         ▼
                 ┌───────────────┐
                 │   Constraints │
                 └───────┬───────┘
                         │
                         ▼
                 ┌───────────────┐
                 │   Capacity    │
                 │   Estimation  │
                 └───────┬───────┘
                         │
                         ▼
                 ┌───────────────┐
                 │  Architecture │
                 └───────┬───────┘
                         │
             ┌───────────┼───────────┐
             ▼           ▼           ▼
          Storage      Network     Compute
             │           │           │
             └───────────┼───────────┘
                         ▼
                  Trade-offs
```

---

# Real-World / Real Project

Consider the **CDS Journey Staff Management System**.

A simplified functional requirement could be:

> Admin users can generate monthly payroll slips.

That leads to functionality such as:

```text
Admin
  ↓
Payroll Screen
  ↓
Select Month
  ↓
Generate Payroll
  ↓
Calculate Salary
  ↓
Generate Slip
  ↓
Store Payroll Record
```

Now consider non-functional requirements:

```text
Security
    ↓
Only authorized administrators can access payroll.

Reliability
    ↓
Payroll must not be accidentally generated twice.

Auditability
    ↓
Finalized payroll records must remain traceable.

Performance
    ↓
Payroll generation should complete within
an acceptable operational time.

Data Integrity
    ↓
Financial calculations must not be silently lost
or corrupted.
```

Notice how the non-functional requirements influence architecture.

For example, authorization, transaction boundaries, audit records, and immutable finalized payroll records become architectural concerns.

---

# Engineering Perspective

A strong engineer does not simply collect requirements.

They **challenge and clarify them**.

Suppose a product requirement says:

> "The application must support millions of users."

Ask:

```text
Millions of registered users?

Millions of active users?

Millions of concurrent users?

Millions of requests per second?
```

These are completely different requirements.

Similarly:

> "The system must be highly available."

Ask:

```text
99%?
99.9%?
99.99%?
99.999%?
```

Each additional availability target has architectural and operational consequences.

---

# Questions Engineers Should Ask

When receiving a new system requirement, ask:

### Traffic

```text
How many users?

How many active users?

Requests per second?

Peak traffic?
```

### Data

```text
How much data?

How fast does it grow?

How long must it be retained?
```

### Performance

```text
What latency is acceptable?

Which operations are latency-sensitive?
```

### Availability

```text
What downtime is acceptable?

Are there business-critical operations?
```

### Consistency

```text
Must reads immediately reflect writes?

Can stale data be tolerated?
```

### Security

```text
What data is sensitive?

Who can access it?

What must be audited?
```

### Cost

```text
What infrastructure budget exists?

Which requirements are worth additional cost?
```

---

# Best Practices

## 1. Clarify Before Designing

Never make architectural decisions based on ambiguous requirements.

---

## 2. Quantify Whenever Possible

Use measurable targets.

```text
p95 < 200 ms

99.99% availability

100K requests/sec

500 GB/day
```

---

## 3. Separate Must-Haves From Nice-to-Haves

Prioritize requirements before designing.

---

## 4. Identify Business-Critical Operations

Not every feature needs the same availability, consistency, or latency.

---

## 5. Think About Peak Load

Average traffic can hide the real capacity requirement.

---

## 6. Document Assumptions

If exact numbers aren't available, state assumptions explicitly.

Example:

> Assume 1 million daily active users.

This makes the rest of the design explainable.

---

# Common Mistakes

## Mistake 1 — Designing Before Understanding Requirements

```text
Kafka
Redis
Microservices
Kubernetes
```

These are technologies, not requirements.

---

## Mistake 2 — Using "High", "Large", or "Fast"

These words are too vague.

Quantify them.

---

## Mistake 3 — Only Thinking About Average Traffic

Peak traffic often determines architecture.

---

## Mistake 4 — Treating Every Feature Equally

Critical payment operations may require stronger guarantees than analytics dashboards.

---

## Mistake 5 — Ignoring Business Context

Technical decisions should support business priorities.

---

## Mistake 6 — Inventing Requirements

If the product doesn't require multi-region deployment, don't assume it does.

State assumptions instead.

---

# Interview Questions

These questions are intentionally focused on understanding requirements. A dedicated interview module will later cover the complete interview methodology.

### Beginner

1. What is a functional requirement?

2. What is a non-functional requirement?

3. Give three examples of each.

4. Why are non-functional requirements important?

### Intermediate

5. How do functional requirements influence architecture?

6. Why should non-functional requirements be quantified?

7. Why is p95 latency more useful than average latency in some cases?

8. How would you clarify the requirement "the system should support millions of users"?

### Advanced

9. How would you prioritize conflicting non-functional requirements?

10. How would you design differently for 99.9% vs 99.99% availability?

11. How can business requirements influence technical architecture?

12. What assumptions would you make when requirements are incomplete?

---

# Hands-on Exercise

Choose one system:

```text
URL Shortener
E-Commerce
Chat Application
Notification System
Employee Management System
```

Create a requirements document.

## Step 1 — Functional Requirements

Write at least 8.

```text
1.
2.
3.
4.
5.
6.
7.
8.
```

## Step 2 — Non-Functional Requirements

Define:

```text
Availability:
Latency:
Throughput:
Scalability:
Security:
Durability:
Consistency:
```

## Step 3 — Quantify Them

Convert:

```text
High traffic
```

into something measurable:

```text
100,000 requests/second
```

## Step 4 — Identify Priorities

Mark each requirement:

```text
P0 — Critical
P1 — Important
P2 — Nice to Have
```

## Step 5 — Explain the Architectural Impact

For every major requirement, write:

```text
Requirement
     ↓
Architectural consequence
```

Example:

```text
99.99% Availability
        ↓
Redundant application instances
        ↓
Load balancing
        ↓
Failure detection
```

---

# Key Takeaways

- Functional requirements define **what** a system does.
- Non-functional requirements define **how well** it does it.
- Both are essential to System Design.
- Requirements should be measurable whenever possible.
- Peak traffic matters.
- Business-critical operations may require stronger guarantees.
- Requirements directly influence architecture.
- Assumptions should be explicit.
- Technology should follow requirements, not the other way around.

---

# Summary

A good System Design begins with a clear understanding of requirements.

The basic relationship is:

```text
Business Problem
       ↓
Functional Requirements
       ↓
Non-Functional Requirements
       ↓
Constraints
       ↓
Capacity
       ↓
Architecture
```

Functional requirements tell us what capabilities the system needs.

Non-functional requirements tell us the operational characteristics those capabilities must satisfy.

Together, they establish the constraints within which the architecture must operate.

The better the requirements analysis, the more defensible the architecture becomes.

---

# Further Reading

- [SD-FND-001 — What Is System Design?](SD-FND-001-what-is-system-design.md)
- SD-FND-003 — Scalability *(next)*
- SD-FND-004 — Availability *(upcoming)*
- SD-FND-005 — Reliability *(upcoming)*

---

## Navigation

| Previous | Module | Next |
|---|---|---|
| [← What Is System Design](SD-FND-001-what-is-system-design.md) | [System Design Fundamentals](../README.md) | [Scalability →](SD-FND-003-scalability.md) |

---

## Continue Your Journey

You now know how to translate a product requirement into measurable system requirements.

The next question is:

> **What happens when the workload grows?**

Continue with:

**[SD-FND-003 — Scalability →](SD-FND-003-scalability.md)**

---

**Document ID:** `SD-FND-002`  
**Module:** `01-fundamentals / 01-core-concepts`  
**Status:** ✅ Complete