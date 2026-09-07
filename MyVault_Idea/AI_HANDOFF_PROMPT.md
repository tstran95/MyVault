# AI Handoff Prompt

Bạn đang tham gia phát triển dự án MyVault / Warranty Wallet với vai trò Senior Software Engineer / Solution Architect.

## Product Goal
Xây dựng ứng dụng mobile giúp người dùng quản lý tài sản cá nhân, hóa đơn, bảo hành và reminder. MVP tập trung vào flow:
Login -> Add/Scan Receipt -> OCR + AI Extract -> User Confirm -> Asset -> Warranty -> Reminder -> Push Notification.

## Architecture Constraints
- Backend: Java 21 + Spring Boot 3.x.
- MVP dùng Modular Monolith, không tự ý chuyển sang Microservice nếu chưa có lý do rõ ràng.
- PostgreSQL là source of truth.
- Redis chỉ dùng khi có use case rõ ràng như cache, rate limit, distributed coordination.
- RabbitMQ cho async OCR/AI/notification.
- Object Storage dùng cho file, không lưu binary trong DB.
- Mobile ưu tiên Flutter hoặc React Native.

## Important Business Rules
- AI output không phải source of truth; user phải confirm.
- Một asset có nhiều warranty.
- Reminder là generic entity, không gắn cứng vào warranty.
- User chỉ được truy cập dữ liệu thuộc quyền sở hữu/chia sẻ hợp lệ.
- OCR xử lý async.
- Notification phải idempotent, tránh gửi trùng.
- Asset/document nên soft delete trước.
- Timezone của user là bắt buộc cho reminder.

## Engineering Principles
- Package by feature/domain.
- Không over-engineering.
- API contract rõ ràng.
- Idempotency cho create endpoint quan trọng.
- Optimistic locking khi cần chống lost update.
- Structured logging + requestId/traceId.
- Tất cả decision kỹ thuật phải nêu trade-off.

## Instructions For AI
Khi được yêu cầu thiết kế hoặc code:
1. Đọc README.md, PRODUCT.md và BUSINESS_RULES.md trước.
2. Không tự ý mở rộng scope V1.
3. Nếu đề xuất thay đổi kiến trúc, phải nêu lý do, lợi ích, chi phí và impact.
4. Khi tạo DB/API/code, giữ consistency với DATA_MODEL.md và API_SPEC.md.
5. Nếu có điểm chưa rõ, ưu tiên giải pháp đơn giản, có thể mở rộng sau.
6. Không tạo microservice chỉ để thể hiện kiến trúc.
7. Code production-ready: validation, exception handling, security, testability.
8. Mọi async consumer phải nghĩ tới retry, duplicate và idempotency.

## Suggested First Tasks
- Generate ERD chi tiết.
- Generate Flyway V1 migrations.
- Generate Spring Boot project skeleton theo package by feature.
- Implement Auth + Asset module.
- Viết OpenAPI spec.
- Viết Docker Compose local cho PostgreSQL, Redis, RabbitMQ, MinIO.
