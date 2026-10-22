## Interview 05

### Metadata

| Field | Value |
|---|---|
| Respondent | Respondent 05 |
| Date | 22.10.2026 |
| Interviewer | Adil |
| Format | Written (messenger) |
| Duration | 15 minutes (asynchronous) |
| Consent obtained | Yes |
| Language | Russian |
| Notes in English | Answers were given in Russian. The interviewer recorded them in English with the help of an AI tool. Quotes are translations and may be shortened; they are not verbatim. |

### Respondent profile

| Field | Value |
|---|---|
| Group | Author |
| Occupation | 4th-year Computer Science Student, Teaching Assistant, and online course author |
| Age range | 18–24 |
| Online course experience | Created a free introductory programming course on Stepik, acts as a TA for university algorithms classes on Moodle. |

---

### B. Experience as a course author or teacher (authors)

| # | Question | Answer |
|---|---|---|
| B1 | On which platforms have you published or taught courses? | "I published a free crash course on programming fundamentals on Stepik. I also work as a Teaching Assistant (TA) at my university, so I regularly manage assignments and grade students on our Moodle platform." |
| B2 | What is difficult when creating a course: structure, tests, video, publishing? | "Creating engaging practical tasks is definitely the hardest part. On Stepik, it's writing good auto-grading tests for the code. If the test cases are too strict or check for specific print formatting instead of logic, students get frustrated. If they are too loose, they pass without actually understanding the concept." |
| B3 | How do you check what learners have understood? Which test settings do you need (passing score, attempts)? | "I rely heavily on automated coding exercises rather than multiple-choice questions. For code, the passing score is basically 100% (it either compiles and gives the right output or it doesn't). However, I allow unlimited attempts. I want them to debug and learn from their mistakes, not fail and give up." |
| B4 | What do you notice about learners who stop a course? At which point do they usually stop? | "Most drop-offs happen right when the course transitions from basic syntax (like 'if' statements and 'for' loops) to abstract concepts like Object-Oriented Programming or recursion. If a student gets stuck on a single coding task for more than 2 days, they almost always abandon the course." |
| B5 | Which information about students and income would you like to see in an author dashboard? | "Since my course is free, I don't track income. But for students, I desperately need a 'failure heatmap'. If 80% of students are failing Test Case #3 on a specific problem, I need the dashboard to flag this so I can rewrite my explanation or fix the task description." |

### C. Attitude to gamification

| # | Question | Answer |
|---|---|---|
| C1 | Have you used apps with points, levels, daily streaks, badges or leaderboards (e.g. Duolingo)? How did they affect you? | "I use Anki with gamification add-ons for my own studies, and Stepik has a built-in points system for solving tasks. It gives a nice little dopamine hit when you see the green checkmark and points added, but it doesn't replace good educational content." |
| C2 | Would points (XP) and levels for completed lessons and tests motivate you to continue a course? Why or why not? | "As a learner, I like seeing my total score grow. As a creator, I see it helps keep beginners motivated through the boring early modules. But for advanced topics, points matter less than the ability to build a working project at the end." |
| C3 | A daily streak counts consecutive days of study. Would it motivate you or put pressure on you? What should happen if you miss a day? | "Streaks are a double-edged sword. They are great for language learning, but terrible for programming. Sometimes a student needs to step away from a bug for a couple of days to clear their head. Breaking their streak because they took a healthy break might demotivate them permanently." |
| C4 | Would you like to see your position on a leaderboard? Weekly, all-time or both? How would you feel if you were far from the top? | "Anonymous or opt-in leaderboards are okay. Forced public leaderboards can be very intimidating for beginners who are already struggling. A weekly leaderboard for 'Most active helper in the Q&A comments' would be much more beneficial for the community than 'Fastest to solve'." |
| C5 | Which achievements (badges) would be meaningful to you? Which would seem useless? | "Meaningful badges: 'Community Helper' (for answering other students' questions) or 'Optimal Code' (for solving a task with high memory/time efficiency). Useless badges: 'Read the syllabus', 'Logged in on a Friday'." |

### D. Closing

| # | Question | Answer |
|---|---|---|
| D1 | If you could change one thing in online learning platforms, what would it be? | "I would drastically improve the comment and Q&A sections. Learning is social. Right now, on most platforms, discussions are a mess. I want a system where students can easily link a specific line of their broken code in the forum so mentors and peers can help them instantly." |
| D2 | Is there anything else you would like to add? | "Don't build features just to make the platform look modern or game-like. Focus on the feedback loop. The faster a student gets meaningful feedback on their mistake (whether from an auto-grader or a mentor), the less likely they are to drop out." |

---

### Findings

| # | Observation (what the respondent said) | Related hypothesis / requirement | Interpretation |
|---|---|---|---|
| 1 | The hardest part of creating a course is writing good auto-graded tasks: too strict frustrates students, too loose lets them pass without understanding (B2) | FR-AUT-05 | Test quality is a key problem for authors |
| 2 | Allows unlimited attempts so that students learn from mistakes (B3) | FR-AUT-05 | Supports the "unlimited attempts" option |
| 3 | Most drop-offs happen at the move from basic syntax to OOP or recursion; a student stuck on one task for more than 2 days almost always abandons the course (B4) | H1, H2 | Supports H1 from the author's side; the reason is difficulty and getting stuck, not boredom |
| 4 | Needs a "failure heatmap": which test case most students fail (B5) | FR-AUT-09 | Candidate: per-question failure rate in the author dashboard |
| 5 | The course is free, so income is not tracked (B5) | FR-AUT-10 | The income section is not relevant for authors of free courses |
| 6 | Points help beginners get through the early modules; they matter less for advanced topics (C2) | H3, FR-GAM-01 | Partial support for XP, mainly for beginners |
| 7 | Streaks are "terrible for programming": breaking a streak after a healthy break may demotivate a student permanently (C3) | FR-GAM-04 | A streak that resets after one missed day may harm learners who need breaks |
| 8 | Anonymous or opt-in leaderboards are acceptable; forced public ones intimidate beginners; suggests a weekly "most active helper" board (C4) | FR-GAM-10, FR-GAM-12 | Candidate: students can hide themselves from public leaderboards |
| 9 | Wants better Q&A where students can point to a specific line of code; suggests a "Community Helper" badge (C5, D1) | FR-LRN-10, FR-GAM-08 | Q&A quality matters to keep learners going |
| 10 | Advises against features that only make the platform look game-like; fast feedback matters most (D2) | H3 | Gamification should support feedback, not replace it |

### Notable quotes

- "If a student gets stuck on a single coding task for more than 2 days, they almost always abandon the course."
- "I desperately need a 'failure heatmap'."
- "Forced public leaderboards can be very intimidating for beginners who are already struggling."
- "Don't build features just to make the platform look modern or game-like."
