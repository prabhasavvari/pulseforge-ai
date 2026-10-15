# PulseForge AI — Initial Architecture

## 1. Development Architecture

Initially, the Spring Boot application will run directly on the Ubuntu VM. PostgreSQL will run as a Docker Compose service.

```text
Event Simulator
      |
      | HTTP POST /api/v1/events
      v
Spring Boot Application
      |
      | JDBC
      v
PostgreSQL Container
      |
      v
Persistent Docker Volume
```

## 2. Components

### Event Simulator

Generates realistic application events for local testing. It represents an instrumented application or event producer.

### Spring Boot Application

Initially implemented as a modular backend. It validates incoming events, persists them, and exposes retrieval APIs.

### PostgreSQL

Stores accepted events and, in later milestones, incidents, deployments, and investigation evidence.

### Docker Compose

Defines the local infrastructure services and their configuration.

## 3. Event Lifecycle

1. The simulator generates an event.
2. It sends the event to the ingestion endpoint.
3. The backend validates the request.
4. The backend persists the accepted event.
5. The API returns an appropriate response.
6. The event can be retrieved for verification.

## 4. Planned Evolution

The architecture will evolve to include:

- Kafka for asynchronous event processing.
- Anomaly detection and incident correlation.
- Redis for selected caching and rate-limiting use cases.
- An AI investigation module with retrieval-augmented generation.
- A React dashboard.
- Automated CI/CD and observability.

These components will be added only when the preceding milestone is working.

## 5. Development Networking

Because the Spring Boot application initially runs on the VM, it will connect to PostgreSQL through a published host port, using `localhost` and the configured PostgreSQL port.

If the backend later runs inside Docker Compose, it will connect to PostgreSQL using the Compose service name on the shared container network.

## 6. Reliability Considerations

- Database transactions must be handled explicitly.
- Duplicate-event behavior will be designed and tested.
- Retries must not silently create duplicate incidents.
- AI findings must be grounded in retrieved evidence.
- Secrets must not be committed to source control.