# What Is System Design?

> **Module:** System Design Fundamentals  
> **Document ID:** SD-FND-001  
> **Difficulty:** 🟢 Beginner  
> **Reading Time:** 30–40 Minutes

---

## Overview

System Design is the process of defining how the components of a software system work together to satisfy business requirements, technical constraints, and operational goals.

It answers questions such as:

- What components does the system need?
- How do those components communicate?
- Where is data stored?
- How does the system handle increasing traffic?
- What happens when a component fails?
- How is the system secured?
- How do we monitor it?
- What trade-offs are we making?

System Design is therefore much more than drawing boxes and arrows.

It is the process of making engineering decisions about how software should be:

- Structured
- Communicated
- Stored
- Scaled
- Secured
- Monitored
- Operated
- Evolved

---

## Prerequisites

Before starting System Design, you should have a basic understanding of:

- Programming fundamentals
- HTTP and APIs
- Databases
- Client-server architecture
- Basic networking
- Software development lifecycle

You do **not** need to already know distributed systems, Kubernetes, Kafka, or cloud architecture.

Those concepts will be introduced progressively throughout this learning path.

---

## Learning Objectives

After completing this document, you should be able to:

- Define System Design.
- Explain why System Design matters.
- Distinguish an application from a larger system.
- Understand functional and non-functional concerns.
- Identify common system-level constraints.
- Explain why architecture changes as systems scale.
- Understand the role of trade-offs in architecture.
- Describe a basic System Design workflow.

---

# Concept

## What Does System Design Mean?

Consider a simple application:

```text
User
  │
  ▼
Application
  │
  ▼
Database
```

For a small internal application, this architecture might be completely sufficient.

But as the system grows, new requirements appear.

```text
More Users
    ↓
More Traffic
    ↓
More Servers
```

Then:

```text
More Servers
    ↓
Load Balancer
```

Then:

```text
More Database Traffic
    ↓
Caching
    ↓
Database Replication
```

Then:

```text
Traffic Spikes
    ↓
Message Queue
```

Then:

```text
Global Users
    ↓
CDN / Multi-Region Architecture
```

System Design is the discipline of deciding **when and why these architectural changes are necessary**.

---

# Why System Design Matters

A system can be functionally correct and still be poorly designed.

Consider:

```text
100 Users
    ↓
Application
    ↓
Database
```

Everything works.

Now traffic increases:

```text
100
 ↓
1,000
 ↓
10,000
 ↓
100,000
 ↓
1,000,000 Users
```

The original architecture may no longer be sufficient.

Possible problems include:

- Slow responses
- Database overload
- Server crashes
- Increased latency
- Failed requests
- Data inconsistency
- Downtime

System Design helps engineers anticipate these problems and design appropriate solutions.

---

# System Design Is About Constraints

Every system operates under constraints.

Typical constraints include:

```text
Traffic
Storage
Latency
Availability
Reliability
Consistency
Security
Cost
Team Size
Operational Complexity
```

There is rarely a perfect architecture.

Instead, engineers choose an architecture that provides the right balance for the requirements.

---

# Functional Requirements

Functional requirements describe:

> **What should the system do?**

For a URL Shortener:

```text
Long URL
   ↓
Create Short URL
   ↓
Store Mapping
   ↓
Return Short URL
```

Functional requirements might include:

- Create a short URL.
- Redirect users to the original URL.
- Validate submitted URLs.
- Associate URLs with users.
- Allow users to delete their URLs.

These requirements describe system behavior.

---

# Non-Functional Requirements

Non-functional requirements describe:

> **How well should the system perform?**

Examples:

```text
Availability
99.99%

Latency
< 100 ms

Throughput
100,000 requests/second

Durability
No data loss

Security
Encrypted communication
```

These requirements have a major influence on architecture.

For example:

A system requiring:

```text
99.99% availability
```

needs a different architecture from an internal application that can tolerate several hours of downtime.

Functional and non-functional requirements are explored in depth in the next document.

---

# Application vs System

An application is often only one part of a larger system.

Consider an e-commerce platform:

```text
                    E-Commerce System

                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
        ▼                  ▼                  ▼
   Web Client         Mobile Client         APIs
                                              │
              ┌───────────────┬───────────────┤
              │               │               │
              ▼               ▼               ▼
        Product Service   Order Service   Payment Service
              │               │               │
              └───────────────┼───────────────┘
                              ▼
                         Data Storage
```

The system may also include:

- Authentication
- Search
- Caching
- Messaging
- Notifications
- Monitoring
- Logging
- External payment providers

The application is one component.

The **system** is the complete ecosystem and the relationships between its components.

---

# System Design vs Software Development

Software development often focuses on:

```text
Requirements
    ↓
Features
    ↓
Components
    ↓
Functions
    ↓
Code
```

System Design expands the scope:

```text
Components
    ↓
Communication
    ↓
Data
    ↓
Infrastructure
    ↓
Scaling
    ↓
Failure
    ↓
Security
    ↓
Operations
```

Both perspectives are necessary.

A strong software engineer needs to understand how individual code fits into the larger system.

---

# System Design vs Software Architecture

These terms overlap, but they are not identical.

### Software Architecture

Primarily focuses on:

```text
Components
Modules
Services
Boundaries
Dependencies
```

### System Design

Includes architecture plus:

```text
Architecture
    +
Networking
    +
Data
    +
Scaling
    +
Reliability
    +
Security
    +
Observability
    +
Operational Concerns
    +
Trade-offs
```

System Design therefore considers a broader operational environment.

---

# How System Design Works

A typical System Design process follows this sequence:

```text
Requirements
      ↓
Constraints
      ↓
Capacity
      ↓
Architecture
      ↓
Data Model
      ↓
APIs
      ↓
Scaling
      ↓
Reliability
      ↓
Security
      ↓
Observability
      ↓
Trade-offs
```

The order is important.

You should not start by selecting technologies.

Start with the problem.

---

# Example

## Notification System

Suppose the requirement is:

> Build a system that sends notifications to users.

A beginner might immediately create:

```text
Notification API
       ↓
Database
```

An engineer asks more questions.

### What notification types?

```text
Email
SMS
Push
In-App
```

### How much traffic?

```text
100 / second

10,000 / second

1,000,000 / second
```

### What latency is acceptable?

```text
Immediately
    OR
Within 5 seconds
    OR
Within 5 minutes
```

### What happens if a provider fails?

```text
SMS Provider
     ↓
Failure
```

Should the system:

- Retry?
- Switch providers?
- Queue the notification?
- Mark it failed?

### Can duplicates occur?

Suppose a retry succeeds after the first request actually succeeded.

You could accidentally send:

```text
Payment Successful

Payment Successful
```

Therefore the design must consider idempotency and delivery guarantees.

This is why System Design starts with requirements rather than technologies.

---

# Diagram

## Simple Architecture

For a small notification system:

```text
┌──────────┐
│  Client  │
└────┬─────┘
     │
     ▼
┌───────────────┐
│ Notification  │
│      API      │
└──────┬────────┘
       │
       ▼
┌───────────────┐
│   Database    │
└───────────────┘
```

This may be sufficient for low traffic.

---

## Scaled Architecture

At larger scale:

```text
                         ┌───────────────┐
                         │ Email Provider│
                         └───────▲───────┘
                                 │
                         ┌───────┴───────┐
                         │ Notification  │
                         │    Workers    │
                         └───────▲───────┘
                                 │
┌──────────┐   ┌────────────┐   │
│  Client  │──▶│ Notification│──┘
└──────────┘   │     API     │
               └──────┬─────┘
                      │
                      ▼
               ┌─────────────┐
               │ Message     │
               │ Queue       │
               └──────┬──────┘
                      │
                      ▼
               ┌─────────────┐
               │  Database   │
               └─────────────┘
```

This architecture allows:

- Asynchronous processing
- Traffic buffering
- Worker scaling
- Retry handling
- Failure isolation

The architecture became more complex because the requirements justified that complexity.

---

# Real-World / Real Project

Consider an employee management system.

A simple architecture could be:

```text
React
  │
  ▼
FastAPI
  │
  ▼
MongoDB
```

For a small organization, this may be completely appropriate.

If the system grows significantly, engineers might eventually introduce:

