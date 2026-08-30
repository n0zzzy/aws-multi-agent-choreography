# AWS Multi-Agent Choreography Pattern

Serverless event-driven architecture using Amazon EventBridge and multi-agent AWS Lambda functions (Planner, Weather, Flight Manager) for automated travel booking workflows.

## Architecture Pattern
- Choreography: Fully decoupled agents communicating via EventBridge custom events.
- State & Storage: Distributed state validation via Amazon S3 bucket tracking.
- Human-in-the-Loop: Asynchronous approval ingestion via workshop.human-review.

## Test Command
aws events put-events --entries "[{\"Source\": \"workshop.human-review\", \"DetailType\": \"HumanApprovalDecision\", \"Detail\": \"{\\\"bookingId\\\": \\\"high-risk-test-456\\\", \\\"decision\\\": \\\"APPROVED\\\", \\\"reviewer\\\": \\\"workshop-admin\\\"}\"}]"
