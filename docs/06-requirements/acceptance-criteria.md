# Acceptance Criteria

Acceptance criteria for every functional requirement in [functional-requirements.md](functional-requirements.md). A requirement is accepted when **all** its criteria are met. For non-functional requirements, the acceptance criterion is the target value and verification method stated in [non-functional-requirements.md](non-functional-requirements.md).

**Verification methods:** UT — unit test, IT — integration / API test, E2E — end-to-end test through the user interface, MT — manual test.

## Accounts and access (ACC)

| Requirement | Acceptance criteria | Verification |
|---|---|---|
| FR-ACC-01 (Must) | 1. Registration with valid name, email and password creates an account with the student role.<br>2. Registration with an email that is already registered is rejected with an error message.<br>3. A password shorter than 8 characters is rejected. | IT, E2E |
| FR-ACC-02 (Must) | 1. After registration a confirmation email with a link is sent.<br>2. Opening the link marks the email as confirmed.<br>3. A user with an unconfirmed email cannot enrol in a course and sees a message asking to confirm the email. | IT, E2E |
| FR-ACC-03 (Must) | 1. Login with correct credentials opens the user's dashboard.<br>2. Login with wrong credentials is rejected without saying which field is wrong.<br>3. After logout, protected pages are no longer accessible without logging in again. | IT, E2E |
| FR-ACC-04 (Should) | 1. A reset link is sent to a registered email.<br>2. The link allows setting a new password once and expires after 1 hour.<br>3. After the reset, the old password no longer works. | IT |
| FR-ACC-05 (Must) | 1. A guest can open only public pages (catalog, course pages, preview lessons, registration, login).<br>2. Author functions are available only to authors; administration functions only to administrators.<br>3. An attempt to perform a forbidden action is rejected (see NFR-SEC-03). | IT |
| FR-ACC-06 (Must) | 1. The user can change name, interface language and time zone; changes are saved.<br>2. After registration, the time zone equals the browser's time zone. | IT, E2E |
| FR-ACC-07 (Must) | 1. The profile shows the current level, total XP, current streak and earned achievements.<br>2. The values match the data used by the gamification module. | E2E |

## Catalog (CAT)

| Requirement | Acceptance criteria | Verification |
|---|---|---|
| FR-CAT-01 (Must) | 1. The catalog shows only courses with status Published.<br>2. The catalog is available without logging in. | IT, E2E |
| FR-CAT-02 (Must) | 1. Searching for a word contained in a course title or description returns that course.<br>2. A search with no matches shows an empty result message. | IT |
| FR-CAT-03 (Must) | 1. Each filter (category, level, price free/paid, minimum rating, language) returns only matching courses.<br>2. Several filters can be combined, and the result satisfies all of them. | IT |
| FR-CAT-04 (Should) | 1. The home page shows three collections: new, popular and top-rated courses.<br>2. Each collection contains only published courses ordered by its criterion. | IT, E2E |
| FR-CAT-05 (Must) | 1. The course page shows all fields listed in the requirement.<br>2. The syllabus lists all modules and lesson titles in their order. | E2E |
| FR-CAT-06 (Should) | 1. The preview lesson opens without enrolment and without logging in.<br>2. Other lessons of the course cannot be opened without enrolment. | IT, E2E |

## Course authoring (AUT)

| Requirement | Acceptance criteria | Verification |
|---|---|---|
| FR-AUT-01 (Must) | 1. A student can submit an author application.<br>2. After an administrator approves it, the user gets the author role and access to the course builder.<br>3. After rejection, the user stays a student and can see the decision. | IT, E2E |
| FR-AUT-02 (Must) | 1. An author can create a course with all listed fields; the course is saved with status Draft.<br>2. A course with price 0 is shown as free; a course with price > 0 is shown with its price in USD.<br>3. A course without a title or category cannot be saved. | IT, E2E |
| FR-AUT-03 (Must) | 1. The author can add, rename, delete and reorder modules and lessons.<br>2. The new order is shown in the course syllabus. | IT, E2E |
| FR-AUT-04 (Must) | 1. When creating a lesson, the author chooses video, text or test.<br>2. A video lesson contains a video, a text lesson contains formatted text, a test lesson contains a test. | IT |
| FR-AUT-05 (Must) | 1. The author can add questions with at least two answer options and mark one or several correct answers.<br>2. The author sets a passing score from 1 to 100% and an attempt limit (a number or unlimited).<br>3. A test without questions or without a correct answer in any question cannot be saved. | IT |
| FR-AUT-06 (Should) | 1. The author can mark one lesson as preview; marking another lesson removes the mark from the previous one. | IT |
| FR-AUT-07 (Must) | 1. Submitting a course changes its status from Draft to Pending review.<br>2. A course in Pending review cannot be edited by the author.<br>3. A rejected course shows the administrator's comment, can be edited and resubmitted.<br>4. A course appears in the catalog only after approval. | IT, E2E |
| FR-AUT-08 (Must) | 1. The dashboard lists all courses of the author with status and number of enrolled students.<br>2. Courses of other authors are not shown. | IT, E2E |
| FR-AUT-09 (Should) | 1. For each course the author sees the list of enrolled students and each student's progress percentage.<br>2. For each test of a course the author sees every question with the number of submitted attempts and the percentage of attempts in which the question was answered incorrectly.<br>3. Questions can be sorted by this percentage, highest first. | UT, IT |
| FR-AUT-10 (Should) | 1. For each course and in total, the dashboard shows sales amount, commission and net income.<br>2. Net income equals sales amount minus commission (FR-PAY-04). | UT, IT |
| FR-AUT-11 (Should) | 1. The dashboard lists unanswered questions from the author's courses.<br>2. An answer given by the author is shown under the question in the lesson. | IT, E2E |

