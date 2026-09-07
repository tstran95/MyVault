# Task Split For Multiple AI Models

## Model A - Product / BA
- Review product scope.
- Hoàn thiện persona.
- Viết user story + acceptance criteria.
- Viết edge cases.
- Không thay đổi architecture.

## Model B - Solution Architect
- Review modular monolith.
- Hoàn thiện module boundaries.
- Sequence diagrams.
- Security architecture.
- Reliability design.

## Model C - Database
- ERD chi tiết.
- PostgreSQL DDL.
- Flyway migration.
- Index strategy.
- Data retention.

## Model D - Backend Java
- Spring Boot skeleton.
- Auth.
- Asset.
- Warranty.
- Document.
- Reminder.
- Tests.

## Model E - Async / Integration
- RabbitMQ topology.
- OCR worker.
- Retry/DLQ.
- Idempotent consumer.
- Notification worker.

## Model F - Mobile
- Flutter/React Native structure.
- Login.
- Asset list/detail.
- Scan receipt.
- OCR review.
- Warranty UI.
- Push notification.

## Model G - DevOps
- Docker Compose local.
- CI/CD.
- Environments.
- Secrets.
- Monitoring.
- Backup.

## Coordination Rule
Tất cả model phải dùng AI_HANDOFF_PROMPT.md làm shared context và không tự ý thay đổi core business rule nếu chưa cập nhật tài liệu trung tâm.
