# Existing Systems Comparison

## 1. Purpose and method

This document compares the proposed system with four existing platforms to show which needs are already covered and where the gap is.

**Systems compared**

| System | Type | Why it was selected |
|---|---|---|
| Coursera | MOOC platform | One of the largest course platforms; named by the team as a reference |
| Udemy | Open course marketplace | Closest business model to the proposed system (any author can sell courses); named by the team as a reference |
| Stepik | Open course platform | Popular in the Russian-speaking region; any author can publish free and paid courses |
| Duolingo | Gamified learning app | Not a course platform, but the best-known example of gamification in education; used as a benchmark for game mechanics |

**Method.** Each criterion was checked against official sources: help centres, official blogs and platform pages. All sources were accessed on **20 October 2026**. Where possible, a screenshot of the source was saved in [`screenshots/`](screenshots/). References are given as [C1], [U1], [S1], [D1] and listed in section 5.

**Rating scale**

| Rating | Meaning |
|---|---|
| **Yes** | The feature is available to regular learners or authors and is documented in official sources |
| **Partial** | The feature exists in a limited form (e.g. only for business customers, or in a different form than the criterion describes) |
| **No** | The feature was not found in official documentation |
| **N/A** | The criterion does not apply to this type of platform |

"No" means that the feature was not found in official sources on the date of the check. It is not proof that the feature does not exist in the product.

## 2. Criteria

| # | Criterion | What is checked |
|---|---|---|
| 1 | Open publishing (marketplace) | Any author can publish and sell courses |
| 2 | Course structure and built-in tests | Courses are divided into parts; tests are part of the course |
| 3 | Course moderation before publishing | The platform reviews a course before it becomes publicly available |
| 4 | Pricing model | Free, paid, subscription |
| 5 | Certificates | Learners receive a certificate after completing a course |
| 6 | Learner interaction | Q&A or discussions, reviews and ratings |
| 7 | Points / XP and levels | Learners earn points for learning activities; levels based on points |
| 8 | Daily streaks | Counter of consecutive days with learning activity |
| 9 | Badges / achievements | Badges for learning events and milestones |
| 10 | Leaderboards | Rankings of learners by activity or points |

## 3. Comparison table

| # | Criterion | Coursera | Udemy | Stepik | Duolingo | Proposed system |
|---|---|---|---|---|---|---|
| 1 | Open publishing | **No** — content from 375+ partner universities and companies [C1] | **Yes** [U1] | **Yes** — unlimited free and paid courses [S2] | **No** — content created by Duolingo staff [D1] | **Yes** |
| 2 | Course structure and tests | **Yes** — modules, graded assignments, usually 80% to pass [C2] | **Yes** — quizzes, practice tests, coding exercises, assignments [U2] | **Yes** — modules → lessons → steps, 18 task types (choice, matching, code, SQL and others) [S3, S4] | **Yes** — lessons with exercises created by Duolingo; no authoring by users [D1, D2] | **Yes** — course → modules → lessons; tests with passing score and attempt limit |
| 3 | Moderation before publishing | **N/A** — no open publishing [C1] | **Yes** — every course must pass a Quality Review [U1] | *Partial* — no review described; catalog listing after 20 learners or first purchase; Stepik may refuse or remove [S5] | **N/A** [D1] | **Yes** — administrator moderation |
| 4 | Pricing model | Free preview + paid courses + subscription (Coursera Plus) [C3, C4] | Free + paid courses + subscription (Personal Plan) [U2, U4] | Free + paid courses [S2] | Free + subscription (Super Duolingo) [D2, D6] | Paid courses, test-mode payments in USD |
| 5 | Certificates | **Yes** — for paid learners [C2, C3] | **Yes** — for paid courses only [U3] | **Yes** — thresholds set by the instructor [S2, S6] | **No** | **Yes** — PDF certificate |
| 6 | Learner interaction | **Yes** — discussion forums, course ratings [C5, C6] | **Yes** — Q&A, reviews and ratings [U2, U5] | **Yes** — comments on every step, reviews and ratings [S5, S7] | *Partial* — community forums closed in 2022 [D7] | **Yes** — questions on lessons, reviews with ratings |
| 7 | Points / XP and levels | *Partial* — Skill Points (XP) per skill in 1,000+ courses; no levels found [C7] | **No** [U2] | *Partial* — knowledge points (1 per task) and reputation; no levels found [S8] | *Partial* — XP; no user levels found [D2, D4] | **Yes** — XP and levels |
| 8 | Daily streaks | *Partial* — **weekly** streaks, for enterprise learners [C8] | *Partial* — **weekly** streaks, Udemy Business Enterprise plan only [U6] | **Yes** — daily streaks and activity calendar; day starts at 00:00 UTC [S1, S9] | **Yes** — daily streak with Streak Freeze [D2, D3] | **Yes** — daily streak in the student's time zone |
| 9 | Badges / achievements | *Partial* — credential badges for completed learning paths only [C9] | **No** on the marketplace — badge hosting only in Udemy Business [U7] | **No** | **Yes** — achievements for milestones and personal records [D4] | **Yes** — configurable achievements stored in the database |
| 10 | Leaderboards | **No** for learners — a skill leaderboard exists only in admin dashboards [C10] | **No** [U2] | *Partial* — all-time top-20 by knowledge and by reputation [S8] | **Yes** — weekly leagues ranked by XP [D2, D5] | **Yes** — weekly and all-time; own position always visible |

