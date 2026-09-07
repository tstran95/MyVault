# Business Rules

## Asset
- BR-001: PurchaseDate không được lớn hơn ngày hiện tại.
- BR-002: Asset không xóa vật lý ngay; dùng trạng thái ARCHIVED hoặc lifecycle status.
- BR-003: Một user có nhiều asset.
- BR-004: Một asset có thể có nhiều warranty.
- BR-005: Một asset có thể có nhiều document.
- BR-006: Asset lifecycle có thể gồm ACTIVE, SOLD, LOST, BROKEN, DISPOSED, ARCHIVED.

## Warranty
- BR-010: WarrantyEndDate >= WarrantyStartDate.
- BR-011: Một asset có thể đồng thời có Manufacturer Warranty, Store Warranty, Extended Warranty, Insurance.
- BR-012: Không cần lưu warranty status nếu có thể tính từ endDate.
- BR-013: EXPIRING_SOON có thể tính theo configurable threshold, mặc định 30 ngày.

## Document
- BR-020: Document có thể tồn tại trước khi gắn với asset vì OCR có thể chạy trước khi asset được tạo.
- BR-021: Binary file không lưu trực tiếp trong PostgreSQL.
- BR-022: Object Storage là private; client truy cập qua presigned URL.
- BR-023: Xóa document nên soft delete trước; physical delete theo retention policy.

## OCR / AI
- BR-030: OCR/AI chạy bất đồng bộ.
- BR-031: AI output không phải source of truth.
- BR-032: User phải confirm trước khi dữ liệu AI trở thành dữ liệu chính thức.
- BR-033: OCR job states: UPLOADED, QUEUED, PROCESSING, SUCCESS, FAILED.
- BR-034: OCR retry phải có retryCount và giới hạn retry.

## Reminder
- BR-040: Reminder là generic entity, không gắn cứng vào Warranty.
- BR-041: Reminder có entityType + entityId.
- BR-042: Mặc định có thể nhắc trước 90, 30, 7, 1 ngày nhưng user được cấu hình.
- BR-043: Reminder worker phải đảm bảo không gửi notification duplicate.
- BR-044: Timezone của user phải được lưu và được dùng khi tính thời điểm gửi.

## Authorization
- BR-050: User chỉ được đọc/sửa/xóa dữ liệu thuộc quyền sở hữu hoặc được chia sẻ hợp lệ.
- BR-051: Không dùng repository.findById(id) cho entity user-owned mà phải kiểm tra userId/permission trong query hoặc service authorization.

## Security
- BR-060: Không log JWT, full IMEI, document private URL hoặc dữ liệu nhạy cảm.
- BR-061: Toàn bộ API production dùng HTTPS.
- BR-062: Upload phải kiểm tra mime type, size, malware policy nếu triển khai production.
