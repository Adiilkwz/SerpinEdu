# Team and Responsibilities

## Team

| Member | Role | Areas of responsibility |
|---|---|---|
| **Yerassyl Kuanyshov** | Frontend developer, architect | Frontend (React + Next.js); authentication and authorization API; API testing; system architecture; architecture diagrams (together with Adil Ramazan) |
| **Adil Ramazan** | Backend developer | Database (PostgreSQL); backend development (Go); architecture diagrams (together with Yerassyl Kuanyshov) |
| **Khaimuldin Askar** | Supervisor | Reviews key deliverables and decisions; provides feedback at agreed checkpoints |

## Responsibilities by project area

| Area | Responsible | Reviewer |
|---|---|---|
| Frontend: pages, components, internationalisation (EN/RU) | Yerassyl Kuanyshov | Adil Ramazan |
| Authentication and authorization API | Yerassyl Kuanyshov | Adil Ramazan |
| API testing | Yerassyl Kuanyshov | Adil Ramazan |
| Database schema and migrations | Adil Ramazan | Yerassyl Kuanyshov |
| Backend modules (catalog, courses, learning, gamification, notifications, etc.) | Adil Ramazan | Yerassyl Kuanyshov |
| System architecture: architecture description and ADRs | Yerassyl Kuanyshov | Adil Ramazan |
| Architecture diagrams | Yerassyl Kuanyshov, Adil Ramazan | Each reviews the other's part |
| Project documentation | Assigned per task in YouTrack | The other team member |

## Completed tasks (pre-defense 1)

The assignee of each task in YouTrack is the same person who authored its commits and pull request.

| Task | Deliverable | Assignee |
|---|---|---|
| DIP-1 | Repository workflow (`.gitignore`, `.env.example`, PR template, contributing guide) | Yerassyl Kuanyshov |
| DIP-2 | Project proposal and scope | Yerassyl Kuanyshov |
| DIP-3 | User interviews and evidence summary (interviews conducted by both team members) | Adil Ramazan |
| DIP-4 | Literature review and sources analysis table | Yerassyl Kuanyshov |
| DIP-5 | Existing systems comparison | Adil Ramazan |
| DIP-6 | Technology comparison | Adil Ramazan |
| DIP-7 | Functional and non-functional requirements, acceptance criteria | Adil Ramazan |
| DIP-8 | Architecture diagrams (system context, use case, component); part of the diagrams was prepared by Adil Ramazan | Yerassyl Kuanyshov |
| DIP-9 | Architecture description and ADRs | Yerassyl Kuanyshov |
| DIP-10 | UI prototype and API examples | Yerassyl Kuanyshov |
| DIP-11 | Verification and evaluation plan | Adil Ramazan |
| DIP-12 | Team roles, milestones, risks and dependencies | Adil Ramazan |

Current assignees, priorities and deadlines of all tasks are maintained in [YouTrack](youtrack.md).

## Working rules

- Every meaningful work item is a YouTrack task with an assignee, a short description, expected outcome, acceptance criteria, deadline and links to the pull request and related materials.
- Each task is developed in its own branch named after the task ID (e.g. `DIP-7-requirements`).
- Each member commits from their own GitHub account with identifiable author details.
- Changes reach `main` only through a pull request reviewed and approved by the other team member.
- Pull requests are merged with **squash merge**; the PR title starts with the task ID and becomes the commit message in `main`. Merged branches are deleted.
- The supervisor reviews key deliverables before each pre-defense; feedback and decisions are recorded in [`docs/11-supervisor-feedback/`](../11-supervisor-feedback/).

See also [`CONTRIBUTING.md`](../../CONTRIBUTING.md).
