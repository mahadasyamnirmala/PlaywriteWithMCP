# Test Plan: VWO Login Page

| Field | Value |
|-------|-------|
| **Version** | 1.1 |
| **Author** | QA Team |
| **Date** | 2026-03-23 |
| **Environment** | Production |
| **Browser** | Chromium, WebKit, Firefox |

---

## 1. Introduction

This test plan describes the testing approach for **VWO Login Page** (`app.vwo.com/#/login`). It outlines the scope, test strategy, resources, schedule, and deliverables for the testing effort.

The VWO login page allows users to sign in to the VWO Digital Experience Optimization platform using their email and password, Google SSO, Enterprise SSO, or Passkey. The page also features a promotional panel highlighting VWO's partnership with ABTasty.

## 2. Objectives

- Verify core login functionality works as expected (email/password sign-in)
- Identify defects before production release
- Ensure user flows are complete and error-free (including all alternative sign-in methods)
- Validate UI elements, navigation links, and form field behaviors
- Confirm proper error messaging for invalid credentials and empty fields

## 3. Scope

### In Scope
- Login via standard **Email ID** and **Password** credentials
- Input validations:
  - Empty email field submission
  - Empty password field submission
  - Invalid/malformed email format (missing `@`, no domain, etc.)
  - Incorrect password for a valid email
  - Unregistered email address
- **Toggle password visibility** (eye icon on password field)
- **Remember me** checkbox state and behavior
- Navigation links:
  - `Forgot Password?` link
  - `Start a FREE TRIAL` button
  - `Privacy policy` link
  - `Terms` link
- Alternative sign-in button initiations:
  - `Sign in with Google`
  - `Sign in using SSO`
  - `Sign in with Passkey`
- UI and layout checks:
  - Left panel: VWO logo, form fields, action buttons
  - Right panel: VWO + ABTasty promotional banner
  - Desktop (1280×800) and tablet (768×1024) resolutions

### Out of Scope
- Complete end-to-end OAuth flows (e.g., completing Google authentication after redirect)
- Backend API performance or load testing
- Post-login dashboard interactions (after successful redirect)
- CAPTCHA bypass or automation (if triggered by rate limits)
- Mobile responsive layout below 768px width (smartphone form factor)

## 4. Test Strategy

### Test Approach
- **Automation Tool:** Playwright with `@playwright/test`
- **Test Type:** End-to-end functional testing
- **Browser:** Chromium, WebKit, Firefox
- **Environment:** Production (`https://app.vwo.com/#/login`)

### Test Levels
- **Smoke Testing** — Critical sign-in path (valid credentials, redirect verification)
- **Functional Testing** — All form fields, buttons, and link behaviors
- **Negative Testing** — Invalid inputs, empty fields, unregistered accounts, wrong passwords
- **Usability Testing** — Password visibility toggle, remember me, label clarity

## 5. Test Environment

| Component | Details |
|-----------|---------|
| Application URL | https://app.vwo.com/#/login |
| Browser | Chromium, WebKit, Firefox |
| OS | Cross-platform (Node.js) |
| Framework | Playwright v1.58+ |
| Reporter | HTML + JSON |

## 6. Entry Criteria

- Application is deployed and accessible at `https://app.vwo.com`
- Test environment is configured with valid Playwright setup
- Test data is available (valid credentials, invalid credentials, unregistered emails)
- Test cases are reviewed and approved by the QA Lead
- Browser installations verified (Chromium, Firefox, WebKit)

## 7. Exit Criteria

- All planned test cases executed (pass/fail status recorded)
- All **Critical** and **High** priority defects resolved or accepted with sign-off
- Test execution report generated (HTML + JSON)
- No open blocker defects remaining
- Test summary report reviewed and signed off

## 8. Test Cases Summary

### 8.1 Smoke Tests (Critical Path)

| Test ID | Title | Priority | Type |
|---------|-------|----------|------|
| **TC_VWO_L_001** | Verify successful login with valid Email ID and Password | Critical | Smoke |
| **TC_VWO_L_002** | Verify user is redirected to dashboard after successful login | Critical | Smoke |

### 8.2 Core Authentication — Negative Tests

