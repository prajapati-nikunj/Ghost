# Monitoring & Observability

## Three Pillars
1. **Logs**: Structured JSON logging (what happened).
2. **Metrics**: Numeric measurements over time (how much).
3. **Traces**: Request flow across services (where it went).

## Structured Logging (Python)
```python
import structlog

logger = structlog.get_logger()

logger.info("todo_created", todo_id=todo.id, user_id=user.id, title=todo.title)
logger.error("todo_creation_failed", error=str(e), user_id=user.id)
```

## Prometheus Metrics
```python
from prometheus_client import Counter, Histogram

REQUEST_COUNT = Counter("http_requests_total", "Total requests", ["method", "endpoint", "status"])
REQUEST_LATENCY = Histogram("http_request_duration_seconds", "Request latency", ["endpoint"])
```

## Health Check Endpoints
```python
@app.get("/health")
async def health():
    return {"status": "healthy", "timestamp": datetime.utcnow().isoformat()}

@app.get("/ready")
async def readiness(db: AsyncSession = Depends(get_db)):
    try:
        await db.execute(text("SELECT 1"))
        return {"status": "ready"}
    except Exception:
        raise HTTPException(status_code=503, detail="Database not ready")
```

## Alerting Rules
| Metric | Threshold | Action |
|---|---|---|
| Error rate | > 5% for 5min | Page on-call |
| P95 latency | > 500ms for 10min | Warn team |
| CPU usage | > 80% for 15min | Auto-scale |
| Disk usage | > 85% | Alert + cleanup |
