# API Spec Draft

Base URL: /api/v1

## Auth
POST /auth/google
POST /auth/apple
POST /auth/refresh

## Asset
POST /assets
GET /assets
GET /assets/{id}
PUT /assets/{id}
DELETE /assets/{id}   # logical archive
GET /assets?keyword=&category=&status=

## Warranty
POST /assets/{assetId}/warranties
GET /assets/{assetId}/warranties
GET /warranties/{id}
PUT /warranties/{id}
DELETE /warranties/{id}

## Document
POST /documents/upload-url
POST /documents/confirm
GET /assets/{assetId}/documents
GET /documents/{id}
DELETE /documents/{id}

## OCR
POST /documents/{documentId}/ocr
GET /ocr-jobs/{id}
POST /ocr-jobs/{id}/confirm

## Reminder
GET /reminders
POST /reminders
PUT /reminders/{id}
DELETE /reminders/{id}

## Device / Notification
POST /devices/register
DELETE /devices/{id}
GET /notifications

## Standard Error
{
  "code": "ASSET_NOT_FOUND",
  "message": "Asset not found",
  "requestId": "..."
}

## API Design Notes
- API tạo resource quan trọng nên hỗ trợ Idempotency-Key.
- Mọi resource user-owned phải authorize theo current user.
- Pagination dùng cursor hoặc page/size nhất quán.
- OCR trả 202 Accepted nếu xử lý async.
