# Contributing

## Workflow

1. Every work item has a YouTrack task (`DIP-<number>`) with an assignee, a short description, expected outcome, acceptance criteria, deadline and links (pull request, related materials).
2. Create a branch from `main` named after the task:
   `DIP-<number>-<short-description>` (e.g. `DIP-12-project-proposal`).
3. Commit with the task ID as a prefix:
   `DIP-12: Add problem statement and target users`.
4. Open a Pull Request to `main` using the PR template. The PR title starts with the task ID (`DIP-12: Write project proposal`).
5. Another team member reviews and approves the PR before merging.
6. Merge with **squash merge**: the PR title becomes the single commit message in `main`. Delete the branch after merging.
7. Add the PR link to the YouTrack task and close the task only when its acceptance criteria are met.

## Rules

- `main` is the reviewed baseline. Direct pushes to `main` are not allowed.
- Each team member commits from their own account with identifiable author details.
- One commit = one coherent change with a descriptive message.
- Never commit secrets or personal data. Configuration is read from environment variables; `.env.example` contains only placeholder values.
- Interview notes must be anonymized (e.g. "Respondent 1, 3rd-year student").

## Pre-defense tags

Submitted versions are tagged `pre-defense-1`, `pre-defense-2` and `final-pre-defense`. Tags are never moved or replaced.