| Test ID | Title | Priority | Type |
|---------|-------|----------|------|
| **TC_VWO_L_003** | Verify error message on login with incorrect password | High | Negative |
| **TC_VWO_L_004** | Verify error message on login with unregistered email | High | Negative |
| **TC_VWO_L_005** | Verify validation when submitting form with empty Email field | High | Negative |
| **TC_VWO_L_006** | Verify validation when submitting form with empty Password field | High | Negative |
| **TC_VWO_L_007** | Verify inline validation for malformed Email ID (missing `@`) | Medium | Negative |
| **TC_VWO_L_008** | Verify inline validation for Email ID with no domain (e.g. `user@`) | Medium | Negative |

### 8.3 UI and Usability Tests

| Test ID | Title | Priority | Type |
|---------|-------|----------|------|
| **TC_VWO_L_009** | Verify password field is masked by default | Medium | Usability |
| **TC_VWO_L_010** | Verify password becomes visible on clicking the eye icon | Medium | Usability |
| **TC_VWO_L_011** | Verify password is re-masked on clicking the eye icon again | Medium | Usability |
| **TC_VWO_L_012** | Verify "Remember me" checkbox can be checked and unchecked | Medium | Functional |
| **TC_VWO_L_013** | Verify page title is "Login - VWO" | Low | UI |
| **TC_VWO_L_014** | Verify VWO logo is visible on the login form | Low | UI |
| **TC_VWO_L_015** | Verify right panel shows VWO + ABTasty partnership banner | Low | UI |

### 8.4 Alternative Sign-in and Navigation Tests

| Test ID | Title | Priority | Type |
|---------|-------|----------|------|
| **TC_VWO_L_016** | Verify "Sign in with Google" button initiates Google OAuth flow | High | Functional |
| **TC_VWO_L_017** | Verify "Sign in using SSO" button routes to SSO entry portal | High | Functional |
| **TC_VWO_L_018** | Verify "Sign in with Passkey" button prompts system passkey dialog | High | Functional |
| **TC_VWO_L_019** | Verify "Forgot Password?" navigates to password recovery page | High | Navigation |
| **TC_VWO_L_020** | Verify "Start a FREE TRIAL" button opens the free-trial registration page | Medium | Navigation |
| **TC_VWO_L_021** | Verify "Privacy policy" link resolves to the correct VWO privacy policy URL | Low | Navigation |
| **TC_VWO_L_022** | Verify "Terms" link resolves to the correct VWO terms of service URL | Low | Navigation |

## 9. Risk Assessment

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| Application downtime during test run | High | Low | Monitor uptime; retry tests; notify dev team |
| Flaky tests due to network latency | Medium | Medium | Implement explicit waits; use `waitForURL` / `waitForSelector` |
| Browser version inconsistencies | Medium | Low | Pin browser versions in `playwright.config.ts` |
| Rate limiting / CAPTCHA triggering during automation | Medium | Medium | Use dedicated test account; stagger test runs |
| Third-party OAuth service unavailability (Google, SSO) | Medium | Low | Assert button is clickable and redirect initiates (do not complete OAuth) |

## 10. Schedule

| Phase | Duration |
|-------|----------|
| Test Planning | 1 day |
| Test Case Design | 1 day |
| Test Execution | 1 day |
| Defect Reporting | Ongoing |
| Test Closure | 1 day |

## 11. Deliverables

- [x] Test Plan (this document)
- [ ] Test Cases Document (`VWO_Invalid_Login_Test_Cases.md`)
- [ ] Automated Test Scripts (Playwright `.spec.ts` files)
- [ ] Test Execution Report (HTML + JSON)
- [ ] Defect Reports (Jira tickets)
- [ ] Test Summary Report

---

## Appendix: Login Page UI Reference

The following UI elements were observed on `https://app.vwo.com/#/login` (as of 2026-03-23):

**Left Panel (Form):**
- VWO logo (top-centre)
- "Sign in to VWO platform" subtitle
- Email address field — placeholder: *Enter email ID*
- Password field — placeholder: *Enter password* + eye icon toggle
- "Forgot Password?" link (text link, blue)
- "Remember me" checkbox
- **Sign in** button (primary, purple)
- Separator: *Or*
- **Sign in with Google** button (with Google logo)
- **Sign in using SSO** button (with SSO icon)
- **Sign in with Passkey** button (with passkey icon)
- "Don't have an account?" + **Start a FREE TRIAL** button
- Footer: "By continuing, you agree to VWO's **Privacy policy** & **Terms**."

**Right Panel (Promotional):**
- VWO + ABTasty combined logo
- Heading: *"have joined forces to redefine the future of Digital Experience Optimization"*
- Partnership handshake illustration
- Reassurance message about workflow continuity
