# Summary

Over the course of this workshop, you’ve explored how to build **multi-agent systems on AWS** using two different coordination patterns — **choreography with EventBridge** and **orchestration with Step Functions**. You also learned how to layer in observability using **CloudWatch Logs**, **X-Ray**, and tracing features built into AWS services. This summary brings it all together.

## What You Built

* **Agents on Lambda**
  * Planner, Weather, and Flight Booking agents.
  * Each features its own personality and tools.
* **Choreography with EventBridge**
  * Loosely coupled agents reacting to events (`DatesFinalized`, `FlightSearchCompleted`, etc.).
  * Scales easily by adding new rules and targets.
* **Orchestration with Step Functions**
  * A centralized state machine controlling sequence, branching, retries, and HITL paths.
  * Provides built-in correlation and visualization.
* **Human-in-the-Loop (HITL)**
  * Escalation path via SQS.
  * Bookings can be paused for manual approval before proceeding.
* **Observability**
  * Logs correlated by booking ID.
  * Tracing enabled across EventBridge, Step Functions, and Lambdas.
  * Distributed visualization in X-Ray.

## Key Learnings

* **Serverless agents scale naturally**
  * Running on AWS Lambda removes infrastructure overhead.
  * Provides cost efficiency by paying only for execution time.
* **Choreography equals flexibility**
  * EventBridge fan-out makes it easy to extend systems.
  * Add new agents without touching existing code.
* **Orchestration equals control**
  * Step Functions provide strict sequencing, error handling, and auditability.
  * Essential for workflows requiring strict guarantees.
* **HITL is essential for trust**
  * Not all decisions should be automated.
  * Routing to SQS for manual review makes systems more reliable and compliant.
* **Observability is non-negotiable**
  * CloudWatch, Logs Insights, and X-Ray give you visibility.
  * Necessary to debug, trace, and optimize distributed systems at scale.

## When to Use Which Pattern

### Choreography is best when:
* You expect to add or remove agents frequently.
* Agents can run independently with minimal coupling.
* Event-driven scalability is the priority.

### Orchestration is best when:
* Order of execution matters.
* You need retries, error handling, or compensation logic.
* Compliance requires full audit trails.

> **Pro Tip:** In real systems, you may combine both patterns — using EventBridge for broad distribution and Step Functions for critical orchestrated workflows.
