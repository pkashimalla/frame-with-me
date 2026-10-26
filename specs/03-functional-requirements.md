# 03 — Functional requirements (Android)

Platform: **Android only** (Expo/React Native). iOS is out of scope for v1 — see `09-android-platform.md`.

---

## FR-AUTH — Authentication

| ID | Requirement | Priority |
|---|---|---|
| FR-AUTH-01 | Sign up / login with phone OTP | P0 |
| FR-AUTH-02 | Optional email attach | P1 |
| FR-AUTH-03 | Choose primary mode: Studio, Talent, or Both | P0 |
| FR-AUTH-04 | Session persist; logout | P0 |
| FR-AUTH-05 | Account delete / data request (DPDP-aware) | P1 |

---

## FR-PROF — Profiles

| ID | Requirement | Priority |
|---|---|---|
| FR-PROF-01 | Talent: bio, photo, city, roles, experience, style tags | P0 |
| FR-PROF-02 | Talent: portfolio images/videos (limit for MVP) | P0 |
| FR-PROF-03 | Talent: gear checklist | P0 |
| FR-PROF-04 | Talent: day rate (INR) + optional hourly | P0 |
| FR-PROF-05 | Talent: working radius (km) | P0 |
| FR-PROF-06 | Talent: availability calendar (available / busy / blocked) | P0 |
| FR-PROF-07 | Studio: name, city, logo, about, typical event types | P0 |
| FR-PROF-08 | Profile completeness score nudges | P1 |
| FR-PROF-09 | Role upgrade request (assistant→second etc.) | P1 |

---

## FR-SEARCH — Find talent

| ID | Requirement | Priority |
|---|---|---|
| FR-SEARCH-01 | Studio search by role, date, city/radius, rate max, gear, min rating, experience | P0 |
| FR-SEARCH-02 | Results only show talent available on job date (within radius) | P0 |
| FR-SEARCH-03 | Talent card: photo, role, rate, rating, distance, gear badges | P0 |
| FR-SEARCH-04 | Talent detail screen with portfolio + reviews | P0 |
| FR-SEARCH-05 | Add to Favorites | P0 |
| FR-SEARCH-06 | Favorites filter / list | P0 |
| FR-SEARCH-07 | Add selected talent to job queue | P0 |

---

## FR-JOB — Jobs

| ID | Requirement | Priority |
|---|---|---|
| FR-JOB-01 | Studio creates job: name, date(s), event type(s), venue/area, role, rate offered, notes | P0 |
| FR-JOB-02 | Multi-function dates on one job (Haldi+Wedding+Reception) | P0 |
| FR-JOB-03 | Attach call time, food/stay, language, dress code | P1 |
| FR-JOB-04 | Job status: Draft → Offering → Filled → Completed → Cancelled | P0 |
| FR-JOB-05 | Studio job list (upcoming / past) | P0 |
| FR-JOB-06 | Talent job list (offers / confirmed / past) | P0 |
| FR-JOB-07 | Both parties see shared job detail after hire | P0 |

---

## FR-OFFER — Queues & offers

| ID | Requirement | Priority |
|---|---|---|
| FR-OFFER-01 | Ranked offer: sequential exclusive offers | P0 |
| FR-OFFER-02 | Configurable accept window (e.g. 15m / 1h / 4h / 24h) | P0 |
| FR-OFFER-03 | On decline or timeout → auto next in queue | P0 |
| FR-OFFER-04 | Instant offer: parallel to all in queue; first accept wins; others auto-expire | P0 |
| FR-OFFER-05 | Talent push + WA deep-link on new offer | P0 |
| FR-OFFER-06 | Talent Accept / Decline with optional reason | P0 |
| FR-OFFER-07 | Studio notified on accept / decline / fill / queue exhausted | P0 |
| FR-OFFER-08 | Cancel active offer queue | P0 |

---

## FR-MSG — Messaging

| ID | Requirement | Priority |
|---|---|---|
| FR-MSG-01 | Thread per job between studio and talent | P0 |
| FR-MSG-02 | Text messages; image attach P1 | P0 / P1 |
| FR-MSG-03 | Unread badges | P0 |
| FR-MSG-04 | Block phone numbers in chat until reveal (P1) | P1 |

---

## FR-PAY — Payments (India)

| ID | Requirement | Priority |
|---|---|---|
| FR-PAY-01 | On accept, request UPI/Razorpay deposit (% of agreed rate) | P0 |
| FR-PAY-02 | Mark job Confirmed when deposit paid | P0 |
| FR-PAY-03 | Studio can mark balance paid offline | P0 |
| FR-PAY-04 | Refund deposit rules on studio cancel / talent no-show | P1 |
| FR-PAY-05 | Platform fee toggle (off for MVP) | P1 |

---

## FR-REV — Reviews

| ID | Requirement | Priority |
|---|---|---|
| FR-REV-01 | After completed job, both sides prompted to review | P0 |
| FR-REV-02 | Star rating + short text + tags (punctual, gear, attitude) | P0 |
| FR-REV-03 | Reviews visible on profiles | P0 |
| FR-REV-04 | Report no-show / dispute | P0 |

---

## FR-NOTIF — Notifications

| ID | Requirement | Priority |
|---|---|---|
| FR-NOTIF-01 | FCM push for offer / accept / decline / deposit / review | P0 |
| FR-NOTIF-02 | WhatsApp deep-link helper for critical actions | P0 |
| FR-NOTIF-03 | WhatsApp Cloud API templates | P1 |
| FR-NOTIF-04 | In-app notification center | P1 |

---

## FR-ADMIN — Ops (minimal)

| ID | Requirement | Priority |
|---|---|---|
| FR-ADMIN-01 | Simple admin (web or Supabase): ban user, verify badge | P1 |
| FR-ADMIN-02 | City allowlist for launch | P0 |

---

## FR-AGENT — Agentic (see 06)

| ID | Requirement | Priority |
|---|---|---|
| FR-AGENT-01 | NL → suggested shortlist + draft queue | P1 |
| FR-AGENT-02 | Auto-chase declines / propose backups | P1 |
