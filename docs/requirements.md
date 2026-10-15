# PulseForge AI — Requirements

## 1. Objective

Build a platform that receives application events, identifies abnormal behavior, groups related events into incidents, and assists engineers in investigating incidents using evidence-grounded AI.

## 2. Primary Users

- **Software engineer:** Investigates failures affecting an application.
- **Platform engineer:** Monitors service health and event-processing behavior.
- **Incident responder:** Reviews incident evidence, records findings, and tracks resolution.

## 3. Functional Requirements

### FR-01: Event Ingestion

The backend must expose an HTTP API that accepts application events in JSON format.

### FR-02: Event Validation

The backend must validate required fields and reject malformed events with appropriate HTTP responses.

### FR-03: Event Persistence

Accepted events must be stored in PostgreSQL.

### FR-04: Event Retrieval

Users and authorized API clients must eventually be able to retrieve events using filters such as service, severity, and time range.

### FR-05: Anomaly Detection

The platform must identify abnormal event patterns using configurable rules and statistical techniques.

### FR-06: Incident Creation

The platform must create incidents when configured anomaly conditions are met.

### FR-07: Event Correlation

Related events should be associated using available information such as timestamps, service names, trace IDs, and deployment records.

### FR-08: AI-Assisted Investigation

The platform should generate investigation summaries and possible causes using relevant stored evidence.

### FR-09: Evidence Grounding

AI-generated findings must distinguish observed facts from hypotheses and reference actual retrieved evidence. The system must not fabricate event identifiers or evidence.

### FR-10: Dashboard

The frontend should display incident summaries, severity, timelines, supporting evidence, and investigation results.

### FR-11: Reliability

Important processing steps must be tested for failures, retries, duplicate events, and recovery behavior.

## 4. Non-Functional Requirements

- Maintainable code and clear module boundaries.
- Automated unit and integration tests.
- Secure handling of configuration and credentials.
- Structured application logging.
- Documented local setup and reproducible execution.
- Measured performance under explicitly documented test conditions.
- Graceful handling of unavailable external AI services.

## 5. Initial Scope

The first release will focus on:

1. A Spring Boot REST API.
2. PostgreSQL persistence.
3. Event validation.
4. Event retrieval.
5. A simulator for generating test events.

Kafka, Redis, AI investigation, authentication, and the dashboard will be introduced incrementally.

## 6. Out of Scope Initially

- Training a custom large language model.
- Automatically executing production remediation actions.
- Claiming guaranteed root-cause identification.
- Deploying a production-grade multi-region system.

## 7. Success Criteria for the First Milestone

- The backend starts successfully.
- PostgreSQL runs through Docker Compose.
- A valid event can be submitted through the API.
- The event is persisted and can be retrieved.
- Invalid input is rejected appropriately.
- Automated tests cover the core event workflow.