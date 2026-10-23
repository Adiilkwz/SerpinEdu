# Literature Review

## 1. Introduction

The project is based on the assumption that many learners abandon online courses because the learning process does not keep them interested, and that gamification can make learning more engaging (see hypotheses H1–H4 in the [project proposal](../01-proposal/project-proposal.md)). This review examines what recent research says about these assumptions. It is organised around four questions:

- **Q1.** Why do learners abandon online courses? (H1, H2)
- **Q2.** Does gamification improve learning, motivation and engagement? (H3)
- **Q3.** What is known about specific game elements — points, badges, leaderboards and streaks — and their negative effects? (H3, design of the gamification subsystem)
- **Q4.** How do learners perceive existing online course platforms? (H4)

The structured analysis of each source is given in the [sources analysis table](sources-analysis-table.md).

## 2. Review method

**Inclusion criteria:**
- peer-reviewed journal article or systematic review;
- published in 2021–2026;
- full text freely available (open access or a free preprint of the published version);
- written in English;
- directly related to one of the questions Q1–Q4.

**Search.** Sources were searched in academic web search and open-access databases and publisher websites (DOAJ, PubMed Central, arXiv, MDPI, Frontiers, SpringerOpen, SAGE) using combinations of the keywords *gamification*, *meta-analysis*, *MOOC*, *dropout*, *completion*, *engagement*, *leaderboard*, *badges*, *streaks*, *negative effects* and *learner satisfaction*.

**Screening.** An initial list of 21 candidate sources (18 scientific and 3 industry sources) was screened against the criteria. Six scientific sources published before 2021 and all industry sources were excluded. One systematic review was excluded because its full text is not freely available (Wang et al., 2023), and one working paper on streaks was excluded because it is not peer-reviewed (Aulagnon et al., 2024). Two further sources on dropout were added through a targeted search to strengthen Q1. The final set consists of **12 peer-reviewed sources**: two systematic reviews, two meta-analyses, one systematic mapping study, six empirical studies and one design study.

**Analysis.** For each source, the aim, method, sample, key findings and limitations were extracted from the full text. Inconsistencies found in the sources themselves were recorded and are discussed below.

## 3. Why learners abandon online courses (Q1)

Dropout from MOOCs is a well-documented problem. Uygun et al. (2026), summarising earlier empirical studies, note that 85–95% of MOOC participants may leave before completing a course. In their own GELMOOC dataset, 2,660 of 2,957 enrollees did not complete the course. Even in university-run programming MOOCs with relatively high completion, Rõõm et al. (2021) found that completion fell from 60.5% in a short introductory course to 34.0% in a longer and more demanding one.

**When learners leave.** Dropout is concentrated at the beginning of a course. Rõõm et al. (2021) found that dropout was highest in the first one or two weeks in all four analysed course runs, with a second peak in one course when a final project started. Huang et al. (2023) similarly describe engagement as developing in start, middle and end stages and list activity in the first weeks among the behavioural predictors of dropout.

**Why learners leave.** The systematic review by Huang et al. (2023) groups dropout factors into five categories: course attributes, social status, cognitive ability, emotional factors (including motivation and self-regulation) and learning behaviour. This shows that dropout has several causes rather than one. The qualitative study by Uygun et al. (2026), based on the accounts of 117 learners who had left a MOOC, adds an important nuance: the most frequently mentioned reasons were **external** — professional workload, lack of time and academic workload. Declining motivation was also reported, but less often: learners described initial enthusiasm that faded, and one learner explicitly said that they lost interest because there was "no feeling of progress or achievement". Course-related problems such as content that was too easy or too difficult, limited interaction and doubts about the value of the certificate also played a role.