## Learning (LRN)

| Requirement | Acceptance criteria | Verification |
|---|---|---|
| FR-LRN-01 (Must) | 1. A student with a confirmed email can enrol in a free course with one action.<br>2. After enrolment the course appears in the student's dashboard. | IT, E2E |
| FR-LRN-02 (Must) | 1. A paid course cannot be opened before a successful payment.<br>2. After a successful payment the student is enrolled automatically. | IT, E2E |
| FR-LRN-03 (Must) | 1. An enrolled student can open every lesson of the course.<br>2. A user who is not enrolled cannot open lessons, except the preview lesson.<br>3. The lesson page has links to the previous and next lessons. | IT, E2E |
| FR-LRN-04 (Must) | 1. A video lesson plays in the browser; play, pause and seek work. | MT |
| FR-LRN-05 (Must) | 1. The student can mark a video or text lesson as completed.<br>2. The lesson is shown as completed in the syllabus and progress is updated. | IT, E2E |
| FR-LRN-06 (Must) | 1. The score is calculated as the percentage of correctly answered questions.<br>2. The test is passed if the score is greater than or equal to the passing score.<br>3. When the attempt limit is reached, a new attempt cannot be started.<br>4. The result (score, passed / not passed, attempts left) is shown after each attempt. | UT, IT |
| FR-LRN-07 (Must) | 1. Progress equals completed lessons divided by all lessons of the course, shown as a percentage.<br>2. Progress is updated immediately after a lesson is completed or a test is passed. | UT, E2E |
| FR-LRN-08 (Must) | 1. A course is marked as completed exactly when all lessons are completed and all tests are passed.<br>2. A course with at least one unpassed test is not completed. | UT |
| FR-LRN-09 (Must) | 1. A PDF certificate is generated when the course is completed.<br>2. The certificate contains the student's name, course title, author, completion date and a unique number.<br>3. The certificate is available for download from the student dashboard. | IT, MT |
| FR-LRN-10 (Should) | 1. An enrolled student can post a question under a lesson.<br>2. When the author answers, the student receives a notification (FR-NOT-01). | IT, E2E |
| FR-LRN-11 (Should) | 1. Only an enrolled student can leave a review; one review per student per course.<br>2. A rating outside 1–5 is rejected.<br>3. The course rating equals the average of all ratings and is updated after each new or edited review. | UT, IT |
| FR-LRN-12 (Must) | 1. The dashboard lists all courses of the student with progress.<br>2. Certificates of completed courses can be downloaded from the dashboard. | E2E |
| FR-LRN-13 (Should) | 1. A logged-in user can report a course, review or question with a reason.<br>2. The report appears in the administrator's list (FR-ADM-03). | IT |

## Payments (PAY)

| Requirement | Acceptance criteria | Verification |
|---|---|---|
| FR-PAY-01 (Must) | 1. The checkout shows the course price in USD.<br>2. A simulated successful payment enrols the student; a simulated failed payment does not.<br>3. No external payment provider is called and no real money is charged. | IT, E2E |
| FR-PAY-02 (Must) | 1. Each payment attempt creates a purchase record with course, student, price, date and status (successful / failed). | IT |
| FR-PAY-03 (Should) | 1. The student sees a list of their purchases with course, price, date and status. | E2E |
| FR-PAY-04 (Should) | 1. For a successful purchase, commission = price × commission percentage; net income = price − commission.<br>2. Changing the commission percentage does not change previous purchases. | UT |

## Administration (ADM)

