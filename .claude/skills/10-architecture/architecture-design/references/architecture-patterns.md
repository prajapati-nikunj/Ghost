# Architecture Patterns Reference

## Monolith vs Microservices

| Factor | Monolith | Microservices |
|---|---|---|
| Team Size | < 10 | > 10 |
| Deploy Frequency | Weekly | Daily/Per-service |
| Data Coupling | Tight | Loose |
| Complexity | Low at start | High at start |

## Clean Architecture Layers
```
┌─────────────────────────────────┐
│  Infrastructure (Frameworks)    │
│  ┌───────────────────────────┐  │
│  │  Interface (Adapters)     │  │
│  │  ┌─────────────────────┐  │  │
│  │  │  Use Cases (App)    │  │  │
│  │  │  ┌───────────────┐  │  │  │
│  │  │  │  Core (Domain) │  │  │  │
│  │  │  └───────────────┘  │  │  │
│  │  └─────────────────────┘  │  │
│  └───────────────────────────┘  │
└─────────────────────────────────┘
```

## Event-Driven Architecture
Use when: asynchronous workflows, decoupled services, real-time notifications.
- **Event Bus**: RabbitMQ, Kafka, Redis Pub/Sub.
- **Pattern**: Command → Handler → Event → Subscriber.

## CQRS
Separate read and write models when read/write patterns diverge significantly.
