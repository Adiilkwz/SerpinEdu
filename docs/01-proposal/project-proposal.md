# Project Proposal

## 1. General information

| Item                  | Details                                                              |
| --------------------- | -------------------------------------------------------------------- |
| Project title         | Development of a Management System of Educational Electronic Courses |
| Product name          | SerpinEdu                                                            |
| Team members          | Yerassyl Kuanyshov, Adil Ramazan                                     |
| Supervisor            | Khaimuldin Askar                                                     |
| University            | Astana IT University                                                 |
| Educational programme | Software Engineering                                                 |

## 2. Problem statement

Many learners start online courses but abandon them before completion, often because the learning process does not keep them interested. Popular course platforms such as Coursera and Udemy present learning mostly as a sequence of videos and tests, which the team perceives as monotonous and not engaging enough.

The project proposes an open course marketplace where authors publish courses and learners study them, extended with gamification mechanics (experience points, levels, daily streaks, achievements and leaderboards). The underlying hypothesis is that gamification makes the learning process more interesting and motivates learners to continue their courses.

### Hypotheses and their status

The problem statement started from the team's observations. Each statement was then checked through the literature review, the user interviews and the existing systems comparison. The current status is:

| # | Statement | Status | Evidence |
|---|---|---|---|
| H1 | Many learners abandon online courses before completion | **Supported** — completion depends strongly on the learner's goal and planning | Literature review (S1–S3); interviews R01, R05 |
| H2 | A common reason for abandoning courses is loss of interest | **Partially supported** — loss of interest is one of the reasons, linked to passive, text- or slide-based formats; external time pressure is mentioned more often in the literature | Literature review (S1, S3); interviews R01, R02 |
| H3 | Gamification makes learning more interesting and motivates learners to continue | **Partially supported** — positive average effects, but variable, subject to the novelty effect and possible negative effects; respondents accept game elements that reflect real achievement | Literature review (S3–S10); interviews R01–R05 |
| H4 | Learning on existing platforms (Coursera, Udemy) is perceived as monotonous | **Partially supported** — for passive, text-based course formats, not for the platforms as a whole | Literature review (S11, S12); interviews R01–R04 |

Details are given in the [evidence summary](../02-relevance-evidence/evidence-summary.md) (section 3) and the [literature review](../03-literature-review/literature-review.md) (section 7). H3 is the central hypothesis of the project: it is evaluated with users according to the [verification and evaluation plan](../09-verification-plan/verification-and-evaluation-plan.md).

## 3. Target users

The platform is open to everyone. When creating a course, the author specifies its target audience (for example, an age group).

| Role          | Description                                                      |
| ------------- | ---------------------------------------------------------------- |
| Guest         | Unregistered visitor who browses the course catalogue            |
| Student       | Registered user who enrols in courses and studies them           |
| Author        | User who creates and publishes courses                           |
| Administrator | Platform operator who moderates content and manages the platform |

## 4. Aim

To develop a web-based open marketplace of educational electronic courses that supports the full course lifecycle — from course creation and moderation to learning and certification — and uses gamification to make learning more engaging.

## 5. Objectives

1. Analyse the problem through a literature review, user interviews and a comparison of existing platforms.
2. Compare technology alternatives and justify the selected technology stack.
3. Specify functional and non-functional requirements with acceptance criteria.
4. Design the system architecture and user interface prototypes.
5. Implement the core functionality of the platform: user accounts and roles, course catalogue, course builder, learning process, certificates, administration and notifications.
6. Implement the gamification subsystem: experience points, levels, daily streaks, achievements and leaderboards.
7. Test the system and evaluate it according to the verification and evaluation plan.

## 6. Expected outcomes

- A working web application with a backend written in Go.
- User interface in English and Russian.
- A gamification subsystem in which new achievements can be added through the database without changing the code.
- Project documentation: requirements, architecture and diagrams, test plan and evaluation results.

## 7. Scope

### In scope

**Users and access**

- Registration, login, email confirmation and password recovery.
- Roles: guest, student, author, administrator.
- User profile.

**Catalogue**

- Home page with course collections.
- Search and filters by category, level, price, rating and language.
- Course page: description, syllabus, author, reviews and a preview lesson.

**For authors**

- Course builder: course → modules → lessons (video, text, test).
- Target audience of the course (e.g. age group).
- Tests with answer options, passing score and number of attempts.
- Submitting a course for moderation.
- Author dashboard: own courses, students and their progress, statistics of test questions, income, answers to questions.

**Learning**

- Enrolment in free courses and payment for paid courses in test mode (simulated payments in USD, no real transactions); the platform keeps a commission set by the administrator.
- Lesson page with the embedded video player (videos are hosted on YouTube or Vimeo) and course progress.
- Questions on lessons, reviews with ratings.
- PDF certificate after course completion.
- Student dashboard: my courses, certificates, purchases.

**Administration**

- Course moderation, author applications, reports about content, categories.
- Achievements: creating, editing and deactivating them.
- Platform settings: commission percentage and the time zone of the weekly leaderboard.

**Notifications**

- Email and in-app notifications.

**Gamification**

- Experience points (XP) for learning activities, e.g. completed lessons, passed tests and completed courses.
- Levels reached at XP thresholds, shown in the profile and on the leaderboard.
- Daily streak of consecutive study days, calculated in the student's time zone.
- Achievements (badges) for events such as the first completed course, a 7-day streak or a test passed with 100%; conditions are stored in the database.
- Leaderboards: weekly (reset every Monday) and all-time; a student always sees their own position, even outside the top list.

### Optional (if time permits)

- Responsive layout for mobile browsers.

### Out of scope

- Native mobile applications.
- Real payment processing: payments work only in test mode.

## 8. Engineering complexity

Beyond standard data management, the project includes the following engineering challenges:

- **Time-zone-aware streaks.** Study days must be counted by each student's local date rather than by server time.
- **Data-driven achievements.** Achievement conditions are stored in the database and evaluated by a generic mechanism, so new achievements require no code changes.
- **Leaderboards.** Weekly rankings that reset every Monday and all-time rankings, where each student's position must be available even outside the top list.
- **Chained processing of learning events.** A single action, such as completing a lesson, affects progress, XP, levels, streaks, achievements and notifications.
- **Role-based access and moderation workflow** for four user roles.
- **Course content structure** with three lesson types, tests with attempt limits and passing scores, and automatic PDF certificate generation.