```text
                    Load Balancer
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
          API Server             API Server
              │                     │
              └──────────┬──────────┘
                         ▼
                       Cache
                         │
                         ▼
                    Database
```

Later, specific workloads might become asynchronous:

```text
Payroll Request
      ↓
API
      ↓
Message Queue
      ↓
Payroll Worker
      ↓
Database
```

The important engineering principle is:

> **Do not add these components simply because large systems use them. Add them when requirements and measured bottlenecks justify them.**

---

# System Design Levels

System Design can be considered at multiple levels.

## Level 1 — Component Design

```text
Component
    ↓
Responsibility
    ↓
Interface
```

Example:

```text
NotificationService
```

---

## Level 2 — Application Architecture

```text
Frontend
    ↓
API
    ↓
Services
    ↓
Database
```

---

## Level 3 — Distributed Architecture

```text
Clients
    ↓
Load Balancer
    ↓
Services
    ↓
Cache
    ↓
Message Queue
    ↓
Databases
```

---

## Level 4 — Global Architecture

```text
                Global Traffic
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
         Region A             Region B
             │                   │
        Services              Services
             │                   │
          Database             Database
```

Each level introduces additional engineering concerns.

---

# Trade-offs

System Design is fundamentally about trade-offs.

For example:

## Caching

Benefits:

```text
Lower Latency
Higher Throughput
Reduced Database Load
```

Costs:

```text
Cache Invalidation
Stale Data
Additional Infrastructure
Memory Cost
```

---

## Microservices

Benefits:

```text
Independent Deployment
Independent Scaling
Team Ownership
Failure Isolation
```

Costs:

```text
Network Complexity
Distributed Debugging
Operational Overhead
Data Consistency Challenges
```

---

## Strong Consistency

Benefits:

```text
More predictable reads
```

Costs:

```text
Potentially higher latency
Lower availability in some architectures
More coordination
```

There is no universally best choice.

The correct choice depends on the requirements.

---

# Engineering Perspective

System Design is fundamentally about **managing complexity deliberately**.

A system often evolves like this:

```text
Simple Application
       ↓
More Users
       ↓
Scaling Problem
       ↓
Horizontal Scaling
       ↓
More Data
       ↓
Caching / Replication
       ↓
Traffic Spikes
       ↓
Queues
       ↓
Global Users
       ↓
CDN / Multi-Region
       ↓
More Failure Modes
       ↓
Resilience / Observability
```

The engineer's job is not to eliminate complexity.

It is to introduce complexity **only when it provides meaningful value**.

---

# Best Practices

## 1. Start With Requirements

Never begin with:

> "Should we use Kafka?"

Begin with:

> "What problem are we solving?"

---

## 2. Quantify Requirements

Prefer:

```text
100,000 requests/second
```

over:

```text
Very high traffic
```

Prefer:

```text
99.99% availability
```

over:

```text
Highly available
```

Numbers make architectural decisions concrete.

---

## 3. Design for Failure

Assume:

- Servers fail.
- Networks fail.
- Databases fail.
- External services timeout.
- Deployments fail.
- Traffic spikes happen.

Reliable systems are designed around failure rather than assuming everything works.

---

## 4. Start Simple

Use:

```text
React
    ↓
API
    ↓
Database
```

when that architecture satisfies the requirements.

Don't introduce:

```text
Kafka
Redis
Kubernetes
Microservices
Multi-Region
Event Sourcing
```

without a reason.

---

## 5. Make Trade-offs Explicit

For every major decision, ask:

```text
What do we gain?

What do we give up?

Why is this acceptable?
```

---

## 6. Measure Before Optimizing

Use:

```text
Implement
    ↓
Measure
    ↓
Find Bottleneck
    ↓
Improve
    ↓
Measure Again
```

Architecture should be evidence-driven whenever possible.

---

# Common Mistakes

## Mistake 1 — Starting With Technology

Bad:

```text
We need Kafka.
```

Better:

```text
We need asynchronous processing
because the workload is bursty and
doesn't need synchronous completion.
```

Then evaluate whether Kafka is appropriate.

---

## Mistake 2 — Jumping Directly to Microservices

Microservices introduce significant operational complexity.

