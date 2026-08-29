Summary
Over the course of this workshop, you’ve explored how to build multi-agent systems on AWS using two different coordination patterns — choreography with EventBridge and orchestration with Step Functions. You also learned how to layer in observability using CloudWatch Logs, X-Ray, and tracing features built into AWS services. This summary brings it all together.

What You Built
Agents on Lambda — Planner, Weather, and Flight Booking agents, each with their own personality and tools.
Choreography with EventBridge — loosely coupled agents reacting to events (DatesFinalized, FlightSearchCompleted, etc.). Scales easily by adding new rules and targets.
Orchestration with Step Functions — a centralized state machine controlling sequence, branching, retries, and HITL paths. Provides built-in correlation and visualization.
Human-in-the-Loop (HITL) — escalation path via SQS where bookings can be paused for manual approval before proceeding.
Observability — logs correlated by booking ID, tracing enabled across EventBridge, Step Functions, and Lambdas, and distributed visualization in X-Ray.
Key Learnings
Serverless agents scale naturally: running on AWS Lambda removes infrastructure overhead and provides cost efficiency (pay only for execution time).
Choreography = flexibility: EventBridge fan-out makes it easy to extend systems by adding new agents without touching existing code.
Orchestration = control: Step Functions provide strict sequencing, error handling, and auditability, which is essential for workflows requiring guarantees.
HITL is essential for trust: not all decisions should be automated; routing to SQS for manual review makes systems more reliable and compliant.
Observability is non-negotiable: CloudWatch, Logs Insights, and X-Ray give you the visibility to debug, trace, and optimize distributed systems at scale.
When to Use Which Pattern
Choreography is best when:

You expect to add or remove agents frequently.
Agents can run independently with minimal coupling.
Event-driven scalability is the priority.
Orchestration is best when:

Order of execution matters.
You need retries, error handling, or compensation logic.
Compliance requires full audit trails.
In real systems, you may combine both patterns — using EventBridge for broad distribution and Step Functions for critical orchestrated workflows.