# AWS Lambda Reference

## Handler (Python)
```python
import json

def handler(event, context):
    body = json.loads(event.get("body", "{}"))
    return {
        "statusCode": 200,
        "headers": {"Content-Type": "application/json"},
        "body": json.dumps({"message": "Todo created", "data": body})
    }
```

## API Gateway Integration
```yaml
# SAM Template
Resources:
  TodoFunction:
    Type: AWS::Serverless::Function
    Properties:
      Handler: src/handler.handler
      Runtime: python3.12
      Events:
        CreateTodo:
          Type: Api
          Properties:
            Path: /todos
            Method: post
```

## When to Use
- Event-driven, short-lived tasks (< 15 min).
- Webhooks, image processing, scheduled jobs.
- Low/unpredictable traffic (pay per invocation).
