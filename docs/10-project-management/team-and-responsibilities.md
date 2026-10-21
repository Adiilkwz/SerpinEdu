# Team and Responsibilities

## Team

| Member | Role | Areas of responsibility |
|---|---|---|
| **Yerassyl Kuanyshov** | Frontend developer | Frontend (React + Next.js); authentication and authorization API; API testing |
| **Adil Ramazan** | Backend developer, architect | Database (PostgreSQL); backend development (Go); system architecture |
| **Khaimuldin Askar** | Supervisor | Reviews key deliverables and decisions; provides feedback at agreed checkpoints |

## Responsibilities by project area

| Area | Responsible | Reviewer |
|---|---|---|
| Frontend: pages, components, internationalisation (EN/RU) | Yerassyl Kuanyshov | Adil Ramazan |
| Authentication and authorization API | Yerassyl Kuanyshov | Adil Ramazan |
| API testing | Yerassyl Kuanyshov | Adil Ramazan |
| Database schema and migrations | Adil Ramazan | Yerassyl Kuanyshov |
| Backend modules (catalog, courses, learning, gamification, notifications, etc.) | Adil Ramazan | Yerassyl Kuanyshov |
| System architecture and diagrams | Adil Ramazan | Yerassyl Kuanyshov |
| Project documentation | Assigned per task in YouTrack | The other team member |

## Completed tasks (pre-defense 1)

The assignee of each task in YouTrack is the same person who authored its commits and pull request.

| Task | Deliverable | Assignee |
|---|---|---|
| DIP-1 | Repository workflow (`.gitignore`, `.env.example`, PR template, contributing guide) | Yerassyl Kuanyshov |
| DIP-2 | Project proposal and scope | Yerassyl Kuanyshov |
| DIP-4 | Literature review and sources analysis table | Yerassyl Kuanyshov |
| DIP-5 | Existing systems comparison | Adil Ramazan |
| DIP-6 | Technology comparison | Adil Ramazan |

Current assignees, priorities and deadlines of all tasks are maintained in [YouTrack](youtrack.md).

## Working rules

- Every meaningful work item is a YouTrack task with an assignee, expected outcome, acceptance criteria and deadline.
- Each task is developed in its own branch named after the task ID (e.g. `DIP-7-requirements`).
- Each member commits from their own GitHub account with identifiable author details.
- Changes reach `main` only through a pull request reviewed and approved by the other team member.
- Pull requests are merged with **squash merge**; the PR title starts with the task ID and becomes the commit message in `main`. Merged branches are deleted.
- The supervisor reviews key deliverables before each pre-defense; feedback and decisions are recorded in [`docs/11-supervisor-feedback/`](../11-supervisor-feedback/).

See also [`CONTRIBUTING.md`](../../CONTRIBUTING.md).
