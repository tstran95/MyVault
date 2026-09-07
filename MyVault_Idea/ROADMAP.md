# Development Roadmap

## Phase 0 - Discovery
- Product vision
- Persona
- User journey
- Business rules
- Wireframe
- ERD
- API contract

## Phase 1 - Foundation
- Spring Boot project
- PostgreSQL
- Flyway
- Security/Auth
- Global exception
- Logging
- Docker Compose
- CI pipeline

## Phase 2 - Asset
- Asset CRUD
- Category
- Search
- Archive
- Validation

## Phase 3 - Warranty
- Warranty CRUD
- Multiple warranties per asset
- Expiry calculation
- Warranty timeline

## Phase 4 - Document
- Presigned upload
- Object storage
- Metadata
- Document preview/download authorization

## Phase 5 - OCR + AI
- OCR job
- Queue
- OCR provider integration
- AI structured extraction
- Review/confirm screen

## Phase 6 - Reminder + Notification
- Reminder rules
- Scheduler
- Claim/lock strategy
- RabbitMQ event
- FCM/APNs
- Notification history
- Duplicate prevention

## Phase 7 - Production Readiness
- Metrics
- Backup
- Rate limit
- Security hardening
- Privacy Policy
- Terms
- Delete Account
- Store release

## Definition of MVP Done
User có thể:
Login -> Scan receipt -> OCR/AI detect -> Confirm -> Create asset -> Add warranty -> Receive expiry reminder.