## 4. Analysis by system

### Coursera
Coursera is not an open marketplace: courses come from more than 375 partner universities and companies [C1]. Courses are well structured, with graded assignments that usually require 80% to pass [C2]. Gamification is limited and fragmented: learners earn Skill Points (XP) towards skills in over 1,000 courses, but no levels were found [C7]; weekly (not daily) streaks were introduced in January 2026 for enterprise learners, earned by learning on at least three days or completing the learning plan in a week [C8]; badges are digital credentials for completed learning paths rather than achievements for learning events [C9]; a "Skill Mastery Leaderboard" exists only in administrator dashboards [C10].

### Udemy
Udemy is the closest to the proposed business model: authors publish and sell courses after a Quality Review that usually takes two business days [U1]. Courses support quizzes, practice tests, coding exercises, assignments, Q&A and reviews [U2]; certificates are issued only for paid courses [U3]. Gamification on the marketplace is practically absent: the official list of course features contains no points, badges or leaderboards [U2]. A weekly streak exists only for Udemy Business customers on the Enterprise plan [U6], and badge hosting is also a Udemy Business feature [U7].

### Stepik
Stepik allows authors to publish an unlimited number of free and paid courses [S2] and offers the richest set of task types among the compared systems [S4]. There is no described review of courses before publishing; a free course is added to the catalog after 20 learners, a paid one after the first purchase, and Stepik may refuse or remove a course [S5]. Gamification is partial: knowledge and reputation points with an all-time top-20 of learners [S8], and daily streaks shown in an activity calendar, where a day counts only if at least one new practice task is solved [S1, S9]. The day boundary is fixed at **00:00 UTC** [S9], so for a learner in Kazakhstan (UTC+5) a new "day" starts at 05:00 local time. No achievements or weekly leaderboards were found.

**Note on availability:** during the check (20 October 2026) the Stepik platform itself was unavailable due to an infrastructure incident; the status page states that courses, progress, certificates and streaks will be restored [S1]. All Stepik features were therefore verified through the Stepik Help Center, which remained available.

### Duolingo
Duolingo has the most complete gamification: XP, weekly leagues ranked by XP [D2, D5], a daily streak with Streak Freeze [D2, D3] and achievement badges for milestones and personal records [D4]. However, it is not a course platform: all content has been created by paid Duolingo staff since the volunteer contributor programme ended in 2021 [D1]. Its gamification design is relevant as a benchmark, but its model (no authors, no moderation, no course certificates) is different from the proposed system.

## 5. Conclusions

1. **No compared system combines an open course marketplace with a complete gamification layer.** Udemy and Stepik support open publishing but have little or no gamification for regular learners; Duolingo has complete gamification but no authors or courses from third parties; Coursera has neither open publishing nor complete gamification.
2. **Gamification in course platforms is fragmented.** Where it exists, it is limited to business customers (Udemy, Coursera), uses weekly instead of daily streaks (Udemy, Coursera), or lacks achievements and weekly rankings (Stepik).
3. **Time zones are not handled per learner in the documented streak mechanics.** Stepik counts days in UTC [S9]. The proposed system counts the streak in each student's own time zone.
4. **Data-driven achievements were not found** in any of the course platforms. The proposed system stores achievement conditions in the database so that new achievements can be added without changing the code.
5. **Moderation varies.** Only Udemy documents a review of every course before publishing [U1]; Stepik relies on catalog thresholds and complaints [S5]. The proposed system includes moderation by an administrator.

These findings support the need for the proposed system: an open course marketplace with moderation, combined with a full, configurable gamification subsystem (XP and levels, daily streaks in local time, data-driven achievements, weekly and all-time leaderboards). The comparison does not show whether learning on existing platforms is perceived as monotonous (hypothesis H4); this will be checked in the user interviews.

**Limitations of this comparison**
- Only official documentation was used; the logged-in learner experience was not tested on each platform.
- Platforms change quickly; results are valid for the date of the check.
- Stepik was unavailable during the check and was evaluated through its help center only.

## 6. References

All sources accessed on 20 October 2026.

