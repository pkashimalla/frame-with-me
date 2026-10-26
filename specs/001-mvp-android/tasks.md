# Tasks — 001 MVP Android

Ordered for Spec Kit `/speckit-implement`. Check boxes as done.

## Phase 0 — Foundation

- [ ] T001 Init monorepo: `apps/mobile` (Expo TS), `packages/domain`, workspace tooling
- [ ] T002 Add `.specify` constitution hooks to README + Cursor rules (already authored — verify agents load them)
- [ ] T003 Create design tokens + base UI: `Button`, `Field`, `Chip`, `Screen`, `Skeleton`, `TabBar`
- [ ] T004 i18n skeleton: en/te/hi JSON + language picker screen + Noto fonts
- [ ] T005 Supabase project + env templates (no secrets committed)
- [ ] T006 Domain ports: `NotificationPort`, `PaymentPort`, repository interfaces
- [ ] T007 Jest for `packages/domain` + CI script `test`
- [ ] T008 Document laptop → emulator → Pixel flow in README (verify)

## Phase 1 — Auth & profiles

- [ ] T010 Phone OTP auth via AuthPort/Supabase
- [ ] T011 Role selection Studio / Talent / Both
- [ ] T012 Studio profile CRUD
- [ ] T013 Talent profile: rates, gear, radius, portfolio upload (paged)
- [ ] T014 RLS policies for profiles
- [ ] T015 Unit tests: profile validation
- [ ] T016 Customer-perspective pass: onboarding in te/hi

## Phase 2 — Calendar

- [ ] T020 Availability calendar UI + AvailabilityService
- [ ] T021 Persist open/busy dates; indexed query helper
- [ ] T022 Auto-busy on confirmed booking
- [ ] T023 Unit tests: conflict / auto-busy
- [ ] T024 Customer pass: freelancer calendar clarity

## Phase 3 — Hire & offers

- [ ] T030 Call sheet create job (multi-function dates)
- [ ] T031 Lookbook search paginated + filters
- [ ] T032 Roster/favorites
- [ ] T033 Job queue reorder
- [ ] T034 Ranked offer engine + timer worker/edge function
- [ ] T035 Instant offer engine
- [ ] T036 Offer inbox UI (freelancer)
- [ ] T037 Domain tests: ranked + instant state machines (high coverage)
- [ ] T038 Customer pass: studio hire ≤ 5 min happy path

## Phase 4 — Trust rails & messaging

- [ ] T040 Razorpay deposit via PaymentPort + webhook
- [ ] T041 Confirm booking on deposit paid
- [ ] T042 In-app job chat (Realtime) with cleanup on unmount
- [ ] T043 FcmPushAdapter + WaMeNotificationAdapter
- [ ] T044 Two-way reviews + no-show report
- [ ] T045 Push/wa.me on offer/accept/deposit
- [ ] T046 Security+memory checklist on chat/realtime code
- [ ] T047 Tests: deposit confirm, webhook signature mock

## Phase 5 — Admin web

- [ ] T050 Scaffold `apps/admin`
- [ ] T051 Admin auth allowlist / role
- [ ] T052 Users list (paginated) + suspend/ban + reason
- [ ] T053 Jobs force-cancel
- [ ] T054 Deposit refund flag / ops action
- [ ] T055 Verification badge toggle
- [ ] T056 Audit log viewer
- [ ] T057 Ensure suspend cascades (logout, search hide, offers cancel)
- [ ] T058 Tests for ModerationService

## Phase 6 — Hardening & pilot

- [ ] T060 Pixel device QA checklist (en/te/hi)
- [ ] T061 Performance pass: list pagination, image sizes
- [ ] T062 Coverage report for domain; fill gaps
- [ ] T063 EAS preview APK for Hyd studios
- [ ] T064 `/speckit-converge` style gap review vs spec.md
- [ ] T065 Customer-perspective final gate

---

## Agent rules while implementing

1. Read constitution before coding  
2. After each task: run `.specify/checklists/post-change-security-memory.md`  
3. User-facing tasks: run Customer Perspective Agent  
4. Prefer extending design-system components over new one-offs  
