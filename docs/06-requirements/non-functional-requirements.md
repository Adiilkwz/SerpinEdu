# Non-Functional Requirements

## 1. Conventions

Priorities and sources follow the conventions in [functional-requirements.md](functional-requirements.md#1-conventions).

The numeric targets below are **initial targets** chosen for a diploma-scale system. They will be measured according to the verification and evaluation plan (`docs/09-verification-plan/`) and may be adjusted based on the results.

**Verification methods:** UT — unit test, IT — integration / API test, PT — performance test, SR — code or configuration review, MT — manual test.

**Reference load profile** (used by performance requirements): test database with 10,000 students, 200 published courses and 500,000 XP records; 100 concurrent users; test environment described in the verification plan.

## 2. Performance (PERF)

| ID | Requirement | Target | Priority | Verification |
|---|---|---|---|---|
| NFR-PERF-01 | Response time of read API requests (catalog, search, course page, lesson page) under the reference load | 95th percentile ≤ 500 ms | Must | PT |
| NFR-PERF-02 | Response time of a learning event (lesson completed or test submitted), including XP, level, streak and achievement processing, under the reference load | 95th percentile ≤ 1 s | Must | PT |
| NFR-PERF-03 | Response time of a leaderboard request including the student's own position, under the reference load | 95th percentile ≤ 500 ms | Must | PT |
| NFR-PERF-04 | Generation of a PDF certificate | ≤ 5 s | Should | IT |

## 3. Capacity (CAP)

| ID | Requirement | Target | Priority | Verification |
|---|---|---|---|---|
| NFR-CAP-01 | The system works with the data volume of the reference load profile | 10,000 students, 200 courses, 500,000 XP records | Must | PT |
| NFR-CAP-02 | The system serves concurrent users without errors | 100 concurrent users, error rate < 1% | Must | PT |

## 4. Security (SEC)

| ID | Requirement | Priority | Verification |
|---|---|---|---|
| NFR-SEC-01 | Passwords are stored only as hashes produced by an adaptive password hashing algorithm (bcrypt or Argon2); plain-text passwords are never stored or logged | Must | SR, IT |
| NFR-SEC-02 | Authenticated requests use tokens with limited lifetime: access token 15 minutes, refresh token 30 days | Must | IT |
| NFR-SEC-03 | Role checks are enforced on the backend for every API endpoint; requests without authentication receive 401, requests with an insufficient role receive 403 | Must | IT |
| NFR-SEC-04 | Database queries use parameters (no string concatenation of user input); user-generated text is escaped when displayed | Must | SR, IT |
| NFR-SEC-05 | Login and password reset requests are limited to 5 attempts per minute per account and IP address | Should | IT |
| NFR-SEC-06 | Secrets (passwords, keys, tokens) are not stored in the repository; configuration uses environment variables with placeholder examples | Must | SR |
| NFR-SEC-07 | In a deployed environment, all traffic uses HTTPS | Should | MT |
| NFR-SEC-08 | The system follows the OWASP Top 10 recommendations for the categories relevant to the project (access control, injection, authentication) [N1] | Should | SR |

## 5. Reliability and data integrity (REL)

| ID | Requirement | Priority | Verification |
|---|---|---|---|
| NFR-REL-01 | Processing of a learning event is atomic: progress, XP, level, streak and achievements are either all updated or none of them | Must | IT |
| NFR-REL-02 | Processing the same learning event twice does not award XP or achievements twice | Must | UT, IT |
| NFR-REL-03 | All timestamps are stored in UTC; dates relevant to the user (streaks, deadlines in the interface) are converted to the user's time zone | Must | UT |
| NFR-REL-04 | A failed or interrupted payment never grants access to a paid course | Must | IT |

## 6. Usability and accessibility (USE)

| ID | Requirement | Priority | Verification |
|---|---|---|---|
| NFR-USE-01 | All interface texts are stored in translation files for English and Russian; no hard-coded interface strings | Must | SR |
| NFR-USE-02 | The interface works correctly in the latest versions of Chrome, Firefox and Edge on desktop (screen width from 1280 px) | Must | MT |
| NFR-USE-03 | Key pages (catalog, course page, lesson page, profile) are usable with a keyboard, images have text alternatives and text contrast meets WCAG 2.1 level AA [N2] | Should | MT |
| NFR-USE-04 | A student can reach any lesson of an enrolled course from the dashboard in no more than 3 clicks | Should | MT |

## 7. Maintainability (MNT)

| ID | Requirement | Priority | Verification |
|---|---|---|---|
| NFR-MNT-01 | The backend follows the modular structure defined in the architecture; modules communicate only through their public interfaces | Must | SR |
| NFR-MNT-02 | All API endpoints are described in the OpenAPI specification (`backend/api/openapi.yaml`) | Must | SR |
| NFR-MNT-03 | Unit test coverage of the gamification module (XP, levels, streaks, achievements, leaderboards) is at least 80%; of other backend domain modules — at least 60% | Must | UT |
| NFR-MNT-04 | XP values, level thresholds and achievement rules are configurable data, not hard-coded values | Must | SR |
| NFR-MNT-05 | Code follows the standard formatters and linters of each language (gofmt for Go, ESLint for TypeScript) | Should | SR |

## 8. Portability and deployment (POR)

| ID | Requirement | Priority | Verification |
|---|---|---|---|
| NFR-POR-01 | The whole system can be started locally by following the setup instructions in the README | Must | MT |
| NFR-POR-02 | The local environment, including the database, starts with a single command | Should | MT |

## 9. Summary

| Priority | Number of requirements |
|---|---|
| Must | 21 |
| Should | 8 |
| **Total** | **29** |

## 10. References

- [N1] OWASP Foundation. *OWASP Top Ten*. https://owasp.org/www-project-top-ten/
- [N2] W3C. *Web Content Accessibility Guidelines (WCAG) 2.1*. https://www.w3.org/TR/WCAG21/