**Critical assessment.** The evidence for Q1 comes from different types of studies that complement each other: a systematic review (Huang et al., 2023), log-data analysis (Rõõm et al., 2021) and learners' own explanations (Uygun et al., 2026). However, each has limitations. Rõõm et al. (2021) inferred the reasons for dropout from activity data rather than measuring them, and their completion rates are much higher than usually reported for MOOCs without an explanation. Uygun et al. (2026) relied on a single course and a 4.4% response rate, so more motivated learners may be over-represented.

## 4. Effect of gamification on learning and motivation (Q2)

Recent meta-analyses report positive average effects of gamification. Li et al. (2023), analysing 41 studies with more than 5,000 participants, found a large overall effect (g = 0.82). Gyedu et al. (2026), focusing on higher education, reported a large effect on motivation and deep learning (d = 1.12). In the MOOC context, the systematic review by Wahyudi et al. (2025) found that most of the 22 reviewed studies reported gains in engagement, motivation and retention, mainly through badges, leaderboards, points, progress bars and challenges.

These results must be interpreted with caution:

- **Effects on engagement are smaller than effects on performance.** In Li et al. (2023) the effect on academic performance (g = 1.02) was much larger than on engagement (g = 0.38), and the estimate for motivation was based on only three studies with a confidence interval crossing zero. Gyedu et al. (2026) also found smaller effects for engagement than for performance and deep learning. For this project, engagement and course continuation are the main goals, so the most relevant effects are the weakest ones.
- **Online settings show smaller effects.** Li et al. (2023) report g = 0.34 for online environments compared with g = 0.86 for hybrid ones; Gyedu et al. (2026) found offline delivery more effective than online. The results for hybrid learning differ between the two meta-analyses (larger than online in Li et al., the weakest format in Gyedu et al.), which shows that the moderators are not yet well understood.
- **Heterogeneity is very high.** Both meta-analyses report I² above 90%, meaning that results vary strongly between studies and depend on the design and context.
- **Methodological weaknesses.** Li et al. (2023) report different numbers of studies in the abstract and results and describe a moderator with p = 0.015 as non-significant. Gyedu et al. (2026) state a 2015–2024 search range but include a study from 2011, and report possible publication bias.
- **Gamification is not always the driver.** Wahyudi et al. (2025) note that in several MOOC studies gamification was not a critical factor for engagement or completion, and they report no effect sizes.

Overall, the literature supports the idea that gamification *can* improve engagement, but the effect in online courses is moderate, varies strongly and depends on design.

## 5. Game elements and their negative effects (Q3)

**Negative effects.** The systematic mapping by Almeida et al. (2023), covering 87 papers, shows that the elements most often linked to negative effects are badges, leaderboards and competition, followed by points. The most frequent negative effects were lack of effect, worsened performance and demotivation; gaming the system and cheating were also common. The authors conclude that game elements are "not silver bullets": learners with different preferences react to them differently.

**The novelty effect.** Rodrigues et al. (2022) followed 756 students over 14 weeks. The positive effect of gamification began to decline after about four weeks and then partially recovered between weeks six and ten, without returning to its initial level. The authors warn that studies shorter than about 12 weeks may give unreliable results and suggest adapting game elements when the effect starts to drop.

**Leaderboards.** Park and Kim (2021) explain that a single global leaderboard can leave low-ranked learners with repeated experiences of failure, which reduces motivation, and that newcomers may find leaderboards stressful. They propose combining macro (whole-course) and micro (activity-level) leaderboards to give more learners a chance to succeed. These principles were derived from literature and existing systems and have not yet been tested with learners.

**Badges.** In a quasi-experimental study, Uanhoro and Young (2022) found that badges led students to submit homework about 1.8 days earlier and to space their practice more, but had little effect on exam results; few students earned higher-level badges. This suggests that badges influence behaviour more than learning outcomes. Because students chose their course sections themselves, the causal conclusions are limited.

**Streaks.** No peer-reviewed study on daily streaks in online courses that met the inclusion criteria was found. The only experimental study identified was a working paper measuring weekly streaks among primary-school pupils, which was excluded. At the same time, learners in Uygun et al. (2026) asked to be able to pause and resume a course without penalty, which is relevant to how strictly a daily streak should reset.

