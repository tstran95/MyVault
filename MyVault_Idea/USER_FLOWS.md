# User Flows

## Flow 1 - Add Asset Manually
Login -> Home -> Add Asset -> Enter Product Info -> Add Warranty -> Save -> Asset Detail

## Flow 2 - Scan Receipt
Login -> Add Asset -> Scan/Upload Receipt -> Receive upload URL -> Upload Object Storage -> Confirm Upload -> OCR Job -> AI Extraction -> Review Screen -> User Confirm -> Create Asset -> Add Warranty -> Save

## Flow 3 - Warranty Reminder
Warranty Created -> Reminder Rules Generated -> Scheduler Finds Due Reminder -> Claim Reminder -> Publish Event -> Notification Worker -> FCM/APNs -> Mark Notification SENT

## Flow 4 - View Warranty
Asset List -> Asset Detail -> Warranty Timeline -> View provider/start/end/days left -> Open invoice/warranty document

## Flow 5 - Archive Asset
Asset Detail -> Archive -> Confirm -> status=ARCHIVED -> Hide from default active list

## Key UX Principle
AI phải giúp giảm thao tác nhập liệu, nhưng không được tự động ghi dữ liệu final mà không cho user kiểm tra.
