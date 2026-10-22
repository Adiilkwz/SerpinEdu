# UX Prototype: Mockups of Key User Scenarios

**Project:** SerpinEdu — Development of a Management System of Educational Electronic Courses
**Task:** DIP-10
**Status:** Version 1 (pre-defense 1)

## 1. Purpose

This document shows how users will interact with SerpinEdu. It contains clickable high-fidelity mockups of the six key user scenarios, with each screen mapped to the functional requirements in [`../06-requirements/functional-requirements.md`](../06-requirements/functional-requirements.md).

Examples of the REST API behind these screens are in [`api-examples.md`](api-examples.md).

## 2. Prototype link and files

| Item | Location |
|---|---|
| Interactive prototype (all screens on one canvas, links between screens work) | https://claude.ai/artifact/PyrBdpPzXZaHgv8gVbCFnS |
| Static exports (PNG, 1440 px wide) | [`mockups/`](mockups/) |

## 3. Scope and conventions

- **Fidelity:** high-fidelity desktop mockups at 1440 px width. The responsive mobile layout (FR-UI-02, *Could*) is not designed yet.
- **Language:** screens are in English. Every header has the EN / RU switch (FR-UI-01). Russian versions of the screens are not drawn.
- **Sample data:** the sample student and author carry the names of the project team members. All other names, and all courses, numbers and dates, are invented sample data for the mockups. They are not real users or results.
- **Sample users:**

  | Role | Name in mockups |
  |---|---|
  | Student | Yerassyl Kuanyshov |
  | Author | Adil Ramazan |
  | Administrator | Administrator (AD) |

- **Timeline:** the screens follow one student's story, from buying the course on 22.10.2026 to finishing it on 15.11.2026. Then the author submits a new course for moderation on 16.11.2026.
- **Gamification values** follow FR-GAM-01 and FR-GAM-03. The XP shown in the headers is consistent across screens:

  | Moment | Screen | XP | Level |
  |---|---|---|---|
  | Before the first lesson | 2.3 My learning | 720 | 4 |
  | After lesson 1 (+10) | 3.1 Lesson | 730 | 4 |
  | After the Module 1 quiz (+20) | 3.2 Test result | 750 | 4 |
  | After the course: 11 more lessons (+110), 3 more tests (+60), course completed (+200) | 3.3, 4.1, 4.2 | 1,120 | 5 (reached at 1,000; level 6 at 1,500) |

## 4. Scenarios

| # | Scenario | Actor | Screens |
|---|---|---|---|
| 1 | Guest finds a course | Guest | 1.1 Home → 1.2 Catalog → 1.3 Course page |
| 2 | Student signs up, enrols and pays (test mode) | Guest → Student | 2.1 Sign up → 2.2 Checkout → 2.3 My learning |
| 3 | Student learns: lesson, test, certificate | Student | 3.1 Lesson → 3.2 Test result → 3.3 Course completed |
| 4 | Gamification: profile and leaderboard | Student | 4.1 Profile → 4.2 Leaderboard |
| 5 | Author creates a course | Author | 5.1 Author dashboard → 5.2 Course builder → 5.3 Test editor → submit |
| 6 | Administrator moderates | Administrator | 6.1 Moderation |

### Scenario 1 — Guest finds a course

1. **1.1 Home.** The guest sees the search field and three course collections: new, popular and top-rated.
2. **1.2 Catalog.** The guest searches by keyword and filters by category, level, price (free / paid), minimum rating and language.
3. **1.3 Course page.** The guest sees the description, syllabus (4 modules, 12 lessons, 4 tests), author, level, language, target audience, price, rating and reviews. The guest can open the preview lesson or report a review. **Buy course** leads to sign-up.

![1.1 Home](mockups/01-1-home.png)
![1.2 Catalog](mockups/01-2-catalog.png)
![1.3 Course page](mockups/01-3-course-page.png)

### Scenario 2 — Student signs up, enrols and pays (test mode)

1. **2.1 Sign up.** The guest enters name, email and password. The interface language and the time zone are preset; the time zone comes from the browser. A confirmation email is sent, and enrolment is possible only after the email is confirmed. The same screen has a **Log in** tab and a **Forgot password?** link.
2. **2.2 Checkout.** A banner says that payments are simulated. The student chooses the result of the test payment: success or failure.
3. **2.3 My learning.** After a successful payment the student sees a confirmation, their courses with progress, certificates and purchase history (including the failed attempt).

![2.1 Sign up](mockups/02-1-sign-up.png)
![2.2 Checkout](mockups/02-2-checkout.png)
![2.3 My learning](mockups/02-3-my-learning.png)

### Scenario 3 — Student learns: lesson, test, certificate

1. **3.1 Lesson.** Video player, course syllabus with progress, **+10 XP** feedback after the lesson is completed, and questions to the author under the lesson.
2. **3.2 Test result.** Score 80% (4 of 5) against a passing score of 70%, attempt 1 of 3, **+20 XP**, and a review of the answers.
3. **3.3 Course completed.** **+200 XP**, the new level (5), the unlocked achievement "Perfect test", a certificate preview (student name, course, author, date and unique number), PDF download, and a form to rate and review the course.

![3.1 Lesson](mockups/03-1-lesson.png)
![3.2 Test result](mockups/03-2-test-result.png)
![3.3 Course completed](mockups/03-3-course-completed.png)

### Scenario 4 — Gamification: profile and leaderboard

