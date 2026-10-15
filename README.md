# PulseForge AI

**An AI-powered incident investigation platform that turns application events into evidence-grounded incident insights.**

PulseForge AI is a portfolio project designed to explore backend engineering, distributed event processing, anomaly detection, and AI-assisted incident investigation.

## Problem Statement

When production systems fail, engineers often need to investigate logs, identify related errors, examine recent deployments, and determine possible root causes. This process can be time-consuming, especially when evidence is spread across multiple services.

PulseForge AI aims to help engineers investigate incidents by correlating application events, detecting unusual behavior, and generating AI-assisted investigation reports grounded in stored evidence.

## Planned Features

- Application event ingestion through REST APIs
- Event storage and searchable incident timelines
- Rule-based and statistical anomaly detection
- Incident creation and event correlation
- Asynchronous processing using Apache Kafka
- AI-assisted investigation using retrieval-augmented generation (RAG)
- Evidence references for investigation findings
- Interactive incident dashboard
- Automated tests, observability, and performance evaluation

## Technology Stack

| Area | Technology |
|---|---|
| Backend | Java 21, Spring Boot |
| Build | Maven |
| Database | PostgreSQL |
| Infrastructure | Docker, Docker Compose |
| Messaging | Apache Kafka |
| Caching | Redis |
| AI integration | Spring AI and an external LLM API |
| Frontend | React, TypeScript |
| Testing | JUnit, Mockito, Testcontainers |
| CI/CD | GitHub Actions |
| Observability | OpenTelemetry, Prometheus, Grafana |

The stack will be introduced incrementally as the project develops.

## Initial Architecture

The first milestone is a Spring Boot application that accepts application events through a REST API and persists them in PostgreSQL.

A lightweight event simulator will generate sample events for development and testing.

Kafka, anomaly detection, the dashboard, and AI investigation capabilities will be added in later milestones.

## Development Principles

- Build working features incrementally.
- Validate input and handle failures explicitly.
- Write automated tests for important behavior.
- Keep credentials and secrets out of source control.
- Document architectural decisions and trade-offs.
- Measure performance rather than making unsupported claims.
- Ensure AI-generated findings are supported by available evidence.

## Project Status

**Phase 1 — Repository and backend foundation**

- [x] Create the GitHub repository
- [x] Configure the development environment
- [ ] Document initial requirements and architecture
- [ ] Create the Spring Boot application
- [ ] Run PostgreSQL using Docker Compose
- [ ] Implement the event ingestion API

## License

See the [LICENSE](LICENSE) file for details.