| Requirement | Acceptance criteria | Verification |
|---|---|---|
| FR-ADM-01 (Must) | 1. The administrator sees all courses with status Pending review.<br>2. Approving a course publishes it; rejecting requires a comment and returns the course to the author.<br>3. The author is notified of the decision. | IT, E2E |
| FR-ADM-02 (Must) | 1. The administrator sees pending author applications and can approve or reject each of them.<br>2. Approval gives the user the author role (FR-AUT-01). | IT |
| FR-ADM-03 (Should) | 1. The administrator sees open reports.<br>2. Hiding the reported content removes it from public pages; dismissing closes the report without changes. | IT |
| FR-ADM-04 (Must) | 1. The administrator can create, rename and delete categories.<br>2. A category that contains courses cannot be deleted. | IT |
| FR-ADM-05 (Should) | 1. The administrator can set the commission percentage (0–100%) and the leaderboard time zone.<br>2. New values apply to purchases and leaderboard weeks that start after the change. | IT |
| FR-ADM-06 (Should) | 1. The administrator can create an achievement by choosing an event type and condition parameters, without changing code.<br>2. A deactivated achievement is no longer awarded; already earned achievements remain in profiles. | IT, E2E |

## Notifications (NOT)

| Requirement | Acceptance criteria | Verification |
|---|---|---|
| FR-NOT-01 (Should) | 1. Each listed event creates an in-app notification for the right user.<br>2. The unread counter increases with each new notification and decreases when notifications are read. | IT, E2E |
| FR-NOT-02 (Should) | 1. Each listed event sends an email to the user's address (checked with a test mail server). | IT |

## Gamification (GAM)

| Requirement | Acceptance criteria | Verification |
|---|---|---|
| FR-GAM-01 (Must) | 1. Completing a lesson gives 10 XP, passing a test gives 20 XP, completing a course gives 200 XP.<br>2. The total XP shown in the profile equals the sum of all awards. | UT, IT |
| FR-GAM-02 (Must) | 1. Completing the same lesson again, passing the same test again or processing the same event twice does not give additional XP.<br>2. Every award is stored with student, source, amount and time. | UT, IT |
| FR-GAM-03 (Must) | 1. With 99 XP the level is 1, with 100 XP — 2, with 300 XP — 3, with 1,000 XP — 5.<br>2. The level is recalculated immediately after each award and shown in the profile and on leaderboards. | UT |
| FR-GAM-04 (Must) | 1. Activity on consecutive local days gives streaks of 1, 2, 3, …<br>2. Several activities on the same local day do not change the streak.<br>3. A day without activity resets the streak; the next activity starts a new streak of 1.<br>4. Activity at 23:30 local time and at 00:30 local time the next day counts as two consecutive days, regardless of the date in UTC. | UT |
| FR-GAM-05 (Should) | 1. The profile shows the current streak and the longest streak.<br>2. The longest streak is not reduced when the current streak is reset. | UT, E2E |
| FR-GAM-06 (Must) | 1. A new achievement added as a record in the database (event type + condition) is awarded to a student who meets the condition, with no code change or redeployment. | IT |
| FR-GAM-07 (Must) | 1. When a student meets an achievement condition, the achievement is awarded after the triggering event.<br>2. The same achievement is never awarded twice to the same student. | UT, IT |
| FR-GAM-08 (Must) | 1. Completing the first course awards "First course".<br>2. Reaching a 7-day streak awards "7 days in a row".<br>3. Passing a test with 100% awards "Perfect test". | IT |
| FR-GAM-09 (Must) | 1. Each earned achievement is shown in the profile with the date it was earned. | E2E |
| FR-GAM-10 (Must) | 1. The weekly leaderboard counts only XP earned since the last Monday 00:00 in the platform time zone.<br>2. At Monday 00:00 the weekly values start from zero; the all-time leaderboard is not affected. | UT, IT |
| FR-GAM-11 (Must) | 1. The all-time leaderboard ranks students by total XP in descending order. | IT |
| FR-GAM-12 (Must) | 1. Each leaderboard shows at most 50 entries with rank, name, level and XP.<br>2. A logged-in student outside the top 50 sees their own rank and XP below the list.<br>3. Students with equal XP have the same rank, and the next rank is skipped accordingly (e.g. 1, 2, 2, 4). | UT, IT, E2E |
| FR-GAM-13 (Could) | 1. The student sees a list of XP awards with date, source and amount. | E2E |

## User interface (UI)

| Requirement | Acceptance criteria | Verification |
|---|---|---|
| FR-UI-01 (Must) | 1. All interface texts are available in English and Russian.<br>2. Switching the language changes the interface texts without losing the current page; the choice is saved in the profile. | E2E |
| FR-UI-02 (Could) | 1. Catalog, course page, lesson page and profile are usable at a screen width of 375 px without horizontal scrolling. | MT |