**Coursera**
- [C1] Coursera. *About Coursera*. https://www.coursera.org/about
- [C2] Coursera Learner Help Center. *Taking assignments*. https://www.coursera.support/s/article/learner-000001563
- [C3] Coursera Learner Help Center. *How to preview a course*. https://www.coursera.support/s/article/learner-000002293
- [C4] Coursera Learner Help Center. *Coursera Plus*. https://www.coursera.support/s/article/learner-000001075
- [C5] Coursera Learner Help Center. *Get help with your courses in the discussion forums*. https://www.coursera.support/s/article/learner-000001210
- [C6] Coursera. Example course page showing learner rating and number of reviews (course offered by DeepLearning.AI and Stanford Online). https://www.coursera.org/learn/machine-learning
- [C7] Coursera Learner Help Center. *About Skills and Skill Points*. https://www.coursera.support/s/article/learner-000002436 — screenshot: `screenshots/coursera-skill-points.jpg`
- [C8] Coursera Admin Help Center. *Enterprise Platform Release Notes* (January 2026: "Build learner momentum with weekly streaks"). https://www.coursera.support/s/article/admin-000002192
- [C9] Coursera Learner Help Center. *About Coursera Badges*. https://www.coursera.support/s/article/learner-000002274 — screenshot: `screenshots/coursera-badges.jpg`
- [C10] Coursera Admin Help Center. *View top skills & growth*. https://www.coursera.support/s/article/admin-000002094

**Udemy**
- [U1] Udemy Help Center. *Udemy's Quality Review Process*. https://success.udemy.com/s/article/229605348 — screenshot: `screenshots/udemy-quality-review-process.jpg`
- [U2] Udemy Help Center. *Udemy Platforms and Features*. https://success.udemy.com/s/article/229233847 — screenshot: `screenshots/udemy-platform-features.jpg`
- [U3] Udemy Help Center. *How to download your certificate of completion (on a browser)*. https://success.udemy.com/s/article/229603868
- [U4] Udemy Teaching Center. *Accelerating learning with Personal Plan* (25 May 2022). https://teach.udemy.com/may-2022-personal-plan-update/
- [U5] Udemy Teaching Center. *Course Reviews FAQ*. https://teach.udemy.com/course-reviews-101/
- [U6] Udemy Business Support. *Streaks Frequently Asked Questions*. https://business-support.udemy.com/hc/en-us/articles/16943691866519-Streaks-Frequently-Asked-Questions
- [U7] Udemy (press release via Business Wire). *Udemy Expands Badging and Certification Preparation Offerings to Consumers on its Marketplace* (20 June 2024). https://www.businesswire.com/news/home/20240620039580/en/

**Stepik**
- [S1] Stepik. Status page "Stepik сейчас не работает. Мы его восстанавливаем" (update of 19 October 2026). https://stepik.org — screenshot: `screenshots/stepik-status-page-2026-10-19.jpg`
- [S2] Stepik Help Center. *Варианты публикации курсов* (Course publishing options). https://help.stepik.org/article/54722
- [S3] Stepik Help Center. *Структура курса* (Course structure). https://help.stepik.org/article/54734
- [S4] Stepik Help Center. *Виды практических задач* (Types of practice tasks). https://help.stepik.org/article/54741
- [S5] Stepik Help Center. *Нет курса в поиске и каталоге* (Course is not in search and catalog). https://help.stepik.org/article/54833
- [S6] Stepik Help Center. *Баллы и сертификаты* (Points and certificates). https://help.stepik.org/article/54735
- [S7] Stepik Help Center. *Общение с преподавателями и другими учащимися* (Communication with teachers and other learners). https://help.stepik.org/article/54714
- [S8] Stepik Help Center. *Знания и репутация* (Knowledge and reputation). https://help.stepik.org/article/54738 — screenshot: `screenshots/stepik-knowledge-reputation.jpg`
- [S9] Stepik Help Center. *Календарь активности* (Activity calendar). https://help.stepik.org/article/58828 — screenshot: `screenshots/stepik-activity-calendar.jpg`

**Duolingo**
- [D1] Duolingo Blog. *Ending & honoring our volunteer Contributor program* (10 March 2021). https://blog.duolingo.com/ending-honoring-our-volunteer-contributor-program-2/
- [D2] Duolingo Help Center (sections on streaks, leaderboards and Super Duolingo). https://www.duolingo.com/help — screenshots: `screenshots/duolingo-streak.jpg`, `screenshots/duolingo-leaderboards.jpg`
- [D3] Duolingo Blog. *The habit-building research behind your Duolingo streak* (31 January 2022). https://blog.duolingo.com/how-duolingo-streak-builds-habit
- [D4] Duolingo Blog. *Start earning brand-new Achievements on Duolingo!* (11 December 2023). https://blog.duolingo.com/achievement-badges
- [D5] Duolingo Blog. *How do Duolingo Leaderboards work?* (3 May 2023). https://blog.duolingo.com/duolingo-leagues-leaderboards/
- [D6] Duolingo Blog. *Why is Duolingo free?* (23 September 2024). https://blog.duolingo.com/is-duolingo-free/
- [D7] MetaFilter. *Duolingo forums shutting down March 22* (16 March 2022; links to the official announcement on forum.duolingo.com). https://metatalk.metafilter.com/26027/Duolingo-forums-shutting-down-March-22
