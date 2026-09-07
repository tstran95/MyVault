# MyVault / Warranty Wallet

## Mục tiêu
Xây dựng một ứng dụng quản lý tài sản cá nhân, hóa đơn, bảo hành và các mốc cần nhắc. MVP tập trung vào việc giúp người dùng không bị mất thông tin bảo hành/hóa đơn và được nhắc trước khi hết hạn.

## Product Vision
Một app quản lý "những thứ bạn sở hữu và những thứ bạn không được phép quên".

## MVP
1. Đăng nhập.
2. Thêm tài sản thủ công.
3. Chụp/upload hóa đơn.
4. OCR + AI trích xuất thông tin sản phẩm.
5. User xác nhận dữ liệu AI.
6. Quản lý nhiều loại bảo hành trên một tài sản.
7. Tạo reminder trước ngày hết hạn.
8. Push notification.

## Hướng mở rộng
V1: Warranty Wallet
V2: Personal Asset Manager
V3: Expiry Reminder
V4: Family Vault / Digital Household Management

## Tech Stack đề xuất
- Backend: Java 21, Spring Boot 3.x
- Architecture: Modular Monolith
- Database: PostgreSQL
- Cache/Lock: Redis
- Async: RabbitMQ
- Object Storage: S3 compatible
- Mobile: Flutter hoặc React Native
- Notification: Firebase Cloud Messaging / APNs
- Migration: Flyway
- Testing: JUnit, Testcontainers

## Thứ tự đọc cho AI/model khác
1. README.md
2. PRODUCT.md
3. BUSINESS_RULES.md
4. USER_FLOWS.md
5. DATA_MODEL.md
6. API_SPEC.md
7. ARCHITECTURE.md
8. ROADMAP.md
9. AI_HANDOFF_PROMPT.md
