# Architecture

## Strategy
Bắt đầu bằng Modular Monolith, không dùng Microservice cho MVP.

## Logical Modules
- auth
- user
- asset
- warranty
- document
- ocr
- reminder
- notification

## Suggested Package Structure
com.myvault
  auth/
  user/
  asset/
  warranty/
  document/
  ocr/
  reminder/
  notification/
  shared/

## Main Architecture
Mobile App
  -> HTTPS REST API
  -> Spring Boot Modular Monolith
      -> PostgreSQL
      -> Redis
      -> RabbitMQ
      -> S3 Compatible Object Storage
      -> FCM/APNs

Async workers:
- OCR Worker
- AI Parsing Worker
- Notification Worker

## Upload Design
1. Mobile requests presigned upload URL.
2. Backend validates intent and returns presigned URL.
3. Mobile uploads directly to object storage.
4. Mobile confirms upload.
5. Backend creates document metadata + OCR job.
6. Async event is published.

## OCR Design
DocumentUploadedEvent
 -> RabbitMQ
 -> OCR Worker
 -> OCR text
 -> AI structured extraction
 -> OCR job SUCCESS
 -> Mobile polls or receives completion notification
 -> User confirms

## Reminder Design
Scheduler query:
SELECT ... FROM reminders
WHERE status='PENDING'
AND trigger_at <= now()
LIMIT N

Then atomically claim reminder before publishing ReminderTriggeredEvent.

## Reliability
- Outbox pattern có thể thêm khi hệ thống cần đảm bảo DB commit + event publish không mất sự kiện.
- Idempotent consumer.
- Retry + DLQ cho OCR/notification.
- Optimistic locking cho entity cần tránh lost update.

## Observability
- requestId / traceId
- structured logging
- Prometheus metrics
- Grafana dashboard
- Loki/ELK logging

## Security
- JWT/refresh token hoặc OAuth2 social login
- Object storage private
- Presigned URL expiry ngắn
- Rate limit upload/OCR/login
- Input validation
- Sensitive log masking
