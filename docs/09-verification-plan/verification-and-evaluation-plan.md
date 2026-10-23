# Verification and Evaluation Plan

**Project:** SerpinEdu — Development of a Management System of Educational Electronic Courses
**Task:** DIP-11
**Status:** Version 1 (pre-defense 1)

## 1. Purpose

This plan describes how the team will show that the project aim is achieved. The aim, from the [project proposal](../01-proposal/project-proposal.md), is:

> To develop a web-based open marketplace of educational electronic courses that supports the full course lifecycle — from course creation and moderation to learning and certification — and uses gamification to make learning more engaging.

The plan has two parts:

- **Verification** (section 3): does the system meet its [functional](../06-requirements/functional-requirements.md) and [non-functional](../06-requirements/non-functional-requirements.md) requirements?
- **Evaluation** (section 4): does the system reach its aim with real users, and does gamification make learning more engaging than the same system without it (the baseline)?

| Part of the aim | How it is demonstrated | Section |
|---|---|---|
| A working web-based course marketplace | All acceptance criteria of the Must requirements pass; non-functional targets are met | 3.2, 3.5 |
| The full course lifecycle: creation → moderation → learning → certification | End-to-end scenarios that go through all roles in one run | 3.3 |
| Gamification makes learning more engaging | Two-week study with two groups: the same course with and without gamification | 4 |
| Usable for learners | System Usability Scale (SUS) in both groups, compared with the published average | 4.7 |

## 2. Overview of activities

| Activity | Question it answers | Method | When |
|---|---|---|---|
| Unit and integration tests | Does each function behave as specified? | Automated tests, run on every pull request | During implementation |
| End-to-end and manual tests | Do complete user scenarios work in the browser? | Automated browser tests and checklists | Before pre-defense 2 and the final pre-defense |
| Performance tests | Does the system meet the response-time targets under the reference load? | Load tests | Before the final pre-defense |
| Code and configuration review | Are structure, security and maintainability rules followed? | Pull request review checklist, linters | Every pull request |
| User study | Does gamification increase engagement compared with the baseline? Is the system usable? | Two groups, two weeks, system data and questionnaires | After the system is deployed |

## 3. Verification

### 3.1 Test levels and tools

The tools are proposed for implementation and may be replaced by equivalents; the test levels and criteria do not change.

| Level | Code | What is tested | Proposed tools | Where it runs |
|---|---|---|---|---|
| Unit test | UT | Domain logic without the database: XP, level formula, streak calculation, achievement rules, leaderboard ranking, commission | Go `testing` package | Locally and in CI on every pull request |
| Integration / API test | IT | REST endpoints with a real PostgreSQL database: requests, responses, roles, transactions | Go `testing`, `net/http/httptest`, PostgreSQL in Docker | Locally and in CI on every pull request |
| End-to-end test | E2E | User scenarios through the web interface | Playwright | Full system started with Docker Compose |
| Manual test | MT | Video playback, browsers, accessibility, local setup | Checklists in the test report | Before each milestone |
| Performance test | PT | Response times and errors under the reference load | k6 | Performance environment (section 3.6) |
| Review | SR | Module structure, security rules, configuration, OpenAPI | Pull request checklist; `gofmt`, ESLint | Every pull request |

CI runs in GitHub Actions. A pull request can be merged only if unit and integration tests pass.

### 3.2 Functional requirements

Every one of the 64 functional requirements has acceptance criteria and verification methods in [acceptance-criteria.md](../06-requirements/acceptance-criteria.md):

| Verification method | Number of requirements using it |
|---|---|
| IT | 50 |
| E2E | 32 |
| UT | 15 |
| MT | 3 |

A requirement may use several methods. Rules:

- Every automated test names the requirement it checks (e.g. `TestFRGAM04_StreakResetsAfterMissedDay`, or the ID in the E2E test title). A script lists the tests per requirement for the test report.
- A requirement passes when **all** its acceptance criteria pass.
- Defects are registered in YouTrack as type Bug with a link to the requirement and a severity: Critical (data loss, security problem or a Must requirement blocked), High, Medium, Low.

#### Gamification rules

