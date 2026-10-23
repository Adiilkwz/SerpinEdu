# YouTrack Project

**Agile board:** https://dp-project.youtrack.cloud/agiles/204-1/current
**Task ID prefix:** `DIP`

## Task rules

Every meaningful work item is created as a YouTrack task. Each task contains:

- **Assignee** — the team member responsible for the task;
- **Description** — a short explanation of what the task is about and why it is needed;
- **Priority**;
- **Due date**;
- **Expected outcome** — what will be produced;
- **Acceptance criteria** — conditions that must be met before the task is closed;
- **Links** — the pull request and related materials (e.g. the prototype or the Miro board).

A task is marked as done only when its acceptance criteria are met.

## Traceability between YouTrack and GitHub

| Item | Format | Example |
|---|---|---|
| Task | `DIP-<number> – <title>` | DIP-7 – Write functional and non-functional requirements |
| Branch | `DIP-<number>-<short-description>` | `DIP-7-requirements` |
| Commit | `DIP-<number>: <description>` | `DIP-7: Add functional requirements` |
| Pull request title | `DIP-<number>: <title>` | `DIP-7: Write requirements` |
| Link back | The pull request link is added as a comment in the YouTrack task | — |

Pull requests are merged with squash merge, so the PR title becomes the commit message in `main`, and each task can be traced from YouTrack to its pull request and commit.

## Dependencies

Dependencies between tasks are recorded in YouTrack as "depends on" links. The dependency map is described in [risks-and-dependencies.md](risks-and-dependencies.md#2-dependencies).
