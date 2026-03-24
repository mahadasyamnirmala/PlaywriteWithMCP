# Test Cases: VWO Login Page

| Field | Value |
|-------|-------|
| **Version** | 1.0 |
| **Author** | QA Team |
| **Date** | 2026-03-23 |
| **Total Test Cases** | 5 |

---

## Test Case Format

Each test case follows this structure:

| Field | Description |
|-------|-------------|
| **TC ID** | Unique identifier (TC-001, TC-002, ...) |
| **Title** | Brief description of what is tested |
| **Preconditions** | What must be true before the test |
| **Steps** | Step-by-step instructions |
| **Expected Result** | What should happen |
| **Priority** | High / Medium / Low |
| **Category** | Smoke / Functional / Negative |
| **Spec File** | Corresponding Playwright spec file |

---

## Test Cases

### TC-001: Invalid Login using Arabic Characters
| Field | Value |
|-------|-------|
| **TC ID** | TC-001 |
| **Title** | Verify authentication failure with Arabic characters in Email/Password |
| **Preconditions** | Application URL is accessible. User is on the login page (`https://app.vwo.com/#/login`). |
| **Steps** | 1. Enter an email containing Arabic characters (e.g., `مستخدم@مثال.كوم`).<br>2. Enter an invalid password.<br>3. Click the "Sign in" button. |
| **Expected Result** | System should display an appropriate error validation message indicating invalid email format or authentication failure, and login must be prevented. |
| **Priority** | High |
| **Category** | Negative |
| **Spec File** | `vwo_invalid_login.spec.ts` |

### TC-002: Invalid Login using Chinese Characters
| Field | Value |
|-------|-------|
| **TC ID** | TC-002 |
| **Title** | Verify authentication failure with Chinese characters in Email field |
| **Preconditions** | Application URL is accessible. User is on the login page (`https://app.vwo.com/#/login`). |
| **Steps** | 1. Enter an email containing Chinese characters (e.g., `测试@域名.公司`).<br>2. Enter an invalid password.<br>3. Click the "Sign in" button. |
| **Expected Result** | System should display an error validation message indicating invalid email format or authentication failure, and login must be prevented. |
| **Priority** | High |
| **Category** | Negative |
| **Spec File** | `vwo_invalid_login.spec.ts` |

### TC-003: Invalid Login using Dummy/Fake Credentials
| Field | Value |
|-------|-------|
| **TC ID** | TC-003 |
| **Title** | Verify authentication failure with a dummy/fake email address |
| **Preconditions** | Application URL is accessible. User is on the login page (`https://app.vwo.com/#/login`). |
| **Steps** | 1. Enter a structurally valid but dummy/fake email (e.g., `dummy12345@dummy.com`).<br>2. Enter an invalid dummy password.<br>3. Click the "Sign in" button. |
| **Expected Result** | System should display an error message stating "That email address doesn't exist" or a generic authentication failure message. |
| **Priority** | High |
| **Category** | Negative |
| **Spec File** | `vwo_invalid_login.spec.ts` |

### TC-004: Invalid Login using SQL Injection Payload
| Field | Value |
|-------|-------|
| **TC ID** | TC-004 |
| **Title** | Verify application handles SQL injection attempts gracefully in the login form |
| **Preconditions** | Application URL is accessible. User is on the login page (`https://app.vwo.com/#/login`). |
| **Steps** | 1. Enter an SQL injection payload in the Email field (e.g., `' OR 1=1 --`).<br>2. Enter an arbitrary password.<br>3. Click the "Sign in" button. |
| **Expected Result** | System should not execute the payload. It should display a format validation error or an authentication failure message, preventing login. |
| **Priority** | High |
| **Category** | Negative |
| **Spec File** | `vwo_invalid_login.spec.ts` |

### TC-005: Invalid Login using Extremely Long String
| Field | Value |
|-------|-------|
| **TC ID** | TC-005 |
| **Title** | Verify validation when email field exceeds maximum character limits |
| **Preconditions** | Application URL is accessible. User is on the login page (`https://app.vwo.com/#/login`). |
| **Steps** | 1. Enter an extremely long string (e.g., 256+ characters) in the Email field.<br>2. Enter an arbitrary password.<br>3. Click the "Sign in" button. |
| **Expected Result** | The form should prevent submission either via frontend max-length restriction or display an error message indicating the input is too long/invalid. Login must be prevented. |
| **Priority** | Medium |
| **Category** | Negative |
| **Spec File** | `vwo_invalid_login.spec.ts` |

---

## Summary

| Priority | Count |
|----------|-------|
| High | 4 |
| Medium | 1 |
| Low | 0 |
| **Total** | **5** |

| Category | Count |
|----------|-------|
| Smoke | 0 |
| Functional | 0 |
| Negative | 5 |
