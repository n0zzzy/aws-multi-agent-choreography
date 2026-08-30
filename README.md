# AWS Multi-Agent Choreography Pattern

An enterprise-grade, event-driven multi-agent workshop implementation using **Amazon EventBridge** and **Serverless Architecture**. This project demonstrates decentralized choreography where autonomous agents coordinate by publishing and subscribing to events on a shared event bus.

## Architecture Overview
- **Event Coordination Layer**: Amazon EventBridge (`multi-agent-bus`) handling event-driven routing.
- **Microservices / Agents**:
  - **Planner Agent**: Coordinates general travel itineraries and triggers downstream bookings.
  - **Weather Agent**: Listens to travel requests and retrieves meteorological insights.
  - **Flight Manager Agent**: Handles flight availability and booking logistics.
- **Compute & State**: AWS Lambda functions backed by Amazon S3 session management.

## Repository Structure
- `eventbridge-rules.json`: Event routing configuration rules for agent subscriptions.
- `events-human-review-approved.json`: Test payloads for event-driven review workflows.
- `README.md`: Project documentation.

## Core Event Flow
1. **TravelRequestSubmitted**: Triggered to initiate a distributed multi-agent itinerary workflow.
2. **FinalBookingCompleted**: Emitted upon successful processing by the planner, allowing decoupled extension agents to subscribe cleanly.