## 6. Learners' perception of existing platforms (Q4)

Chen et al. (2022) analysed more than 186,000 sentences from MOOC reviews and found that learners mainly discuss course quality; they are generally satisfied with instructors but dissatisfied with the learning process. Nguyen (2022) found low satisfaction with Coursera courses among 120 students (mean 2.39 out of 6), with assessment and the speed of support rated lowest; students criticised peer grading and limited interaction with teachers.

These studies confirm that learners are dissatisfied with some aspects of existing platforms, but they do not directly confirm the team's view that learning on these platforms is monotonous. The evidence is also limited: Chen et al. (2022) used reviews from a single aggregator, and Nguyen (2022) studied one specialisation at one university and reports some inconsistent statistics.

## 7. Synthesis: status of the hypotheses

| # | Hypothesis | Status after the review | Evidence |
|---|---|---|---|
| H1 | Many learners abandon online courses before completion | **Supported** | S1, S2, S3 |
| H2 | A common reason for abandoning courses is loss of interest | **Partially supported** — motivation is one of the factors, but external time pressure is mentioned more often | S1, S3 |
| H3 | Gamification makes learning more interesting and motivates learners to continue | **Partially supported** — positive average effects, but smaller for engagement and online settings, highly variable, subject to the novelty effect and possible negative effects | S3–S10 |
| H4 | Learning on existing platforms is perceived as monotonous | **Not directly confirmed** — learners are dissatisfied with the learning process, assessment and support, but monotony itself was not measured | S11, S12 |

The user interviews add first-hand evidence for all four hypotheses. The combined status after the review and the interviews is given in the [evidence summary](../02-relevance-evidence/evidence-summary.md), section 3.

## 8. Implications for the project

The review leads to the following considerations, which the project takes into account:

1. **Gamification is not a guaranteed solution.** The project treats the effect of gamification on engagement as a hypothesis to be evaluated, not as a given result (S4–S6).
2. **The beginning of a course matters most.** Since dropout is highest in the first weeks (S2, S3), early activity should be visible and rewarded, for example through progress tracking and XP for the first completed lessons.
3. **Progress must be visible.** Learners who left a course explicitly asked for progress indicators, milestones and badges (S3).
4. **Risks of competition.** Leaderboards and badges are the elements most often associated with negative effects (S7, S9). The weekly leaderboard, which resets every Monday, gives learners a recurring chance to rank higher, and showing each student's own position avoids a view in which only the top learners are visible. These choices are consistent with the principle of maximising success experiences (S9), but their effect has not been tested.
5. **Preventing gaming the system.** Since cheating and gaming the system are frequent negative effects (S7), XP rules should not allow earning XP repeatedly for the same activity.
6. **Long enough evaluation.** Because of the novelty effect (S8), a short evaluation may overestimate or underestimate the effect of gamification. The user study in the [verification and evaluation plan](../09-verification-plan/verification-and-evaluation-plan.md) therefore lasts four weeks and reports activity per week.

**Open questions for the requirements and the team's decisions:**
- How strict should the daily streak be? Learners' requests for pausing without penalty (S3) suggest considering a mechanism that protects the streak during short breaks. **Decision:** the user interviews raised the same point, but the team kept the strict daily streak for version 1 (FR-GAM-04); the pressure it creates is measured in the user study (evaluation question EQ2).
- Should leaderboards include smaller groups (e.g. per course) in addition to weekly and all-time rankings (S9)? **Decision:** not included in version 1; the weekly and all-time leaderboards are kept (FR-GAM-10 – FR-GAM-12), and their effect is measured in the user study (EQ2).

The reasons for these decisions are given in the [evidence summary](../02-relevance-evidence/evidence-summary.md), section 5.