The gamification module has the highest coverage target (NFR-MNT-03: at least 80%), because the evaluation depends on it. Unit and integration tests cover at least these boundary cases:

| Case | Requirements |
|---|---|
| Level thresholds: 99 → 100 XP (level 2), 999 → 1,000 XP (level 5) | FR-GAM-03 |
| The same lesson completed twice or a test passed again gives no new XP; the same event processed twice gives no double XP | FR-GAM-02, NFR-REL-02 |
| Streak: activity on the next local day adds 1; more activity on the same day adds nothing; a missed day resets it | FR-GAM-04 |
| Streak across midnight for students in different time zones (e.g. UTC+5 and UTC−5) | FR-GAM-04, NFR-REL-03 |
| An achievement is awarded once, even if its condition is met again | FR-GAM-07 |
| A new achievement rule added to the database works without code changes | FR-GAM-06, NFR-MNT-04 |
| Leaderboard ties: 1, 2, 2, 4 | FR-GAM-12 |
| Week boundary: XP at Sunday 23:59 and Monday 00:00 in the platform time zone | FR-GAM-10 |
| A student outside the top 50 still sees their own rank | FR-GAM-12 |
| An error in the middle of a learning event leaves no partial changes | NFR-REL-01 |

### 3.3 End-to-end scenarios: the full course lifecycle

These scenarios run in order on one clean system and together demonstrate the full course lifecycle from the aim. Use case IDs refer to the [architecture description](../07-architecture/architecture-description.md), section 4.

| ID | Scenario | Use cases |
|---|---|---|
| E2E-1 | An author creates a course with a video lesson (YouTube or Vimeo link), a text lesson and a test, marks a preview lesson and submits the course for moderation | UC21, UC22, UC23 |
| E2E-2 | An administrator rejects the course with a comment; the author fixes it and resubmits; the administrator approves it, and the course appears in the catalog | UC26, UC23, UC01 |
| E2E-3 | A guest finds the course by search and filters, opens the preview lesson, registers and confirms the email | UC01, UC02, UC03, UC04 |
| E2E-4 | The student pays in test mode: a failed payment gives no access; a successful payment enrols the student | UC07, UC08 |
| E2E-5 | The student completes all lessons and tests; XP, level, streak and achievements change as specified; the certificate is issued and downloaded | UC09, UC10, UC11, UC12 |
| E2E-6 | The student sees the profile and the weekly leaderboard with their own position; the interface is switched to Russian | UC17, UC18 |
| E2E-7 | The student asks a question; the author sees students, question statistics and income, and answers the question; the student gets a notification | UC13, UC24, UC25, UC19 |
| E2E-8 | The student reports a review; the administrator hides it; the administrator changes the commission and the leaderboard time zone | UC15, UC28, UC30 |

### 3.4 Manual test checklist

| Check | Requirements |
|---|---|
| A YouTube video and a Vimeo video play, pause and seek in the lesson page | FR-LRN-04 |
| Key flows work in the latest Chrome, Firefox and Edge at 1280 px width | NFR-USE-02 |
| Catalog, course page, lesson page and profile can be used with the keyboard; images have text alternatives; the accessibility audit in the browser (Lighthouse) reports no contrast errors | NFR-USE-03 |
| Any lesson of an enrolled course is reached from the dashboard in at most 3 clicks | NFR-USE-04 |
| A team member who did not prepare the environment starts the system on a clean machine by following the README, with one command | NFR-POR-01, NFR-POR-02 |
| The deployed system redirects HTTP to HTTPS | NFR-SEC-07 |

### 3.5 Non-functional requirements

