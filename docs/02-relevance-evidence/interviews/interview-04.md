## Interview 04

### Metadata

| Field | Value |
|---|---|
| Respondent | Respondent 04 |
| Date | 22.10.2026 |
| Interviewer | Adil |
| Format | Online call |
| Duration | 20 minutes |
| Consent obtained | Yes |
| Language | Russian |
| Notes in English | Answers were given in Russian. The interviewer recorded them in English with the help of an AI tool. Quotes are translations and may be shortened; they are not verbatim. |

### Respondent profile

| Field | Value |
|---|---|
| Group | Learner |
| Occupation | 3rd-year Software Engineering Student |
| Age range | 18–24 |
| Online course experience | Coursera, edX, Pluralsight. Started around 12 courses in the last two years and completed 10 of them (see A2). |

---

### A. Experience with online courses (learners)

| # | Question | Answer |
|---|---|---|
| A1 | Which online learning platforms have you used? For what purpose? | "I primarily use Coursera for multi-course Specializations (like Software Architecture and Cloud Computing), edX for university-level computer science fundamentals, and Pluralsight for specific backend frameworks." |
| A2 | How many online courses have you started in the last two years? How many did you finish? | "I've started around 12 courses and fully completed 10 of them. I have a very high completion rate because I carefully preview the syllabus and set a strict weekly study schedule before enrolling." |
| A3 | Think about the last course you did not finish. When and why did you stop? | "It was a legacy Java performance tuning course on an older platform. I stopped in the third week because the lab code repositories were outdated, half the dependencies failed to build, and the instructor abandoned the Q&A forum two years ago." |
| A4 | What usually makes you continue a course? What makes you stop? | "I continue when there is a structured learning path with automated code grading (like instant unit test feedback) and a well-maintained curriculum. I stop only if the practical assignments are broken or impossible to execute due to unmaintained platform environments." |
| A5 | How do you keep track of your progress in a course? Is it important to you to see it? | "I rely heavily on detailed progress bars and module percentages. Seeing '85% completed' gives me a strong psychological push to finish the remaining 15%, especially when I'm balancing university exams." |
| A6 | What do you like and dislike about the platforms you have used? | "I like platforms with automated CI/CD-style assignment checkers that evaluate code quality instantly. I dislike video fluff—instructors spending 10 minutes explaining something that could be summarized in a clean 2-paragraph documentation page." |
| A7 | Did a certificate influence your decision to start or finish a course? | "Yes, definitely. Verified certificates from recognized institutions or platform Specializations add tangible value to my LinkedIn profile and help when applying for software engineering internships." |

### C. Attitude to gamification

| # | Question | Answer |
|---|---|---|
| C1 | Have you used apps with points, levels, daily streaks, badges or leaderboards (e.g. Duolingo)? How did they affect you? | "I use LeetCode and HackerRank regularly for algorithmic practice. Their streak counters and problem-solving badges are quite effective at keeping me disciplined, especially during interview prep season." |
| C2 | Would points (XP) and levels for completed lessons and tests motivate you to continue a course? Why or why not? | "XP and levels are motivating if they reflect rigorous skill benchmarks. For example, gaining levels based on code efficiency, passing all unit tests, or solving complex algorithmic edge cases feels earned and rewarding." |
| C3 | A daily streak counts consecutive days of study. Would it motivate you or put pressure on you? What should happen if you miss a day? | "I like streaks, but they need flexibility. During midterms or exam weeks, I might not have time to log in for two days. A 'streak freeze' feature or weekend recovery option is essential so one missed day doesn't ruin weeks of momentum." |
| C4 | Would you like to see your position on a leaderboard? Weekly, all-time or both? How would you feel if you were far from the top? | "I would prefer cohort-based or class-based leaderboards. Competing against my university peers based on assignment scores or code execution speed is fun. A global leaderboard is less interesting because top spots are often dominated by bots or full-time users." |
| C5 | Which achievements (badges) would be meaningful to you? Which would seem useless? | "Meaningful: '100% Test Coverage', 'Zero Linter Errors', or 'Refactoring Master'. Useless: 'Logged in 3 days in a row' or 'Watched your first video'." |

### D. Closing

| # | Question | Answer |
|---|---|---|
| D1 | If you could change one thing in online learning platforms, what would it be? | "I would mandate instant, automated code evaluation with detailed static analysis. Instead of just passing or failing a test, the platform should give feedback on code style, complexity, and potential memory leaks." |
| D2 | Is there anything else you would like to add? | "For engineering students who are determined to finish courses, the key is tight feedback loops. If the platform makes testing code fast and seamless, completion rates will naturally go up." |

---

### Findings

| # | Observation (what the respondent said) | Related hypothesis / requirement | Interpretation |
|---|---|---|---|
| 1 | Started around 12 courses and completed 10; previews the syllabus and sets a weekly schedule before enrolling (A2) | H1 | Does not support H1 for this respondent |
| 2 | Stopped a Java course in week 3: outdated lab repositories, failing dependencies, and the instructor had abandoned the Q&A forum (A3) | H2, FR-LRN-10, FR-AUT-11 | The reason is outdated material and missing support, not loss of interest |
| 3 | Continues when there is a structured path with automated grading and instant feedback (A4) | FR-LRN-06 | Supports automatic grading of tests |
| 4 | Relies on progress bars; "85% completed" pushes the respondent to finish (A5) | FR-LRN-07 | Supports showing course progress |
| 5 | Verified certificates add value to LinkedIn and internship applications (A7) | FR-LRN-09 | Certificates motivate career-oriented learners |
| 6 | Streak counters and badges on coding practice sites keep the respondent disciplined (C1) | H3 | Supports H3 for this respondent |
| 7 | Likes streaks but needs flexibility: a "streak freeze" or weekend recovery (C3) | FR-GAM-04 | Supports a streak with a recovery option instead of a reset after one missed day |
| 8 | Prefers cohort- or class-based leaderboards; a global leaderboard is less interesting (C4) | FR-GAM-10, FR-GAM-12 | Candidate: leaderboard per course |
| 9 | "Logged in 3 days in a row" is useless; skill-based badges are meaningful (C5) | FR-GAM-08 | Our "7 days in a row" is close to the kind of badge this respondent calls useless, although our streak counts learning activity, not log-ins |

### Notable quotes

- "I stopped in the third week because the lab code repositories were outdated, half the dependencies failed to build, and the instructor abandoned the Q&A forum two years ago."
- "Seeing '85% completed' gives me a strong psychological push to finish the remaining 15%"
- "A 'streak freeze' feature or weekend recovery option is essential so one missed day doesn't ruin weeks of momentum."
- "I would prefer cohort-based or class-based leaderboards."
