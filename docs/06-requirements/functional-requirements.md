# Functional Requirements

## 1. Conventions

**Priority (MoSCoW)**

| Priority | Meaning |
|---|---|
| **Must** | Required to achieve the project aim (full course lifecycle + gamification). The system is not accepted without it |
| **Should** | Important, but the system can be demonstrated without it |
| **Could** | Implemented only if time permits |

**Source** shows where a requirement comes from:

| Code | Source |
|---|---|
| P | Project scope — [project proposal](../01-proposal/project-proposal.md), section 7 |
| P-EC | Engineering complexity — project proposal, section 8 |
| L-Sn | Literature review — source Sn in the [sources analysis table](../03-literature-review/sources-analysis-table.md) |
| C-xn | Existing systems comparison — reference xn in the [comparison](../04-existing-systems-comparison/existing-systems-comparison.md) |
| I-Rnn | User interview with respondent Rnn — see the [evidence summary](../02-relevance-evidence/evidence-summary.md) |

Acceptance criteria for every requirement are given in [acceptance-criteria.md](acceptance-criteria.md). Non-functional requirements are in [non-functional-requirements.md](non-functional-requirements.md).

**Roles:** Guest (not registered), Student, Author, Administrator.

## 2. Accounts and access (ACC)

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-ACC-01 | A guest can register with name, email and password | Must | P |
| FR-ACC-02 | The system sends an email confirmation link; until the email is confirmed, the user cannot enrol in courses | Must | P |
| FR-ACC-03 | A registered user can log in and log out | Must | P |
| FR-ACC-04 | A user can reset a forgotten password through a link sent by email | Should | P |
| FR-ACC-05 | The system supports four roles — guest, student, author, administrator — and allows each action only to the roles permitted for it | Must | P |
| FR-ACC-06 | A user can edit their profile: name, interface language and time zone; the time zone is preset from the browser at registration | Must | P, P-EC |
| FR-ACC-07 | The profile shows the user's level, total XP, current streak and earned achievements | Must | P |

## 3. Catalog (CAT)

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-CAT-01 | Any visitor, including a guest, can browse the catalog of published courses | Must | P |
| FR-CAT-02 | A visitor can search courses by keywords in the title and description | Must | P |
| FR-CAT-03 | A visitor can filter courses by category, level, price (free / paid), minimum rating and course language | Must | P |
| FR-CAT-04 | The home page shows course collections: new courses, popular courses (by number of students) and top-rated courses | Should | P |
| FR-CAT-05 | The course page shows the description, syllabus (modules and lesson titles), author, level, language, target audience, price, average rating and reviews | Must | P |
| FR-CAT-06 | A visitor can open the preview lesson of a course without enrolling | Should | P |

## 4. Course authoring (AUT)

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-AUT-01 | A student can apply to become an author; after approval by an administrator the user receives the author role | Must | P |
| FR-AUT-02 | An author can create a course with title, description, category, level, course language, target audience (e.g. age group), cover image and price; price 0 means a free course | Must | P |
| FR-AUT-03 | An author can add, edit, delete and reorder modules and lessons within a course | Must | P |
| FR-AUT-04 | A lesson has one of three types: video, text or test. A video lesson contains a link to a video on YouTube or Vimeo | Must | P |
| FR-AUT-05 | An author can create a test with questions, answer options (one or several correct), a passing score (percentage) and an attempt limit (or unlimited attempts) | Must | P, I-R05 |
| FR-AUT-06 | An author can mark one lesson of a course as a preview lesson | Should | P |
| FR-AUT-07 | An author can submit a course for moderation. Course statuses: Draft → Pending review → Published or Rejected; a rejected course can be edited and resubmitted | Must | P, C-U1 |
| FR-AUT-08 | The author dashboard lists the author's courses with their status and number of students | Must | P |
| FR-AUT-09 | The author dashboard shows the students of each course and their progress, and for each test question the percentage of submitted attempts in which it was answered incorrectly | Should | P, I-R05 |
| FR-AUT-10 | The author dashboard shows income per course and in total: sales amount, platform commission and net income | Should | P |
| FR-AUT-11 | The author dashboard lists students' questions and lets the author answer them | Should | P, I-R04, I-R05 |

## 5. Learning (LRN)

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-LRN-01 | A student can enrol in a free course without payment | Must | P |
| FR-LRN-02 | A student can enrol in a paid course only after a successful payment (FR-PAY-01) | Must | P |
| FR-LRN-03 | An enrolled student can open lessons of the course; the lesson page shows the content by lesson type and links to the previous and next lessons | Must | P |
| FR-LRN-04 | Video lessons are played in the YouTube or Vimeo player embedded in the lesson page, with play, pause and seek | Must | P |
| FR-LRN-05 | A student can mark a video or text lesson as completed | Must | P |
| FR-LRN-06 | A student can take a test: the score is calculated automatically, the test is passed if the score reaches the passing score, and the number of attempts is limited by the test settings | Must | P, I-R03, I-R04 |
| FR-LRN-07 | The system shows course progress as the percentage of completed lessons | Must | P, L-S3, I-R03, I-R04 |
| FR-LRN-08 | A course is completed when all its lessons are completed and all its tests are passed | Must | P |
| FR-LRN-09 | When a course is completed, the system generates a PDF certificate with the student's name, course title, author, completion date and a unique certificate number | Must | P, I-R03, I-R04 |
| FR-LRN-10 | An enrolled student can ask a question under a lesson; the student is notified when the question is answered | Should | P, I-R04, I-R05 |
| FR-LRN-11 | An enrolled student can leave one review per course with a rating from 1 to 5 and optional text, and edit it later; the course rating is the average of all ratings | Should | P |
| FR-LRN-12 | The student dashboard shows the student's courses with progress and their certificates available for download | Must | P |
| FR-LRN-13 | A user can report a course, review or question as inappropriate | Should | P |

## 6. Payments (PAY)

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-PAY-01 | Payment for a paid course works in test mode: the payment is simulated, can succeed or fail, and no real money is charged; prices are in USD | Must | P |
| FR-PAY-02 | Each payment is recorded as a purchase with course, student, price, date and status | Must | P |
| FR-PAY-03 | The student dashboard shows the student's purchase history | Should | P |
| FR-PAY-04 | For each successful purchase the system calculates the platform commission using the commission percentage valid at the time of purchase, and the author's net income | Should | P |

## 7. Administration (ADM)

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-ADM-01 | An administrator can review courses pending moderation and approve or reject them with a comment | Must | P, C-U1 |
| FR-ADM-02 | An administrator can approve or reject applications to become an author | Must | P |
| FR-ADM-03 | An administrator can review reports and resolve them by hiding the reported content or dismissing the report | Should | P |
| FR-ADM-04 | An administrator can create, edit and delete course categories | Must | P |
| FR-ADM-05 | An administrator can change platform settings: platform commission percentage and the time zone used for the weekly leaderboard | Should | P |
| FR-ADM-06 | An administrator can create, edit and deactivate achievements through the administration interface | Should | P |

## 8. Notifications (NOT)

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-NOT-01 | Users receive in-app notifications with an unread counter for: moderation result (author), author application result, answer to a question, achievement earned, new level, certificate issued | Should | P |
| FR-NOT-02 | Users receive email notifications for: email confirmation, password reset, moderation result (author) and successful purchase | Should | P |

Email confirmation itself is required by FR-ACC-02 (Must).

## 9. Gamification (GAM)

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-GAM-01 | A student earns XP for learning activities: lesson completed — 10 XP; test passed — 20 XP; course completed — 200 XP | Must | P, L-S3 |
| FR-GAM-02 | XP for the same activity is awarded only once (e.g. a test passed again gives no additional XP); every award is recorded with its source and time | Must | P-EC, L-S7 |
| FR-GAM-03 | A student's level is determined by total XP. Level *n* is reached at 50 · *n* · (*n* − 1) XP: level 1 — 0, level 2 — 100, level 3 — 300, level 4 — 600, level 5 — 1,000 XP, etc. The level is shown in the profile and on leaderboards | Must | P |
| FR-GAM-04 | The system counts a daily streak — the number of consecutive days with at least one qualifying activity (completed lesson or submitted test attempt). Days are counted by the calendar date in the student's own time zone: activity on the day after the last active day increases the streak by 1, more activity on the same day does not change it, and a missed day resets it | Must | P, P-EC, C-S9 |
| FR-GAM-05 | The profile shows the current streak and the longest streak achieved | Should | P, L-S3 |
| FR-GAM-06 | Achievements are stored in the database as rules (triggering event and condition). New achievements can be added without changing the code | Must | P, P-EC |
| FR-GAM-07 | After each relevant event the system evaluates the achievement rules and awards each achievement to a student at most once | Must | P, P-EC |
| FR-GAM-08 | The initial set of achievements contains: "First course" (first course completed), "7 days in a row" (streak of 7 days) and "Perfect test" (test passed with 100%) | Must | P |
| FR-GAM-09 | Earned achievements are shown in the student's profile with the date they were earned | Must | P |
| FR-GAM-10 | The weekly leaderboard ranks students by XP earned since Monday 00:00 in the platform time zone and starts again every Monday | Must | P, C-D5, I-R03 |
| FR-GAM-11 | The all-time leaderboard ranks students by total XP | Must | P |
| FR-GAM-12 | Each leaderboard shows the top 50 students with rank, name, level and XP; a logged-in student always sees their own rank and XP, even outside the top 50. Students with equal XP share the same rank | Must | P, L-S9 |
| FR-GAM-13 | A student can view the history of their XP awards | Could | P |

## 10. User interface (UI)

| ID | Requirement | Priority | Source |
|---|---|---|---|
| FR-UI-01 | The user interface is available in English and Russian; the user can switch the language | Must | P |
| FR-UI-02 | The interface adapts to mobile browsers (screen width from 375 px) | Could | P |

## 11. Out of scope (Won't)

- Native mobile applications.
- Real payment processing and payouts to authors.

## 12. Summary

| Priority | Number of requirements |
|---|---|
| Must | 44 |
| Should | 18 |
| Could | 2 |
| **Total** | **64** |
