# Consumer–Provider Handshake

## Thông tin chung

- Lab: FIT4110 Lab 03
- Ngày: 2026-05-13
- Provider team: IoT Ingestion Service Team
- Consumer team: Core Business / Analytics Team
- Provider service: IoT Ingestion API
- Consumer service: Core Business Logic

## Contract

- Contract file: contracts/iot-ingestion.openapi.yaml
- Mock base URL: http://localhost:4010
- Auth method: Bearer Token (JWT or Lab Token)
- Endpoint được test:
  - GET /health
  - POST /readings
  - GET /readings/latest

## Smoke test

### Request

```http
POST /readings HTTP/1.1
Host: localhost:4010
Authorization: Bearer lab-token
Content-Type: application/json

{
  "device_id": "ESP32-LAB-A01",
  "metric": "temperature",
  "value": 31.5,
  "unit": "celsius",
  "timestamp": "2026-05-13T08:30:00+07:00"
}
```

### Expected response

```json
{
  "reading_id": "R-20260513-0001",
  "device_id": "ESP32-LAB-A01",
  "metric": "temperature",
  "accepted": true,
  "created_at": "2026-05-13T08:30:01+07:00"
}
```

## Kết quả

- [x] Consumer gọi mock thành công.
- [x] Consumer parse được field cần dùng.
- [x] Consumer hiểu lỗi 4xx/5xx provider trả về.
- [x] Có Newman report hoặc screenshot.

## Ghi chú thay đổi hợp đồng

| Nội dung | Trước | Sau | Người đồng ý |
|----------|-------|-----|-------------|
| Temperature range | 0-100°C | -40 to 80°C | Cả hai team |
| Auth method | API Key | Bearer Token | Provider team |
| Response time SLA | Not defined | < 500ms | Provider team |
|---|---|---|---|
| | | | |

## Xác nhận

- Provider representative:
- Consumer representative:
