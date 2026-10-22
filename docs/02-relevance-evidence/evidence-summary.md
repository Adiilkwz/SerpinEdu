# Evidence Summary: User Interviews

**Project:** SerpinEdu — Development of a Management System of Educational Electronic Courses
**Task:** DIP-3
**Status:** Version 1 (pre-defense 1)

## 1. Purpose

The project proposal states four hypotheses (H1–H4) about the problem. The [literature review](../03-literature-review/literature-review.md) checked them against published research. This document checks them against first-hand evidence from five user interviews. It also lists findings that affect the requirements.

| ID | Hypothesis (from the proposal) |
|---|---|
| H1 | Many learners abandon online courses before completion |
| H2 | A common reason for abandoning courses is loss of interest |
| H3 | Gamification makes learning more interesting and motivates learners to continue |
| H4 | Learning on existing platforms (Coursera, Udemy) is perceived as monotonous |

## 2. Method

- **Instrument:** interviews based on the team's interview template. Section A covers learners (H1, H2, H4), section B covers course authors (H1, H4), section C covers attitudes to gamification (H3), and section D is the closing.
- **Respondents:** five people: four learners and one course author. They are referred to as R01–R05; no names or contacts are stored.
- **Language:** all interviews were conducted in Russian. The interviewers recorded the answers in English with the help of an AI tool. Quotes in this document are therefore translations and may be shortened; they are not verbatim.
- **Analysis:** answers were grouped by hypothesis and topic. Counts such as "3 of 4" are numbers of respondents, not percentages of a population.

| Respondent | Group | Occupation | Date | Interviewer | Format | File |
|---|---|---|---|---|---|---|
| R01 | Learner | 4th-year medical student | 21.10.2026 | Yerassyl | Online call, 20 min | [interview-01](interviews/interview-01.md) |
| R02 | Learner | 4th-year architecture student | 21.10.2026 | Adil | Online call, 18 min | [interview-02](interviews/interview-02.md) |
| R03 | Learner | 3rd-year economics and finance student | 22.10.2026 | Yerassyl | Online call, 20 min | [interview-03](interviews/interview-03.md) |
| R04 | Learner | 3rd-year software engineering student | 22.10.2026 | Adil | Online call, 20 min | [interview-04](interviews/interview-04.md) |
| R05 | Author | 4th-year computer science student, teaching assistant, author of a free Stepik course | 22.10.2026 | Adil | Written (messenger) | [interview-05](interviews/interview-05.md) |

All respondents are aged 18–24.

## 3. Results by hypothesis

### H1 — Many learners abandon online courses before completion

| Respondent | Courses started (2 years) | Courses finished | Comment |
|---|---|---|---|
| R01 | at least 15 | 2 | Usually watches one video on a topic and leaves |
| R02 | about 10 | 7 or 8 | Buys a course when a university project needs it |
| R03 | about 6 | 5 | Treats online courses like university modules |
| R04 | around 12 | 10 | Previews the syllabus and sets a weekly schedule first |

The author (R05) sees frequent drop-offs from the course side. Most happen at the move from basic syntax to harder topics, and "if a student gets stuck on a single coding task for more than 2 days, they almost always abandon the course."

**Interview result: mixed.** One of four learners (R01) finishes few courses. Three of four finish most of what they start, and they explain this by a concrete goal or a fixed schedule. The literature review already supports H1 (S1–S3). The interviews add that completion depends strongly on the learner's goal and planning.

### H2 — A common reason for abandoning courses is loss of interest

Reasons why each learner left the last unfinished course (A3), and the author's view (B4):

| Respondent | Reason | Type |
|---|---|---|
| R01 | Professor reading slides, no interactive cases | Loss of interest (passive format) |
| R02 | Long texts and multiple-choice questions, "like reading Wikipedia" | Loss of interest (text-only format) |
| R03 | Course turned out to be hype without theory or math | Low content quality |
| R04 | Outdated lab code, failing dependencies, instructor left the Q&A | Outdated material, no support |
| R05 (author) | Students get stuck on a difficult task | Difficulty, no help |

**Interview result: partially supported.** Loss of interest explains 2 of 4 cases, and both are linked to a passive, text- or slide-based format. The other reasons are content quality, outdated material, missing instructor support and getting stuck. No learner named lack of time as the reason for leaving the last course, although R01, R03 and R04 describe tight study schedules. In the literature, external time pressure is mentioned more often than loss of interest (S1, S3), so the interviews do not change the overall status.

### H3 — Gamification makes learning more interesting and motivates learners to continue

| Element | What respondents said | Count |
|---|---|---|
| Experience with gamification (C1) | Positive: R04 (streaks and badges on coding practice sites keep the respondent disciplined) and R05 (points give "a nice little dopamine hit"). Positive at first, then stressful: R01. Limited: R02 (works for 5-minute tasks), R03 (little use; can distract if too flashy) | 2 positive, 1 mixed, 2 limited |
| XP and levels (C2) | Plain XP is not motivating on its own for R01, R02 and R03. XP and levels motivate when they reflect real skill or progress (R01, R02, R03, R04). R05 likes seeing the score grow and sees points helping beginners through the early modules, less so in advanced topics | 3 of 5 say plain XP is not enough |
| Daily streak (C3) | All five see a streak that resets after one missed day as a problem. Alternatives: weekly goals (R01, R02, R03) or a "streak freeze" / weekend recovery (R04). R05: a healthy break should not destroy motivation | 5 of 5 |
| Leaderboard (C4) | Positive with conditions: R03 (weekly, by quiz scores), R04 (per class or cohort). Negative to a public leaderboard: R01 (anxiety), R02 (stress), R05 (intimidating for beginners; anonymous or opt-in only) | 2 positive, 3 negative |
| Achievements (C5) | All five value achievements for competence or accuracy and call activity- or login-based badges useless ("Early Bird", "Logged in on a weekend", "Logged in 3 days in a row") | 5 of 5 |
| Turning gamification off | R01 asks for a setting to turn it off; R03 and R05 warn against flashy or decorative game features | 1 asks, 2 cautious |

