# Data Model / ERD Draft

## Main Relations
USER 1:N ASSET
ASSET 1:N WARRANTY
ASSET 1:N DOCUMENT
DOCUMENT 1:0..1 OCR_JOB
USER 1:N REMINDER
REMINDER 1:N NOTIFICATION
USER 1:N DEVICE

## users
- id
- email
- display_name
- timezone
- language
- provider
- provider_user_id
- created_at
- updated_at

## asset_category
- id
- code
- name
- icon
- active

## assets
- id
- user_id
- category_id
- name
- brand
- model
- serial_number
- imei
- purchase_date
- purchase_price
- currency
- seller
- status
- version
- created_at
- updated_at

Indexes:
- user_id
- user_id, status
- category_id

## warranties
- id
- asset_id
- type
- provider
- start_date
- end_date
- policy_number
- notes
- version
- created_at
- updated_at

Indexes:
- asset_id
- end_date

## documents
- id
- user_id
- asset_id nullable
- document_type
- object_key
- file_name
- content_type
- file_size
- status
- created_at
- updated_at

Indexes:
- user_id
- asset_id

## ocr_jobs
- id
- document_id
- status
- raw_text
- result_json
- provider
- error_code
- error_message
- retry_count
- created_at
- processed_at

Indexes:
- document_id unique
- status, created_at

## reminders
- id
- user_id
- entity_type
- entity_id
- reminder_type
- trigger_at
- status
- created_at
- updated_at

Critical index:
- status, trigger_at

## notifications
- id
- reminder_id
- user_id
- channel
- status
- provider_message_id
- error_code
- error_message
- created_at
- sent_at

## devices
- id
- user_id
- platform
- push_token
- active
- last_seen_at
- created_at
