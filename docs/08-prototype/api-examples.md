# API Examples

**Task:** DIP-10
**Status:** Draft. These examples show the proposed REST contract behind the mockups in [`prototype.md`](prototype.md). The binding contract will be the OpenAPI specification in `backend/api/openapi.yaml` (NFR-MNT-02). If the two differ, the OpenAPI specification wins and this file is updated.

## Conventions (proposed)

| Topic | Convention |
|---|---|
| Base path | `/api/v1` |
| Format | JSON, field names in `snake_case`, dates in ISO 8601 with time zone offset |
| Authentication | `Authorization: Bearer <access_token>`; access token lives 15 minutes, refresh token 30 days (NFR-SEC-02) |
| Money | Amount in cents plus currency code: `{"amount": 1999, "currency": "USD"}` |
| Errors | `{"error": {"code": "...", "message": "..."}}` with the matching HTTP status |

All IDs, names and numbers below are sample data that match the mockups.

---

## 1. Register (screen 2.1, FR-ACC-01, FR-ACC-02)

```http
POST /api/v1/auth/register
Content-Type: application/json

{
  "name": "Yerassyl Kuanyshov",
  "email": "yerassyl.kuanyshov@example.com",
  "password": "<password>",
  "interface_language": "en",
  "time_zone": "Asia/Almaty"
}
```

```http
HTTP/1.1 201 Created

{
  "user": {
    "id": "3e8a1f6b-2c4d-4e7f-8a9b-0c1d2e3f4a5b",
    "name": "Yerassyl Kuanyshov",
    "email": "yerassyl.kuanyshov@example.com",
    "role": "student",
    "email_confirmed": false
  },
  "message": "Confirmation link sent to yerassyl.kuanyshov@example.com"
}
```

## 2. Log in (screen 2.1, FR-ACC-03)

```http
POST /api/v1/auth/login
Content-Type: application/json

{ "email": "yerassyl.kuanyshov@example.com", "password": "<password>" }
```

```http
HTTP/1.1 200 OK

{
  "access_token": "<jwt>",
  "access_token_expires_in": 900,
  "refresh_token": "<opaque token>",
  "user": { "id": "3e8a1f6b-2c4d-4e7f-8a9b-0c1d2e3f4a5b", "role": "student" }
}
```

## 3. Search and filter the catalog (screen 1.2, FR-CAT-02, FR-CAT-03)

Available to guests, no token needed.

```http
GET /api/v1/courses?q=python&category=programming&level=beginner&price=paid&min_rating=4&language=en&page=1&page_size=20
```

```http
HTTP/1.1 200 OK

{
  "items": [
    {
      "id": "c2f7a1d4-3b8e-4c6a-9f10-5e2d7b8a4c11",
      "title": "Python Fundamentals",
      "author": { "id": "7b1e2d3c-4f5a-4b6c-8d7e-9f0a1b2c3d4e", "name": "Adil Ramazan" },
      "category": "programming",
      "level": "beginner",
      "language": "en",
      "price": { "amount": 1999, "currency": "USD" },
      "rating": { "average": 4.7, "count": 128 },
      "students_count": 1240
    }
  ],
  "page": 1,
  "page_size": 20,
  "total": 1
}
```

## 4. Pay for a course in test mode (screen 2.2, FR-PAY-01, FR-PAY-02, FR-LRN-02)

The client chooses the simulated result. No card data is sent.

```http
POST /api/v1/courses/c2f7a1d4-3b8e-4c6a-9f10-5e2d7b8a4c11/purchases
Authorization: Bearer <access_token>
Content-Type: application/json

{ "simulated_result": "success" }
```

```http
HTTP/1.1 201 Created

{
  "purchase": {
    "id": "9c0d1e2f-3a4b-4c5d-8e6f-7a8b9c0d1e2f",
    "course_id": "c2f7a1d4-3b8e-4c6a-9f10-5e2d7b8a4c11",
    "price": { "amount": 1999, "currency": "USD" },
    "status": "successful",
    "created_at": "2026-10-22T10:02:00+05:00"
  },
  "enrollment": { "course_id": "c2f7a1d4-3b8e-4c6a-9f10-5e2d7b8a4c11", "progress_percent": 0 }
}
```

If the email is not confirmed yet:

```http
HTTP/1.1 403 Forbidden

{ "error": { "code": "email_not_confirmed", "message": "Confirm your email before enrolling in courses." } }
```

## 5. Complete a lesson and receive XP (screen 3.1, FR-LRN-05, FR-LRN-07, FR-GAM-01, FR-GAM-04)

```http
POST /api/v1/lessons/5a9e3c21-7d4b-4f8a-b2c6-1e0f9d8a7b34/complete
Authorization: Bearer <access_token>
```

```http
HTTP/1.1 200 OK

{
  "lesson_id": "5a9e3c21-7d4b-4f8a-b2c6-1e0f9d8a7b34",
  "completed_at": "2026-10-22T10:20:00+05:00",
  "course_progress": { "completed": 1, "total": 16, "percent": 6 },
  "gamification": {
    "xp_awarded": 10,
    "xp_total": 730,
    "level": 4,
    "next_level_xp": 1000,
    "streak": { "current": 5, "today_counted": true },
    "achievements_unlocked": []
  }
}
```

Calling the same endpoint again returns `"xp_awarded": 0`, because XP for one activity is awarded only once (FR-GAM-02).

## 6. Submit a test attempt (screen 3.2, FR-LRN-06, FR-GAM-01)

```http
POST /api/v1/tests/8d3b6f2a-1c4e-4a7b-9e5d-2f6a0b1c3d48/attempts
Authorization: Bearer <access_token>
Content-Type: application/json

{
  "answers": [
    { "question_id": "q1", "option_ids": ["q1-a"] },
    { "question_id": "q2", "option_ids": ["q2-a", "q2-c"] },
    { "question_id": "q3", "option_ids": ["q3-b"] },
    { "question_id": "q4", "option_ids": ["q4-a"] },
    { "question_id": "q5", "option_ids": ["q5-d"] }
  ]
}
```

```http
HTTP/1.1 201 Created

{
  "attempt": 1,
  "attempts_left": 2,
  "score_percent": 80,
  "correct": 4,
  "total": 5,
  "passing_score_percent": 70,
  "passed": true,
  "gamification": {
    "xp_awarded": 20,
    "xp_total": 750,
    "level": 4,
    "achievements_unlocked": []
  }
}
```

## 7. Weekly leaderboard (screen 4.2, FR-GAM-10, FR-GAM-12)

```http
GET /api/v1/leaderboards/weekly
Authorization: Bearer <access_token>
```

```http
HTTP/1.1 200 OK

{
  "period": {
    "from": "2026-11-09T00:00:00+05:00",
    "to": "2026-11-16T00:00:00+05:00",
    "time_zone": "UTC+05:00"
  },
  "entries": [
    { "rank": 1, "user": { "name": "Daniyar S.", "level": 7 }, "xp": 640 },
    { "rank": 2, "user": { "name": "Madina T.", "level": 6 }, "xp": 515 },
    { "rank": 2, "user": { "name": "Timur B.", "level": 5 }, "xp": 515 },
    { "rank": 4, "user": { "name": "Aliya N.", "level": 6 }, "xp": 480 }
  ],
  "limit": 50,
  "me": { "rank": 14, "xp": 280, "level": 5 }
}
```

The list is shortened here. The response contains up to 50 entries. Equal XP gives the same rank, and the next rank is skipped. `me` is always present for a logged-in student, even outside the top 50. The all-time board uses the same shape at `GET /api/v1/leaderboards/all-time` (FR-GAM-11).

## 8. Moderate a course (screen 6.1, FR-ADM-01, FR-AUT-07)

```http
POST /api/v1/admin/courses/1f2e3d4c-5b6a-4978-8a9b-0c1d2e3f4a5b/moderation
Authorization: Bearer <access_token>
Content-Type: application/json

{ "decision": "reject", "comment": "Quiz · Module 2: mark the correct answers in questions 3 and 5." }
```

```http
HTTP/1.1 200 OK

{
  "course_id": "1f2e3d4c-5b6a-4978-8a9b-0c1d2e3f4a5b",
  "status": "rejected",
  "comment": "Quiz · Module 2: mark the correct answers in questions 3 and 5.",
  "moderated_at": "2026-11-16T15:30:00+05:00"
}
```

With `"decision": "approve"`, the status becomes `published` and the course appears in the catalog. A user without the administrator role gets `403 Forbidden` (FR-ACC-05).