| Requirement | How it is checked | Pass criterion |
|---|---|---|
| NFR-PERF-01 | Load test, read requests (catalog, search, course page, lesson page) | p95 ≤ 500 ms |
| NFR-PERF-02 | Load test, lesson completion and test submission | p95 ≤ 1 s |
| NFR-PERF-03 | Load test, weekly and all-time leaderboard with own position | p95 ≤ 500 ms |
| NFR-PERF-04 | Integration test: generate 20 certificates, measure each from job start to stored PDF | every certificate ≤ 5 s |
| NFR-CAP-01 | Load tests run on the reference data set (section 3.6) | all PERF targets met on this data |
| NFR-CAP-02 | Load test with 100 virtual users | error rate < 1% |
| NFR-SEC-01 | Review of the registration code; integration test checks that the stored value is a bcrypt or Argon2 hash and that the password does not appear in logs | both checks pass |
| NFR-SEC-02 | Integration test: an access token older than 15 minutes is rejected; a refresh token works until 30 days | both checks pass |
| NFR-SEC-03 | Integration test generated from `openapi.yaml`: every protected endpoint without a token and with each insufficient role | 401 and 403 for all |
| NFR-SEC-04 | Review: no SQL built by string concatenation; integration test with SQL and HTML special characters in user input | no injection, text is escaped |
| NFR-SEC-05 | Integration test: 6 login or password reset requests within one minute | the 6th request is refused |
| NFR-SEC-06 | Review of the repository and `.env.example`; secret scanning in CI | no secrets found |
| NFR-SEC-07 | Manual check on the deployed system (section 3.4) | HTTPS only |
| NFR-SEC-08 | Review against the OWASP Top 10 categories access control, injection and authentication | no open findings |
| NFR-REL-01 | Integration test: a failure is forced during a learning event | no partial changes in the database |
| NFR-REL-02 | Unit and integration tests: the same event sent twice | XP and achievements awarded once |
| NFR-REL-03 | Unit tests: storage in UTC, conversion to the user's time zone | all cases pass |
| NFR-REL-04 | Integration test: failed and interrupted test-mode payments | no enrolment created |
| NFR-USE-01 | Review: no interface text outside the EN and RU translation files; both files contain the same keys | no missing keys |
| NFR-USE-02, NFR-USE-03, NFR-USE-04 | Manual checklist (section 3.4) | all checks pass |
| NFR-MNT-01 | Review: modules use only each other's public interfaces | no violations |
| NFR-MNT-02 | Review and CI check: every implemented endpoint is in `openapi.yaml` | no undocumented endpoints |
| NFR-MNT-03 | Coverage report (`go test -cover`) in CI | gamification ≥ 80%, other domain modules ≥ 60% |
| NFR-MNT-04 | Review: XP values, level thresholds and achievement rules are read from the database | no hard-coded values |
| NFR-MNT-05 | `gofmt` and ESLint in CI | no errors |
| NFR-POR-01, NFR-POR-02 | Manual checklist (section 3.4) | all checks pass |

### 3.6 Performance test conditions

| Item | Condition |
|---|---|
| System under test | The whole system started with Docker Compose on one machine. CPU, memory, operating system and software versions are recorded in the test report |
| Load generator | k6 on a separate machine in the same network; if this is not possible, on the same machine, which is noted in the report |
| Data | A seed script creates the reference data set: 10,000 students, 200 published courses, 500,000 XP records (NFR-CAP-01). All data is synthetic; no personal data |
| Load | 100 virtual users (NFR-CAP-02). Proposed request mix: 70% read requests, 20% learning events, 10% leaderboard requests |
| Duration | 2 minutes ramp-up, 10 minutes steady load; only the steady phase is measured |
| Repetitions | 3 runs; the median of the three p95 values is reported |
| Measured | p95 response time per request type, error rate, requests per second |

If a target is not met, the bottleneck is fixed (for the leaderboard, the fallback in the architecture description, section 8.3) and the test is repeated. The non-functional targets are initial targets; changing a target requires a written reason in the test report.

### 3.7 Exit criteria for the final version

- All acceptance criteria of all **Must** functional requirements pass.
- **Should** and **Could** requirements pass or are listed in the test report as not implemented, with a reason.
- All **Must** non-functional requirements meet their targets, or a deviation is justified in the test report.
- No open defects of severity Critical or High.

## 4. Evaluation

### 4.1 Evaluation questions

| ID | Question | Related |
|---|---|---|
| EQ1 | Do students who learn with gamification study more actively and complete the course more often than students who learn the same course without gamification? | H3; objective 6 |
| EQ2 | How do students perceive the game elements: do XP, streaks, achievements and leaderboards motivate them, and do the daily streak and the public leaderboard create pressure? | H3; concerns from the [user interviews](../02-relevance-evidence/evidence-summary.md), section 5 |
| EQ3 | Is the system usable for learners? | Aim; objective 5 |

