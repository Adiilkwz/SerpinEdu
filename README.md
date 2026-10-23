# SerpinEdu — Development of a Management System of Educational Electronic Courses

SerpinEdu is a web-based open marketplace of educational electronic courses. It supports the full course lifecycle — from course creation and moderation to learning and certification — and uses gamification (experience points, levels, daily streaks, achievements and leaderboards) to make learning more engaging.

Diploma project, Software Engineering, Astana IT University.

## Problem statement

Many learners start online courses but abandon them before completion, often because the learning process does not keep them interested. Popular course platforms such as Coursera and Udemy present learning mostly as a sequence of videos and tests, which the team perceives as monotonous and not engaging enough.

The project proposes an open course marketplace where authors publish courses and learners study them, extended with gamification mechanics (experience points, levels, daily streaks, achievements and leaderboards). The underlying hypothesis is that gamification makes the learning process more interesting and motivates learners to continue their courses.

The hypotheses and their current status are described in the [project proposal](docs/01-proposal/project-proposal.md) and the [evidence summary](docs/02-relevance-evidence/evidence-summary.md).

## Target users

| Role | Description |
|---|---|
| Guest | Unregistered visitor who browses the course catalogue |
| Student | Registered user who enrols in courses and studies them |
| Author | User who creates and publishes courses |
| Administrator | Platform operator who moderates content and manages the platform |

## Expected outcomes

- A working web application with a backend written in Go.
- User interface in English and Russian.
- A gamification subsystem in which new achievements can be added through the database without changing the code.
- Project documentation: requirements, architecture and diagrams, test plan and evaluation results.

## Team

| Member | GitHub | Role | Responsibilities |
|---|---|---|---|
| Yerassyl Kuanyshov | `yerassylkm` | Frontend developer, architect | Frontend (React + Next.js); authentication and authorization API; API testing; system architecture and diagrams |
| Adil Ramazan | `Adiilkwz` | Backend developer | Database (PostgreSQL); backend development (Go) |

**Supervisor:** Khaimuldin Askar

Details: [team and responsibilities](docs/10-project-management/team-and-responsibilities.md).

## Scope

**In scope**

- **Users and access:** registration, login, email confirmation, password recovery; roles guest, student, author and administrator; user profile.
- **Catalogue:** home page with course collections; search and filters by category, level, price, rating and language; course page with syllabus, author, reviews and a preview lesson.
- **For authors:** course builder (course → modules → lessons: video, text, test); tests with passing score and number of attempts; submitting a course for moderation; author dashboard with students, test question statistics, income and answers to questions.
- **Learning:** enrolment in free courses and payment for paid courses in test mode (simulated payments in USD); lesson page with the embedded YouTube or Vimeo player and course progress; questions on lessons; reviews with ratings; PDF certificate; student dashboard.
- **Administration:** course moderation, author applications, reports about content, categories, achievements, platform settings (commission, time zone of the weekly leaderboard).
- **Notifications:** email and in-app notifications.
- **Gamification:** experience points, levels, daily streaks in the student's time zone, achievements stored in the database, weekly and all-time leaderboards.

**Optional:** responsive layout for mobile browsers.

**Out of scope:** native mobile applications; real payment processing.

The full scope is in section 7 of the [project proposal](docs/01-proposal/project-proposal.md).

## Current status

**Pre-defense 1 (24.10.2026):** analysis, requirements, architecture, prototype and verification plan are completed. The application is not implemented yet. The milestones are described in [milestones](docs/10-project-management/milestones.md).

## Technologies

| Area | Technology | Decision |
|---|---|---|
| Backend | Go, modular monolith | [Technology comparison](docs/05-technology-comparison/technology-comparison.md), [ADR-0002](docs/07-architecture/adr/0002-modular-monolith.md) |
| Database | PostgreSQL | [Technology comparison](docs/05-technology-comparison/technology-comparison.md) |
| Frontend | React, Next.js, TypeScript | [Technology comparison](docs/05-technology-comparison/technology-comparison.md) |
| Frontend–backend interaction | REST API described with OpenAPI | [Technology comparison](docs/05-technology-comparison/technology-comparison.md) |
| Lesson videos | YouTube or Vimeo (embedded player) | [ADR-0004](docs/07-architecture/adr/0004-lesson-videos-on-youtube-or-vimeo.md) |
| File storage | MinIO (S3-compatible) | [ADR-0005](docs/07-architecture/adr/0005-object-storage-for-files.md) |
| Background jobs | Worker with a job table in PostgreSQL | [ADR-0006](docs/07-architecture/adr/0006-background-jobs-in-postgresql.md) |

## Links

**YouTrack project:** https://dp-project.youtrack.cloud/agiles/204-1/current

**Documentation**

| # | Document | Location |
|---|---|---|
| 1 | Project proposal | [docs/01-proposal](docs/01-proposal/project-proposal.md) |
| 2 | Evidence of relevance (user interviews) | [docs/02-relevance-evidence](docs/02-relevance-evidence/evidence-summary.md) |
| 3 | Literature review | [docs/03-literature-review](docs/03-literature-review/literature-review.md) |
| 4 | Existing systems comparison | [docs/04-existing-systems-comparison](docs/04-existing-systems-comparison/existing-systems-comparison.md) |
| 5 | Technology comparison | [docs/05-technology-comparison](docs/05-technology-comparison/technology-comparison.md) |
| 6 | Requirements and acceptance criteria | [docs/06-requirements](docs/06-requirements/functional-requirements.md) |
| 7 | Architecture description and decisions | [docs/07-architecture](docs/07-architecture/architecture-description.md) |
| 8 | Diagrams (PlantUML sources and PNG exports) | [diagrams](diagrams/src/) |
| 9 | Prototype and API examples | [docs/08-prototype](docs/08-prototype/prototype.md) |
| 10 | Verification and evaluation plan | [docs/09-verification-plan](docs/09-verification-plan/verification-and-evaluation-plan.md) |
| 11 | Team, milestones, risks and dependencies | [docs/10-project-management](docs/10-project-management/milestones.md) |
| 12 | Supervisor feedback | [docs/11-supervisor-feedback](docs/11-supervisor-feedback/supervisor-feedback-log.md) |
| 13 | Pre-defense submissions | [docs/pre-defense](docs/pre-defense/pre-defense-1.md) |

## Repository structure

```
.
├── backend/                 Go backend
│   ├── cmd/                 programs: api, worker
│   ├── internal/            modules (auth, catalog, course, gamification, …) and platform code
│   ├── migrations/          database migrations
│   ├── api/openapi.yaml     REST API specification
│   └── tests/integration/   integration tests
├── frontend/                Next.js web application
├── diagrams/
│   ├── src/                 PlantUML sources
│   └── exports/             PNG exports
├── docs/                    project documentation (01–11) and pre-defense summaries
├── tests/                   end-to-end tests, load tests, test data
├── .github/                 pull request template
├── .env.example             configuration example with placeholder values
└── CONTRIBUTING.md          contribution rules
```

## How we work

Every work item is a YouTrack task (`DIP-<number>`). Each task is developed in its own branch named after the task ID, committed with the task ID as a prefix and merged into `main` through a pull request that the other team member reviews. Pull requests are merged with squash merge. Details are in [CONTRIBUTING.md](CONTRIBUTING.md).

## Setup, run and test

Setup, run and test instructions will be added as soon as runnable code is available.
