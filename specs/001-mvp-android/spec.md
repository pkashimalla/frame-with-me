# Feature Spec — 001 MVP Android (+ Admin Web)

**Status:** Draft complete for SDD  
**Constitution:** `.specify/memory/constitution.md`  
**Wireframe reference:** `wireframes/index.html` (UX must meet or beat this)  
**Related research specs:** `specs/00-*.md` … `specs/10-*.md`

---

## 1. Problem

Indian wedding/event photo-video studios staff overflow crew via WhatsApp/Instagram. That causes no-shows, double booking, unknown quality, and slow Saturday fills. Freelancers miss work because they must monitor groups constantly.

## 2. Vision

**Frame With Me** lets studios hire assistants, second shooters, leads, cine, and drone via mobile — availability calendar, lookbook search, ranked/instant offer queues, UPI deposit, chat, reviews — with Telugu/Hindi/English UI. Platform ops manage trust via a **separate admin web app**.

## 3. Users & goals

| Persona | Goals |
|---|---|
| Studio | Fill a role in minutes; prefer trusted roster; pay deposit; chat; review |
| Freelancer | Set open days; get offers; accept/decline; get paid deposit signal; chat; review |
| Platform admin (web) | Ban/suspend; force-cancel jobs; refund deposits; verify profiles; audit |

## 4. Out of scope (MVP)

- iOS
- Uber-style broadcast to all nearby as default
- Couple-facing booking / full studio CRM / GST invoices
- WhatsApp Business Cloud API (design for later via port)
- Auto-translate of chat/notes
- Tamil/Kannada UI
- Admin inside Android app

## 5. User journeys (acceptance)

### J1 — First-time studio (Hyd)
1. Install / open app (emulator or Pixel)  
2. Choose language EN/TE/HI  
3. Register phone + OTP  
4. Choose Studio (or Both)  
5. Create call sheet (multi-function dates OK)  
6. Lookbook search → queue → Ranked or Instant offer  
7. On accept → pay UPI deposit → Confirmed  
8. Chat + later review  

**Accept:** Completable without training in ≤ 5 minutes on a happy path.

### J2 — Freelancer calendar & offer
1. Language → register → Freelancer  
2. Mark days Open/Busy on calendar  
3. Receive offer (push + optional wa.me)  
4. Accept/Pass within timer  
5. See booking; calendar auto-Busy when confirmed  

**Accept:** Calendar and offer decision are obvious in chosen language.

### J3 — Admin trust action
1. Admin logs into web  
2. Finds user by phone/name  
3. Suspends user with reason  
4. User cannot login; removed from search; open offers cancelled  
5. Action appears in audit log  

## 6. Functional requirements (summary)

Full FR IDs remain in `specs/03-functional-requirements.md`. MVP MUST include:

| Area | Requirements |
|---|---|
| Auth | Phone OTP; role Studio/Talent/Both |
| i18n | en, te, hi; picker; Noto fonts for te/hi |
| Profiles | Talent: rates INR/day, gear, radius, portfolio (paged); Studio profile |
| Calendar | Open/Busy; confirmed jobs force Busy |
| Hire | Call sheet; lookbook; favorites/roster; filters |
| Offers | Ranked exclusive queue + Instant; timers; auto-advance |
| Pay | Razorpay deposit (~25%); confirm on pay |
| Chat | Per-job thread; push on message |
| Reviews | Two-way after complete |
| Notify | FCM + wa.me via NotificationPort |
| Admin web | Ban, force-cancel, refund flag, verify, audit |
| Perf | Paginated lists; skeletons; no full-table loads |

## 7. Non-functional requirements

| ID | Requirement |
|---|---|
| NFR-SEC-1 | Security & PII per constitution §I |
| NFR-MEM-1 | No listener/timer leaks; post-change checklist |
| NFR-PERF-1 | List endpoints paginated; default page ≤ 20 |
| NFR-I18N-1 | All user-visible chrome via i18n keys |
| NFR-PORT-1 | Notifications/payments behind ports |
| NFR-TEST-1 | Domain offer/payment/auth heavily unit-tested |
| NFR-UX-1 | Customer-perspective gate before done |
| NFR-UI-1 | Shared design system; enterprise consistency |

## 8. Offer state machines

**Ranked:** QUEUED → OFFERED(n) → ACCEPTED → DEPOSIT_PENDING → CONFIRMED  
Decline/Expire → next n+1; empty → UNFILLED. At most one OFFERED at a time.

**Instant:** parallel OFFERED; first ACCEPTED wins; others EXPIRED_LOST → deposit → CONFIRMED.

## 9. Data principles

- Soft-delete / suspend flags preferred over hard-delete where audit needs history  
- Availability queries must be indexed for city + date + role  
- Portfolio media stored in object storage; list returns thumbnails only  

## 10. Success metrics (Hyd, 90 days)

| Metric | Target |
|---|---|
| Active studios | 40–60 |
| Freelancers | 200+ |
| Offer → confirm fill rate | ≥ 50% then ≥ 60% |
| Deposit completion after accept | ≥ 70% |
| Crash-free sessions | ≥ 99% |

## 11. Customer-perspective principles

- Primary CTA always obvious  
- Fewer taps than WhatsApp group hiring for the happy path  
- Errors in plain language (localized)  
- Never surprise-charge; deposit amount shown before pay  
- Language switch doesn’t reset navigation stack unexpectedly  

## 12. Open decisions (defaults locked for MVP)

| Topic | Decision |
|---|---|
| Deposit % | 25% default |
| Instant vs Ranked default | Ranked |
| Nearby open broadcast | Not in MVP |
| Admin surface | Web only |
| Phone reveal | Optional P1; chat first |
