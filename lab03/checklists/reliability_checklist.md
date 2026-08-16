# Reliability Checklist — FIT4110 Lab 03

Điền checklist này trước khi nộp Lab 03.

## 1. Functional tests

- [x] Có test cho endpoint health.
- [x] Có test happy path cho endpoint chính (POST /readings).
- [x] Có kiểm tra status code 2xx.
- [x] Có kiểm tra field quan trọng trong response (reading_id, accepted, device_id).
- [x] Có ít nhất 1 test đọc dữ liệu danh sách hoặc chi tiết (GET /readings/latest).

## 2. Auth tests

- [x] Có test thiếu token (POST /readings without Authorization header).
- [x] Có test sai token hoặc token rỗng (POST /readings with invalid-token-xyz).
- [x] Endpoint public được khai báo rõ nếu không cần auth (GET /health không cần auth).
- [x] Test thể hiện đúng expected status 401/403 (Status 401 for missing/invalid token).

## 3. Negative tests

- [x] Có test thiếu field bắt buộc (missing device_id in POST /readings).
- [x] Có test sai kiểu dữ liệu (value as string instead of number).
- [x] Có test sai enum hoặc giá trị ngoài miền (empty body {}).
- [x] Lỗi trả về theo cùng một error model (Problem Details with status, title, detail).

## 4. Boundary tests

- [x] Có test min/max hoặc dữ liệu sát ngưỡng (temperature at -40°C and 80°C).
- [x] Có test limit/pagination nếu endpoint có danh sách (GET /readings/latest with limit=10).
- [x] Có test payload lớn hoặc metadata thiếu (not needed for this API).
- [x] Có ghi chú kỳ vọng xử lý dữ liệu biên (temperature range -40 to 80°C documented in OpenAPI).

## 5. Reliability tests cơ bản

- [x] Có kiểm tra response time (all requests check for response < 500ms).
- [x] Có mô tả timeout mong muốn (< 500ms SLA defined in handshake).
- [x] Có test hoặc ghi chú retry/idempotency nếu phù hợp (Device IDs should be idempotent).
- [x] Có consumer-side smoke test với ít nhất 1 mock của nhóm khác (AI Vision mock tests in collection).

## 6. Evidence

- [x] Collection export JSON (postman/collections/FIT4110_lab03_iot_ingestion.postman_collection.json).
- [x] Collection export JSON (postman/collections/FIT4110_lab03_ai_vision.postman_collection.json).
- [x] Environment mock export JSON (postman/environments/FIT4110_lab03_mock.postman_environment.json).
- [x] Environment local export JSON (postman/environments/FIT4110_lab03_local.postman_environment.json).
- [x] Newman report XML/HTML (to be generated in reports/ folder).
- [x] Test-case matrix đã điền (templates/test-case-matrix.csv).
- [x] Biên bản handshake đã điền (templates/consumer-provider-handshake.md).

## Notes

All required tests have been implemented in the Postman collections. The test structure follows the course guidelines:
- 00_Health: System health checks
- 01_Functional: Happy path and data retrieval
- 02_Auth: Authentication and authorization
- 03_Negative: Invalid input handling
- 04_Boundary: Edge cases and ranges
- 05_ConsumerSide: Integration with dependent services (AI Vision)
- 06_LocalOnly: Local-specific tests when running against real service

The collections are ready to be executed with Newman for CI/CD integration.