1. **4.1 Profile.** Level and XP progress to the next level, current and longest streak, a 4-week activity calendar, achievements with the dates they were earned, and this week's XP history.
2. **4.2 Leaderboard.** Weekly and all-time tabs. The weekly board starts every Monday at 00:00 in the platform time zone. It shows the top 50 with rank, name, level and XP. Equal XP gives a shared rank (1, 2, 2, 4). The student's own place (#14) is always shown.

![4.1 Profile](mockups/04-1-profile.png)
![4.2 Leaderboard](mockups/04-2-leaderboard.png)

### Scenario 5 — Author creates a course

1. **5.1 Author dashboard.** The author's courses with statuses (Published, Draft, Rejected with the moderator's comment), number of students and rating. Income for the month with the platform commission and net income (test mode). Students' questions waiting for an answer.
2. **5.2 Course builder.** Tabs Details / Content / Pricing. The course structure with modules and lessons (video, text or test), which can be reordered. The lesson editor, the preview-lesson option, and a checklist before **Submit for moderation**.
3. **5.3 Test editor.** Passing score, attempt limit (or unlimited attempts), and single-choice and multiple-choice questions with the correct answers marked.

![5.1 Author dashboard](mockups/05-1-author-dashboard.png)
![5.2 Course builder](mockups/05-2-course-builder.png)
![5.3 Test editor](mockups/05-3-test-editor.png)

### Scenario 6 — Administrator moderates

1. **6.1 Moderation.** Queue of courses pending review, course details, review checklist, a comment to the author, and **Approve and publish** / **Reject with comment**. The same screen shows a reported review (hide the review or dismiss the report) and the platform settings: commission, time zone of the weekly leaderboard and payment mode.

![6.1 Moderation](mockups/06-1-moderation.png)

## 5. Traceability: screens → functional requirements

| Screen | File | Requirements |
|---|---|---|
| 1.1 Home | `01-1-home.png` | FR-CAT-01, FR-CAT-02, FR-CAT-04, FR-UI-01 |
| 1.2 Catalog | `01-2-catalog.png` | FR-CAT-01, FR-CAT-02, FR-CAT-03 |
| 1.3 Course page | `01-3-course-page.png` | FR-CAT-05, FR-CAT-06, FR-LRN-13 |
| 2.1 Sign up | `02-1-sign-up.png` | FR-ACC-01, FR-ACC-02, FR-ACC-03, FR-ACC-04 (link), FR-ACC-06 (preset language and time zone) |
| 2.2 Checkout | `02-2-checkout.png` | FR-PAY-01, FR-LRN-02 |
| 2.3 My learning | `02-3-my-learning.png` | FR-LRN-07, FR-LRN-12, FR-PAY-02, FR-PAY-03 |
| 3.1 Lesson | `03-1-lesson.png` | FR-LRN-03, FR-LRN-04, FR-LRN-05, FR-LRN-07, FR-LRN-10, FR-GAM-01, FR-GAM-04 |
| 3.2 Test result | `03-2-test-result.png` | FR-LRN-06, FR-GAM-01 |
| 3.3 Course completed | `03-3-course-completed.png` | FR-LRN-08, FR-LRN-09, FR-LRN-11, FR-GAM-01, FR-GAM-03, FR-GAM-07, FR-GAM-08 |
| 4.1 Profile | `04-1-profile.png` | FR-ACC-07, FR-GAM-03, FR-GAM-04, FR-GAM-05, FR-GAM-09, FR-GAM-13 |
| 4.2 Leaderboard | `04-2-leaderboard.png` | FR-GAM-10, FR-GAM-11, FR-GAM-12 |
| 5.1 Author dashboard | `05-1-author-dashboard.png` | FR-AUT-07, FR-AUT-08, FR-AUT-10, FR-AUT-11, FR-PAY-04 |
| 5.2 Course builder | `05-2-course-builder.png` | FR-AUT-02, FR-AUT-03, FR-AUT-04, FR-AUT-06, FR-AUT-07 |
| 5.3 Test editor | `05-3-test-editor.png` | FR-AUT-05 |
| 6.1 Moderation | `06-1-moderation.png` | FR-ADM-01, FR-ADM-03, FR-ADM-05 |

### Requirements not covered by the mockups yet

| Requirement | Reason |
|---|---|
| FR-AUT-01, FR-ADM-02 (author applications) | Secondary flow; only the admin menu item is shown |
| FR-ADM-04 (categories), FR-ADM-06 (achievements) | Admin CRUD screens; only the menu items are shown |
| FR-AUT-09 (students' progress for the author) | Will be added to the author dashboard |
| FR-NOT-01, FR-NOT-02 (notifications) | Notification centre and emails are not drawn |
| FR-ACC-06 (editing the profile later) | Only the preset at sign-up is shown |
| FR-UI-02 (mobile layout) | *Could* priority; desktop only in version 1 |

## 6. Known simplifications

- **Next lesson** on 3.1 leads straight to the test result (3.2) to keep scenario 3 short.
- **Open course preview** on 6.1 opens the existing course page (1.3) as a stand-in for the course under review.
- **Download PDF** on 3.3 leads to My learning; the PDF itself is not drawn.
- Tabs and buttons without a separate screen (e.g. **All time** on 4.2, **Log in** on 2.1) link back to the same screen.

## 7. How to update

1. Edit the screens in the interactive prototype.
2. Export the changed screens again as PNG at 1440 px width into `mockups/`, keeping the file names.
3. Update the traceability table if the screen content changes.
