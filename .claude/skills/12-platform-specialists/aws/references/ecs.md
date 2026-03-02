# AWS ECS Reference

## Task Definition
```json
{
  "family": "todo-api",
  "containerDefinitions": [{
    "name": "todo-api",
    "image": "123456789.dkr.ecr.us-east-1.amazonaws.com/todo-api:1.0.0",
    "portMappings": [{ "containerPort": 8000, "protocol": "tcp" }],
    "environment": [{ "name": "NODE_ENV", "value": "production" }],
    "secrets": [{ "name": "DATABASE_URL", "valueFrom": "arn:aws:ssm:..." }],
    "healthCheck": { "command": ["CMD-SHELL", "curl -f http://localhost:8000/health || exit 1"] },
    "logConfiguration": {
      "logDriver": "awslogs",
      "options": { "awslogs-group": "/ecs/todo-api", "awslogs-region": "us-east-1" }
    }
  }],
  "cpu": "256", "memory": "512"
}
```

## When to Use
- Container workloads without Kubernetes complexity.
- AWS-native deployments with Fargate (serverless containers).
