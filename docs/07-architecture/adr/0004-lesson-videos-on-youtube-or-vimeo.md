# ADR-0004: Host lesson videos on YouTube or Vimeo

- **Status:** Accepted
- **Date:** 22.10.2026

## Context

Video lessons need storage, streaming and a player (FR-LRN-04). The way of delivering video was left open in the technology comparison and recorded as risk R11. Alternatives were: an S3-compatible object storage with temporary links, the server's disk, and links to videos on YouTube or Vimeo.

## Decision

An author uploads a lesson video to YouTube or Vimeo and adds its link to the lesson. The system stores only the link and shows the hosting's player embedded in the lesson page. The API returns the link only to users who have access to the lesson: enrolled students, the course author and administrators; the link of the preview lesson is public (FR-CAT-06).

## Consequences

- No video storage, transcoding or streaming has to be built or paid for.
- The player is provided by YouTube or Vimeo; it supports play, pause and seek.
- **Limitation:** anyone who obtains a link can watch the video without buying the course. This is accepted for version 1.
- A lesson stops working if the author deletes or hides the video; moderators check the links during review.
- FR-AUT-04 and FR-LRN-04 are worded accordingly.
