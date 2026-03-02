# Kubernetes Reference

## Deployment
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: todo-api
spec:
  replicas: 3
  selector:
    matchLabels: { app: todo-api }
  template:
    metadata:
      labels: { app: todo-api }
    spec:
      containers:
        - name: todo-api
          image: ghcr.io/org/todo-api:1.0.0
          ports: [{ containerPort: 8000 }]
          resources:
            requests: { cpu: "100m", memory: "128Mi" }
            limits: { cpu: "500m", memory: "512Mi" }
          livenessProbe:
            httpGet: { path: /health, port: 8000 }
            initialDelaySeconds: 10
          readinessProbe:
            httpGet: { path: /ready, port: 8000 }
          env:
            - name: DATABASE_URL
              valueFrom:
                secretKeyRef: { name: todo-secrets, key: database-url }
```

## Service
```yaml
apiVersion: v1
kind: Service
metadata:
  name: todo-api
spec:
  selector: { app: todo-api }
  ports: [{ port: 80, targetPort: 8000 }]
  type: ClusterIP
```

## Ingress
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: todo-ingress
  annotations:
    cert-manager.io/cluster-issuer: letsencrypt-prod
spec:
  rules:
    - host: api.todo.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service: { name: todo-api, port: { number: 80 } }
```
