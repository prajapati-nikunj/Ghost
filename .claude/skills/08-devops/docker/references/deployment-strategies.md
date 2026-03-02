# Deployment Strategies

## Blue-Green
- Two identical environments (Blue = current, Green = new).
- Switch traffic from Blue → Green after validation.
- Instant rollback by switching back.
- **Use when**: Zero-downtime required, database compatible.

## Canary
- Route small % of traffic to new version (e.g., 5%).
- Gradually increase if metrics are healthy.
- **Use when**: High-traffic apps needing risk mitigation.

## Rolling Update (K8s default)
- Replace pods one at a time.
- `maxSurge: 1`, `maxUnavailable: 0` for safest rollout.
- **Use when**: Standard deployments with readiness probes.

## Feature Flags
- Deploy code but hide features behind flags (LaunchDarkly, Unleash).
- Decouple deployment from release.
- **Use when**: Gradual rollout to specific users/regions.

## Rollback Procedure
1. Identify failing deployment via monitoring/alerts.
2. `kubectl rollout undo deployment/todo-api` (K8s).
3. Verify health checks pass on previous version.
4. Investigate root cause via logs and traces.