### 4.2 Design

A between-groups comparison: participants are randomly assigned to two groups and take the same course in the same system for two weeks.

| | Experimental group | Control group (baseline) |
|---|---|---|
| Course, lessons, tests, certificate | Same | Same |
| Interface, notifications about questions and certificates | Same | Same |
| XP, levels, streak, achievements | Shown | Not shown |
| Leaderboards | Shown; only experimental-group participants appear on them | Not shown |
| Gamification notifications (new level, achievement) | Sent | Not sent |

### 4.3 Baseline solution

The baseline is **SerpinEdu with gamification hidden**. This isolates the effect of gamification: everything else — content, interface, tests and certificate — is identical. Existing platforms were not chosen as the baseline because they differ from SerpinEdu in many features at once (see the [existing systems comparison](../04-existing-systems-comparison/existing-systems-comparison.md)), so a difference in results could not be attributed to gamification.

Implementation: before the study, the team marks the accounts of the control group with a setting that hides gamification. The backend still records lessons, test attempts and course completions for both groups, so the same metrics can be calculated for everyone. This setting is needed only for the evaluation and is not available to students; it will be added to the requirements as a separate requirement for administrators.

Two further reference points are used:

- **Usability:** the average SUS score of 68, based on 241 industrial usability studies and surveys [V2, V3].
- **Technical quality:** the targets of the non-functional requirements (section 3.5).

### 4.4 Participants

| Item | Plan |
|---|---|
| Number | 10–15 participants, 5–8 per group |
| Who | University students aged 18 or older, recruited through the team's network |
| Assignment | Random, with a random number generator, so that group sizes differ by at most one |
| Consent | Written consent before the study: purpose, duration, what data is collected, the right to stop at any time |
| Anonymity | Participants are referred to as P01, P02, …; only aggregated, anonymised results are published in the repository |

### 4.5 Study material

A short course created by the team: 2–3 modules with video lessons (YouTube or Vimeo links), text lessons and one test per module. The course is free, so that payment does not influence the results. The topic will be chosen by the team before the study; participants should not already know it well.

### 4.6 Procedure

| Day | Step |
|---|---|
| 0 | Short briefing with the same text for both groups. It describes the study as testing a learning platform and does not mention gamification. Consent and pre-questionnaire: field of study, online course experience, prior knowledge of the topic and interest in it (1–7) |
| 1–14 | Participants study at their own pace. The team sends no reminders to either group; only the system's own notifications are active |
| 15 | Post-questionnaire (section 4.7). Optional 10-minute interview with 2–3 participants from each group |
| After the study | Debriefing: participants are told about the two groups; the control group can have gamification switched on |

### 4.7 Outcome metrics

| ID | Metric | Definition | Source | Groups |
|---|---|---|---|---|
| O1 | Course completion rate | Share of participants who completed the course (FR-LRN-08) by day 14 | Database | Both |
| O2 | Course progress | Percentage of completed course items on day 14 (FR-LRN-07); median per group | Database | Both |
| O3 | Active days | Number of different days in days 1–14 with at least one completed lesson or submitted test attempt, by the participant's local date (the same rule as FR-GAM-04) | Database | Both |
| O4 | Return in week 2 | Share of participants active in days 1–7 who are also active in days 8–14 | Database | Both |
| O5 | Learning results | Share of tests passed at the first attempt; average best test score | Database | Both |
| O6 | Usability | SUS score, 0–100 [V1] | Post-questionnaire | Both |
| O7 | Interest and enjoyment | Mean of the 7-item interest/enjoyment subscale of the Intrinsic Motivation Inventory, 1–7 [V4] | Post-questionnaire | Both |
| O8 | Felt pressure | Mean of the IMI pressure/tension subscale, 1–7 [V4]; and for the experimental group, 1–7 ratings of how much XP, the streak, achievements and the leaderboard motivated them and created pressure, with open comments | Post-questionnaire | Both / experimental |

The questionnaire items are translated into Russian by the team; the translation is checked by both team members.

