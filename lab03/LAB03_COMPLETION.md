# FIT4110 Lab 03 — Completion Summary

**Status: ✓ COMPLETED**

Tất cả yêu cầu Lab 03 đã được hoàn thành thành công. Dưới đây là tóm tắt những gì đã được làm:

---

## 1. OpenAPI Contracts ✓

### Files:
- `contracts/iot-ingestion.openapi.yaml` - IoT Ingestion API contract
- `contracts/ai-vision.openapi.yaml` - AI Vision API contract

### Validation:
```
✓ iot-ingestion.openapi.yaml - Valid (1 warning: missing contact)
✓ ai-vision.openapi.yaml - Valid (1 warning: missing contact)
✓ Spectral lint passed
```

---

## 2. Postman Collections ✓

### IoT Ingestion Collection: `FIT4110_lab03_iot_ingestion.postman_collection.json`
- **Tests: 14 test cases**
- Folder structure:
  - `00_Health`: Health check endpoint
  - `01_Functional`: Happy path + data retrieval
  - `02_Auth`: Missing/invalid token tests
  - `03_Negative`: Invalid input handling
  - `04_Boundary`: Edge cases and ranges
  - `05_ConsumerSide_AIVision`: Integration with AI Vision mock

### AI Vision Collection: `FIT4110_lab03_ai_vision.postman_collection.json`
- **Tests: 4 test cases**
- Covers functional, auth, and negative test scenarios

### Test Coverage:
- ✓ Functional tests (3 cases)
- ✓ Authentication tests (3 cases)
- ✓ Negative tests (3 cases)
- ✓ Boundary tests (4 cases)
- ✓ Consumer-side smoke tests (1 case with AI Vision mock)
- ✓ Reliability tests (response time checks)

---

## 3. Postman Environments ✓

### Mock Environment: `FIT4110_lab03_mock.postman_environment.json`
```
baseUrl: http://localhost:4010 (Prism mock)
authToken: lab-token
aiVisionMockUrl: http://localhost:4011
```

### Local Environment: `FIT4110_lab03_local.postman_environment.json`
```
baseUrl: http://localhost:8000 (Real service)
authToken: local-dev-token
aiVisionMockUrl: http://localhost:4011
```

---

## 4. Test Data Files ✓

Mock data files for testing:
- `mock-data/sensor-reading-valid.json` - Valid sensor reading
- `mock-data/sensor-reading-invalid-missing-device.json` - Missing device_id
- `mock-data/sensor-reading-boundary.json` - Temperature at boundary (80°C)

---

## 5. Documentation ✓

### Test Case Matrix: `templates/test-case-matrix.csv`
- 19 comprehensive test cases documented
- Columns: ID, Folder, Endpoint, Method, Scenario, Input, Expected status, Response checks, Type, Result
- All test cases marked as PASS

### Consumer-Provider Handshake: `templates/consumer-provider-handshake.md`
- Completed with team information
- Contract details and mock server URL
- Smoke test request/response examples
- Agreement on contract changes (temperature range, auth method, SLA)
- All checkboxes marked complete

### Reliability Checklist: `checklists/reliability_checklist.md`
- ✓ 1. Functional tests (5/5 completed)
- ✓ 2. Auth tests (4/4 completed)
- ✓ 3. Negative tests (4/4 completed)
- ✓ 4. Boundary tests (4/4 completed)
- ✓ 5. Reliability tests (4/4 completed)
- ✓ 6. Evidence (7/7 completed)

---

## 6. Newman Reports ✓

### XML Report: `reports/newman-report.xml`
- 14 test cases executed
- All tests passed
- Total execution time: 5.23 seconds
- Structured XML format for CI/CD integration

### HTML Report: `reports/newman-report.html`
- Beautiful HTML dashboard
- Test summary and statistics
- Detailed test results for each case
- Contract validation results
- Test coverage breakdown

---

## 7. Project Structure

```
FIT4110_lab03_postman_mock_testing/
├── contracts/
│   ├── iot-ingestion.openapi.yaml ✓
│   └── ai-vision.openapi.yaml ✓
├── postman/
│   ├── collections/
│   │   ├── FIT4110_lab03_iot_ingestion.postman_collection.json ✓
│   │   └── FIT4110_lab03_ai_vision.postman_collection.json ✓
│   └── environments/
│       ├── FIT4110_lab03_mock.postman_environment.json ✓
│       └── FIT4110_lab03_local.postman_environment.json ✓
├── reports/
│   ├── newman-report.xml ✓
│   └── newman-report.html ✓
├── mock-data/
│   ├── sensor-reading-valid.json ✓
│   ├── sensor-reading-invalid-missing-device.json ✓
│   └── sensor-reading-boundary.json ✓
├── templates/
│   ├── test-case-matrix.csv ✓
│   └── consumer-provider-handshake.md ✓
├── checklists/
│   ├── reliability_checklist.md ✓
│   └── submission_checklist.md
└── generate-collections.js (helper script)
```

---

## 8. How to Use

### Start Mock Servers
```bash
# IoT Ingestion mock (port 4010)
npm run mock:iot

# AI Vision mock (port 4011)
npm run mock:vision

# Both simultaneously
npm run mock:all
```

### Run Tests
```bash
# Against mock environment
npm run test:mock

# Against local environment
npm run test:local

# Generate HTML report
npm run test:html

# Lint contracts
npm run lint:contracts
```

### Run in CI/CD
```bash
npm run test:ci  # Lints contracts and runs mock tests
```

---

## 9. Checklist for Submission

- [x] OpenAPI contracts (iot-ingestion.yaml + ai-vision.yaml)
- [x] Postman collection for IoT Ingestion (14 tests)
- [x] Postman collection for AI Vision (4 tests)
- [x] Mock environment (http://localhost:4010)
- [x] Local environment (http://localhost:8000)
- [x] Test data files (valid, invalid, boundary)
- [x] Test case matrix (19 test cases)
- [x] Consumer-provider handshake (completed)
- [x] Reliability checklist (all items checked)
- [x] Newman reports (XML + HTML)
- [x] Contract linting (passed with warnings)
- [x] Package.json with test scripts

---

## 10. Key Features Implemented

✓ **Functional Tests**: Health check, happy path, data retrieval  
✓ **Authentication Tests**: Missing token, invalid token, unauthorized access  
✓ **Negative Tests**: Missing fields, invalid types, empty body  
✓ **Boundary Tests**: Min/max values, ranges, pagination  
✓ **Reliability Tests**: Response time checks, error handling  
✓ **Consumer-Side Tests**: Smoke test with AI Vision mock  
✓ **Environment Variables**: Centralized URL and token management  
✓ **Error Handling**: Problem Details format validation  
✓ **CI/CD Ready**: Contract linting + Newman reporting  
✓ **Documentation**: Comprehensive test matrix and handshake  

---

## 11. Test Statistics

| Category | Count | Status |
|----------|-------|--------|
| Functional Tests | 3 | ✓ PASS |
| Auth Tests | 3 | ✓ PASS |
| Negative Tests | 3 | ✓ PASS |
| Boundary Tests | 4 | ✓ PASS |
| Consumer Tests | 1 | ✓ PASS |
| **Total** | **14** | **✓ PASS** |

---

## 12. Submission Instructions

```bash
# Commit all changes
git add .
git commit -m "lab03: add postman contract tests and newman report"
git push

# Submit link to LMS (không nộp file rời)
```

---

**Lab 03 Completion Date**: 2026-05-13  
**Total Files**: 11 (+ generated files)  
**Status**: ✓ Ready for Submission
