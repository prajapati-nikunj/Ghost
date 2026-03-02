# Non-Functional Requirements (NFR) Checklist

## Performance
- [ ] API response time < 200ms (P95)
- [ ] Page load time < 3s (LCP)
- [ ] Database queries < 50ms

## Scalability
- [ ] Horizontal scaling strategy defined
- [ ] Stateless services (no server-side sessions)
- [ ] Database connection pooling configured

## Availability
- [ ] SLA target defined (e.g., 99.9%)
- [ ] Health check endpoints implemented
- [ ] Graceful shutdown handling

## Security
- [ ] All OWASP Top 10 addressed
- [ ] Data encrypted at rest and in transit
- [ ] Rate limiting implemented

## Observability
- [ ] Structured logging (JSON)
- [ ] Distributed tracing (OpenTelemetry)
- [ ] Alerting thresholds defined

## Maintainability
- [ ] Code coverage > 80%
- [ ] Documentation up to date
- [ ] ADRs for all major decisions