A modular monolith may be a better starting point.

---

## Mistake 3 — Ignoring Requirements

Architecture without requirements is guesswork.

---

## Mistake 4 — Ignoring Failure

A system isn't reliable because everything works.

It is reliable because it behaves predictably when something fails.

---

## Mistake 5 — Over-Engineering

Do not build a globally distributed architecture for a system serving 50 users.

---

## Mistake 6 — Ignoring Cost

Every architecture has:

- Infrastructure cost
- Engineering cost
- Operational cost
- Maintenance cost
- Cognitive cost

---

# Interview Questions

These are intentionally concise.

Dedicated interview preparation will be covered later in the System Design Interview module.

### Beginner

1. What is System Design?

2. Why is System Design important?

3. What is the difference between an application and a system?

4. What are functional requirements?

5. What are non-functional requirements?

### Intermediate

6. How do requirements influence architecture?

7. Why does architecture change as traffic grows?

8. What are common components of a distributed system?

9. What is the difference between System Design and Software Architecture?

10. What are architectural trade-offs?

### Advanced

11. How would you approach designing a system from scratch?

12. How do you decide when to introduce caching?

13. When should a monolith be split into microservices?

14. How do you design for failure?

15. How do you balance scalability, reliability, latency, and cost?

---

# Hands-on Exercise

Choose an application you understand.

For example:

```text
Employee Management System
```

## Step 1 — Requirements

Write:

```text
Users:
Features:
Expected Traffic:
Data:
Availability:
Security:
```

---

## Step 2 — Current Architecture

Draw:

```text
Frontend
    ↓
Backend
    ↓
Database
```

---

## Step 3 — Identify Bottlenecks

Ask:

- What happens with 10× users?
- What happens if the backend fails?
- What happens if the database becomes slow?
- What happens during traffic spikes?
- Where could caching help?
- Which operations could be asynchronous?

---

## Step 4 — Design Version 2

Create a new architecture that addresses the actual bottlenecks.

Do **not** add infrastructure unless you can explain the requirement it satisfies.

---

# Key Takeaways

- System Design defines how components work together to satisfy requirements.
- Requirements should drive architecture.
- Functional requirements describe what the system does.
- Non-functional requirements describe how well it operates.
- Scale changes architectural decisions.
- Failures must be considered during design.
- Every architectural decision involves trade-offs.
- Simple architecture should be the starting point.
- Complexity should be introduced deliberately.
- Measurement should guide optimization.

---

# Summary

System Design is the discipline of designing software systems that satisfy functional requirements while meeting constraints such as scalability, availability, reliability, latency, security, and cost.

A system may begin with a simple:

```text
Client
  ↓
Server
  ↓
Database
```

As requirements grow, additional components may become necessary:

```text
Load Balancers
Caching
Replication
Queues
CDNs
Service Boundaries
Observability
Resilience
```

The goal is not to create the most complicated architecture.

The goal is to create the **simplest architecture that reliably satisfies the requirements** and can evolve as those requirements change.

---

# Further Reading

Within this learning path:

- **SD-FND-002 — Functional vs Non-Functional Requirements**
- **SD-FND-003 — Scalability**
- **SD-FND-004 — Availability**
- **SD-FND-005 — Reliability**
- **SD-FND-006 — Latency and Throughput**
- **SD-FND-007 — Capacity Estimation**
- **SD-FND-008 — Trade-offs**

Later:

- System Architecture
- Distributed Systems
- Caching
- Messaging
- System Design Case Studies
- System Design Interviews

---
## Navigation

| Previous | Module | Next |
|---|---|---|
| — | [System Design Fundamentals](../README.md) | [Functional vs Non-Functional Requirements →](SD-FND-002-functional-vs-non-functional-requirements.md) |

---

## Continue Your Journey

You now have the basic mental model for System Design.

The next question is fundamental:

> **What exactly must the system do, and how well must it do it?**

Continue with:

**[SD-FND-002 — Functional vs Non-Functional Requirements →](SD-FND-002-functional-vs-non-functional-requirements.md)**

---

**Document ID:** `SD-FND-001`  
**Module:** `01-fundamentals / 01-core-concepts`  
**Status:** ✅ Complete