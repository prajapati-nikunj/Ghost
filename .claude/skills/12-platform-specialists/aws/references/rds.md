# AWS RDS Reference

## PostgreSQL on RDS
```hcl
# Terraform
resource "aws_db_instance" "todo_db" {
  identifier           = "todo-db"
  engine               = "postgres"
  engine_version       = "16.1"
  instance_class       = "db.t3.micro"
  allocated_storage    = 20
  db_name              = "tododb"
  username             = "postgres"
  password             = var.db_password
  skip_final_snapshot  = false
  multi_az             = true
  storage_encrypted    = true
  publicly_accessible  = false
  vpc_security_group_ids = [aws_security_group.db.id]
}
```

## Best Practices
- Enable Multi-AZ for production.
- Enable automated backups (7-day retention minimum).
- Use Parameter Groups for tuning.
- Never make publicly accessible; use VPC + security groups.
- Monitor with CloudWatch (CPU, connections, storage).