## 9. Research gaps and limitations of the review

**Gaps in the literature:**
- Few studies examine gamification in open course marketplaces; most evidence comes from formal education or university-run MOOCs.
- Long-term effects of gamification on course completion remain under-studied (S6, S8).
- No peer-reviewed evidence on daily streaks in online courses was found within the inclusion criteria.

**Limitations of this review:**
- Only open-access, English-language sources from 2021–2026 were included, so relevant paywalled studies and earlier foundational works are not covered.
- The search was not a full systematic review: it did not cover all academic databases, and the number of screened records was not recorded.
- Several included studies have small samples or rely on a single course or institution.

## References

Almeida, C., Kalinowski, M., Uchôa, A., & Feijó, B. (2023). Negative effects of gamification in education software: Systematic mapping and practitioner perceptions. *Information and Software Technology, 156*, 107142. https://doi.org/10.1016/j.infsof.2022.107142

Chen, X., Wang, F. L., Cheng, G., Chow, M.-K., & Xie, H. (2022). Understanding learners' perception of MOOCs based on review data analysis using deep learning and sentiment analysis. *Future Internet, 14*(8), 218. https://doi.org/10.3390/fi14080218

Gyedu, F. O., Partey, P. A., Boafo, F. A., & Agbo, D. D. (2026). Gamification effect: Enhancing student learning outcomes in higher education: A meta-analysis and policy implications. *SAGE Open*. https://doi.org/10.1177/21582440261421375

Huang, H., Jew, L., & Qi, D. (2023). Take a MOOC and then drop: A systematic review of MOOC engagement pattern and dropout factor. *Heliyon, 9*(4), e15220. https://doi.org/10.1016/j.heliyon.2023.e15220

Li, M., Ma, S., & Shi, Y. (2023). Examining the effectiveness of gamification as a tool promoting teaching and learning in educational settings: A meta-analysis. *Frontiers in Psychology, 14*, 1253549. https://doi.org/10.3389/fpsyg.2023.1253549

Nguyen, L. Q. (2022). Learners' satisfaction of courses on Coursera as a massive open online course platform: A case study. *Frontiers in Education, 7*. https://doi.org/10.3389/feduc.2022.1086170

Park, S., & Kim, S. (2021). Leaderboard design principles to enhance learning and motivation in a gamified educational environment: Development study. *JMIR Serious Games, 9*(2), e14746. https://doi.org/10.2196/14746

Rodrigues, L., Pereira, F. D., Toda, A. M., Palomino, P. T., Pessoa, M., Carvalho, L. S. G., Fernandes, D., Oliveira, E. H. T., Cristea, A., & Isotani, S. (2022). Gamification suffers from the novelty effect but benefits from the familiarization effect: Findings from a longitudinal study. *International Journal of Educational Technology in Higher Education, 19*, 13. https://doi.org/10.1186/s41239-021-00314-6

Rõõm, M., Lepp, M., & Luik, P. (2021). Dropout time and learners' performance in computer programming MOOCs. *Education Sciences, 11*(10), 643. https://doi.org/10.3390/educsci11100643

Uanhoro, J., & Young, S. S.-C. (2022). Investigation of the effect of badges in the online homework system for undergraduate general physics course. *Education Sciences, 12*(3), 217. https://doi.org/10.3390/educsci12030217

Uygun, E., Cesur, K., Karahan, P., & Mikhailova, T. (2026). Participant perspectives on dropout factors and course enhancement needs in a general English MOOC. *Discover Education, 5*, 109. https://doi.org/10.1007/s44217-026-01126-4

Wahyudi, M. N. A., Budiyanto, C. W., Widiastuti, I., & Pambudi, N. A. (2025). Beyond points and badges: Deepening engagement in MOOCs through gamification. *International Journal of Interactive Mobile Technologies, 19*(1), 18–33. https://doi.org/10.3991/ijim.v19i01.51705