**Interview result: partially supported, with conditions.** Respondents accept gamification when it reflects real achievement and is flexible. Strict daily streaks (5 of 5) and forced public leaderboards (3 of 5) are seen as sources of pressure. This matches the literature review: gamification has positive average effects but also a novelty effect and possible negative effects (S3–S10).

### H4 — Learning on existing platforms is perceived as monotonous

- R01 and R02 describe the Coursera course they left as monotonous: slide reading, long texts, multiple-choice questions only.
- R03 and R04 report a mostly positive experience with Coursera and edX: they finish most courses and like clear grading and structured learning paths. Their complaints are specific: mandatory peer review (R03) and long videos that could be a short text (R04).
- Other complaints: outdated content (R02, R04), poor video quality (R02), weak Q&A and discussions (R04, R05).

**Interview result: partially supported.** 2 of 4 learners perceived a course as monotonous. They link monotony to the course format, not to the platform as a whole. The literature review did not confirm H4 directly (S11, S12). The interviews give first direct evidence, but only for some formats.

### Summary of hypothesis status

| ID | Literature review | Interviews | Combined status |
|---|---|---|---|
| H1 | Supported | Mixed: 1 of 4 learners finishes few courses; the author sees frequent drop-offs | Supported; completion depends on the learner's goal and planning |
| H2 | Partially supported | Partially supported: 2 of 4 cases are loss of interest | Partially supported |
| H3 | Partially supported | Partially supported, with conditions on how game elements are designed | Partially supported |
| H4 | Not directly confirmed | Partially supported: 2 of 4 learners | Partially supported for passive, text-based course formats |

## 4. Other findings

| Topic | Finding | Respondents |
|---|---|---|
| Progress display | Course progress in percent is important for R03 and R04. R01 and R02 prefer progress by topic or skill. R03 also wants a time estimate per module | R01–R04 |
| Certificates | Important for career-oriented learners (LinkedIn, CV, internships); irrelevant in fields where a portfolio or degree matters | Yes: R03, R04; no: R01, R02 |
| Practice and feedback | All respondents value practical tasks and quick feedback: interactive cases (R01), projects and visual feedback (R02), real datasets and auto-graded quizzes (R03), automated code grading (R04, R05) | R01–R05 |
| Course freshness | Outdated software versions or code made respondents stop | R02, R04 |
| Q&A and support | An abandoned Q&A forum was a reason to stop; better Q&A is the author's top wish | R04, R05 |
| Test settings (author) | Unlimited attempts help students learn from mistakes | R05 |
| Author analytics | The author needs to see which test questions most students fail | R05 |
| Interface quality | An outdated-looking interface lowers trust in the content | R02 |

## 5. Implications for the requirements

These are proposals for the team. They are not yet applied to [`functional-requirements.md`](../06-requirements/functional-requirements.md).

| # | Finding | Evidence | Proposal | Requirement |
|---|---|---|---|---|
| 1 | A streak that resets after one missed day is seen as punishing | R01–R05 | Keep the daily streak but add a recovery rule (e.g. a limited number of "freeze" days), or add weekly goals. The exact rule is for the team to decide | FR-GAM-04, FR-GAM-05 |
| 2 | Forced public leaderboards cause anxiety for some learners | R01, R02, R05 (R03, R04 positive) | Let a student hide themselves from public leaderboards while still seeing their own rank; consider a leaderboard per course | FR-GAM-12, new |
| 3 | Some learners want to learn without game elements | R01 (R03, R05 cautious) | New requirement: a student can hide gamification elements in the profile settings | New FR-GAM |
| 4 | Only competence-based achievements are valued | R01–R05 | Prefer result-based achievements such as "Perfect test"; review "7 days in a row". FR-GAM-06 already allows adding achievements without code changes | FR-GAM-08 |
| 5 | Authors need to see where students fail | R05 | Extend the author dashboard with the share of wrong answers per test question | FR-AUT-09 |
| 6 | Outdated content makes learners stop | R02, R04 | Show the date of the last course update on the course page | FR-CAT-05 |
| 7 | Already covered: unlimited attempts, automatic test grading, course progress, certificates, Q&A with the author | R03, R04, R05 | No change needed | FR-AUT-05, FR-LRN-06, FR-LRN-07, FR-LRN-09, FR-LRN-10, FR-AUT-11 |

## 6. Limitations

- **Small sample:** five respondents, four learners and one author. The results show tendencies, not statistically valid proportions.
- **Narrow profile:** all respondents are university students aged 18–24. Working adults, school students and experienced teachers are not represented. The only author is a student teaching assistant with one free course.
- **Completion bias:** three of four learners report high completion rates, so learners who often abandon courses are represented by one respondent (R01).
- **Self-reported numbers:** course counts are approximate and come from memory.
- **Translation:** the interviews were conducted in Russian and recorded in English with an AI tool. Quotes are translations and may be shortened.
- **Interviewer effect:** the interviewers are members of the project team.

## 7. Next steps

1. Decide on proposals 1–6 in section 5 and update the requirements.
2. Add the interview source code to the requirements (e.g. `I-R01` … `I-R05`) for the requirements affected by section 5.
3. Update the hypothesis statuses in the project proposal according to section 3.
