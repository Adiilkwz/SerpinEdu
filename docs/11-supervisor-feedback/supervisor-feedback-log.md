# Supervisor Feedback Log

**Project:** SerpinEdu — Development of a Management System of Educational Electronic Courses
**Supervisor:** Khaimuldin Askar
**Task:** DIP-13

This log records the supervisor's feedback on the key deliverables and the team's decisions on each comment. Every accepted comment is linked to the task or pull request that addresses it. Questions that the team wants to discuss at the next review are listed separately and are not feedback of the supervisor.

## 1. Reviews

| # | Date       | Format      | Participants                                       | Reviewed                                                                                                                                               |
| - | ---------- | ----------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1 | 21.10.2026 | Online call | Khaimuldin Askar, Yerassyl Kuanyshov, Adil Ramazan | YouTrack project, GitHub repository and its structure, documentation for pre-defense 1                                                                 |
| 2 | 22.10.2026 | Messenger   | Khaimuldin Askar, Yerassyl Kuanyshov, Adil Ramazan | Key decisions: architecture, evaluation plan, scope, technology stack, prototype. The wording was prepared by the team and confirmed by the supervisor |

### Review 1 — what was shown

1. **YouTrack project** — the agile board with the tasks of pre-defense 1.
2. **GitHub repository** — the repository and its folder structure.
3. **Documentation** — the deliverables for pre-defense 1, which the supervisor compared with the pre-defense criteria (section 3).

## 2. Feedback and decisions

| #   | Review | Deliverable                      | Feedback                                                                                                       | Decision | Action                                                                                                                                                                                                                                         | Status           |
| --- | ------ | -------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| F1  | 1      | YouTrack project                 | Every task created in YouTrack needs a description                                                             | Accepted | A description, expected outcome, acceptance criteria, deadline and links were added to tasks DIP-1 – DIP-20; the task format is now part of the rules in `CONTRIBUTING.md` (DIP-20) and `docs/10-project-management/youtrack.md` (DIP-19) | Done             |
| F2  | 1      | GitHub repository                | The supervisor reviewed the repository and was satisfied with it                                               | —       | No changes requested                                                                                                                                                                                                                           | Closed           |
| F3  | 1      | All documents                    | Checked that the students' full names and the project title are the same in all documents (section 4)          | —       | No changes requested                                                                                                                                                                                                                           | Closed           |
| F4  | 1      | Repository structure             | Checked the structure of the repository                                                                        | —       | No changes requested                                                                                                                                                                                                                           | Closed           |
| F5  | 1      | All documents                    | Compared the files with the pre-defense 1 criteria (section 3)                                                 | —       | No changes requested                                                                                                                                                                                                                           | Closed           |
| F6  | 1      | Git tags                         | Explained how to create tags in GitHub correctly                                                               | Accepted | The tag `prob-period-1` is created as explained, in DIP-15                                                                                                                                                                                   | Planned (DIP-15) |
| F7  | 1      | Use of AI tools                  | Limited use of AI tools for preparing the documentation is acceptable                                          | Accepted | Where AI tools affected the content, this is stated in the document (e.g. AI-assisted translation of the interview notes in `docs/02-relevance-evidence/interviews/`)                                                                        | Done             |
| F8  | 2      | Backend architecture             | Use Clean Architecture for the backend                                                                         | Accepted | ADR-0008 after pre-defense 1: Clean Architecture layers in the backend; the exact structure (layers inside modules or layers only) is decided in DIP-22                                                                                        | Planned (DIP-22) |
| F9  | 2      | Verification and evaluation plan | The baseline (the same system with gamification hidden, two groups, four weeks) is suitable for the comparison | —       | No changes requested                                                                                                                                                                                                                           | Closed           |
| F10 | 2      | Project proposal                 | The scope (section 7) is realistic for a team of two                                                           | —       | No changes requested                                                                                                                                                                                                                           | Closed           |
| F11 | 2      | Technology comparison            | The selected stack is approved: Go, PostgreSQL, REST with OpenAPI, React with Next.js                          | —       | No changes requested                                                                                                                                                                                                                           | Closed           |
| F12 | 2      | Prototype                        | The prototype covers the key scenarios of all roles: guest, student, author and administrator                  | —       | No changes requested                                                                                                                                                                                                                           | Closed           |