### 4.8 Analysis and expected results

With 5–8 participants per group, statistical significance cannot be shown. Results are reported descriptively for each group: number of participants, median, minimum and maximum, or percentages, and the difference between the groups. Open answers are grouped by theme. The results are treated as indications, not as proof.

The expected results are fixed before the study, so that they are not adjusted to the data afterwards:

| ID | Expectation | Metrics |
|---|---|---|
| X1 | The experimental group has a higher completion rate, more progress, more active days and better return in week 2 than the control group | O1–O4 |
| X2 | Learning results in the experimental group are not lower than in the control group (gamification does not encourage rushing through tests) | O5 |
| X3 | The median SUS score is at least 68 in both groups | O6 |
| X4 | Interest and enjoyment are higher in the experimental group | O7 |
| X5 | Felt pressure in the experimental group does not exceed the scale midpoint (4) | O8 |

**How the aim is considered achieved:**

- The system part of the aim is achieved when the verification exit criteria are met (section 3.7), the end-to-end lifecycle scenarios pass (section 3.3) and X3 holds.
- H3 is considered supported in this study if X1, X2 and X4 hold. If they do not, this is reported as a result: gamification did not increase engagement in this setting. The answers to EQ2 explain why.

### 4.9 Threats to validity

| Threat | Mitigation |
|---|---|
| Small sample | Descriptive reporting only; no claims of statistical significance |
| Volunteers are more motivated than typical learners | Recorded in the limitations; random assignment keeps the groups comparable |
| Novelty effect: game elements are attractive at first, then the effect fades (literature review, Q3) | Two weeks instead of one; activity in week 2 is measured separately (O4) |
| Participants from different groups talk to each other | Participants are asked not to discuss the study until it ends |
| The team created the course and runs the study | The same briefing text, no reminders, metrics calculated automatically from the database |
| Questionnaires are translated | Both team members check the translation; the translated items are published with the results |
| Technical problems during the study | The system passes the end-to-end tests before the study; problems are logged and reported |

### 4.10 Ethics and data protection

- Participation is voluntary and can be stopped at any time; data of a participant who withdraws is deleted on request.
- No names, emails or other personal data are published or committed; participant accounts are referred to by codes.
- Raw questionnaire answers are stored outside the repository and deleted after the defense.
- The study does not affect participants' grades or any other obligations.

## 5. Schedule

The dates of milestones M2–M4 are not fixed yet (see [milestones](../10-project-management/milestones.md)). The order is:

| Activity | Timing |
|---|---|
| Unit and integration tests, CI | Continuously from the start of implementation |
| End-to-end and manual tests | For implemented features before pre-defense 2; all scenarios before the final pre-defense |
| Performance tests | After the core functionality and the gamification subsystem are implemented |
| Preparation of the study course and the questionnaires | Before the study; course content can be prepared in parallel with implementation |
| User study (2 weeks) | After deployment and passed end-to-end tests; finished at least 1 week before the final pre-defense, to leave time for analysis |
| Test report and evaluation report | Before the final pre-defense, in `docs/09-verification-plan/` |

## 6. Open points

- The administrator setting that hides gamification for the control group (section 4.3) is to be added to the functional requirements.
- The topic of the study course (section 4.5).
- The deployment environment for the study (architecture description, section 13).

## References

- [V1] Brooke, J. (1996). SUS: A "quick and dirty" usability scale. In P. Jordan, B. Thomas, & B. Weerdmeester (Eds.), *Usability evaluation in industry* (pp. 189–194). Taylor & Francis.
- [V2] Sauro, J., & Lewis, J. R. (2016). *Quantifying the user experience: Practical statistics for user research* (2nd ed.). Morgan Kaufmann.
- [V3] Lewis, J. R., & Sauro, J. (2018). Item benchmarks for the System Usability Scale. *Journal of Usability Studies, 13*(3), 158–167. https://uxpajournal.org/wp-content/uploads/sites/7/pdf/JUS_Lewis_May2018.pdf
- [V4] Center for Self-Determination Theory. *Intrinsic Motivation Inventory (IMI)*. https://selfdeterminationtheory.org/intrinsic-motivation-inventory/