## 3. Pre-defense 1 criteria and where they are covered

| #  | Criterion                        | Location in the repository                                                                                                                             |
| -- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1  | Project proposal                 | [`docs/01-proposal/`](../01-proposal/project-proposal.md)                                                                                             |
| 2  | Evidence of relevance            | [`docs/02-relevance-evidence/`](../02-relevance-evidence/evidence-summary.md) — 5 interviews and the evidence summary                                |
| 3  | Literature review                | [`docs/03-literature-review/`](../03-literature-review/literature-review.md) — 12 sources and the analysis table                                     |
| 4  | Existing system comparison       | [`docs/04-existing-systems-comparison/`](../04-existing-systems-comparison/existing-systems-comparison.md) — 4 systems, 10 criteria                  |
| 5  | Technology comparison            | [`docs/05-technology-comparison/`](../05-technology-comparison/technology-comparison.md) — 5 decisions                                               |
| 6  | Requirements specification       | [`docs/06-requirements/`](../06-requirements/functional-requirements.md) — 64 functional and 29 non-functional requirements with acceptance criteria |
| 7  | Architecture and diagrams        | [`diagrams/`](../../diagrams/src/) and [`docs/07-architecture/`](../07-architecture/architecture-description.md)                                     |
| 8  | UX / prototype                   | [`docs/08-prototype/`](../08-prototype/prototype.md) — 15 mockups, the interactive prototype and API examples                                        |
| 9  | Verification and evaluation plan | [`docs/09-verification-plan/`](../09-verification-plan/verification-and-evaluation-plan.md)                                                           |
| 10 | Project management and risks     | [`docs/10-project-management/`](../10-project-management/milestones.md) and the YouTrack board                                                        |
| 11 | Supervisor feedback              | This log                                                                                                                                               |

## 4. Names and title used in the documents

| Item                     | Value used in the documents                                          |
| ------------------------ | -------------------------------------------------------------------- |
| Project title            | Development of a Management System of Educational Electronic Courses |
| Product name             | SerpinEdu                                                            |
| Team members             | Yerassyl Kuanyshov, Adil Ramazan                                     |
| Supervisor               | Khaimuldin Askar                                                     |
| University and programme | Astana IT University, Software Engineering                           |

## 5. Changes made by the team before the submission

In addition to the supervisor's feedback, the team checked all documents for consistency before the pre-defense 1 submission. The findings were fixed in separate tasks:

| Task   | Change                                                                                                                                |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------- |
| DIP-16 | Hypothesis statuses and scope in the project proposal updated                                                                         |
| DIP-17 | Outdated statements and open questions closed in the literature review, the existing systems comparison and the technology comparison |
| DIP-18 | User study extended to four weeks because of the novelty effect; prototype notes updated                                              |
| DIP-19 | Team, risks and dependencies updated                                                                                                  |
| DIP-20 | Squash merge documented; unused configuration file removed                                                                            |

## 6. Questions for the next review

These are the team's own open points. The team will ask the supervisor about them at the next review and record the answers in section 2.

| #  | Question                                                                                                                                                                                         | Related        |
| -- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------- |
| Q1 | The user study lasts four weeks and must start at least five weeks before the final pre-defense. Is this schedule realistic once the dates of pre-defense 2 and the final pre-defense are known? | DIP-11, DIP-18 |
| Q2 | Which environment should be used to deploy the system for the user study (university server or a cloud virtual machine)?                                                                         | R16            |

The questions on the backend architecture and on the baseline of the evaluation were answered in review 2 (F8, F9).

## 7. Next review

Before pre-defense 2. The date will be agreed with the supervisor.
