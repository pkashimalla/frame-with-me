# Implementation Plan — 001 MVP Android

**Spec:** `spec.md`  
**Constitution:** `.specify/memory/constitution.md`

---

## 1. Tech stack

| Layer | Choice | Notes |
|---|---|---|
| Mobile | Expo (RN) + TypeScript | Android only |
| Admin | Next.js (or Vite React) + TS | Separate app `apps/admin` |
| Backend | Supabase | Auth OTP, Postgres, Storage, Realtime, RLS |
| Payments | Razorpay | Behind `PaymentPort` |
| Push | FCM via Expo Notifications | Behind `NotificationPort` |
| WhatsApp MVP | `wa.me` deep links | Adapter swappable → Cloud API later |
| i18n | i18next + expo-localization | en / te / hi |
| Lists | FlashList + page cursors | Perf |
| Tests | Jest + React Native Testing Library + Playwright/admin later | |

## 2. Repository layout

```
frame-with-me/
  apps/
    mobile/                 # Expo Android
    admin/                  # Admin web
  packages/
    domain/                 # Use-cases, state machines, ports (classes)
    ui/                     # Shared design-system (mobile-first tokens; admin may mirror)
    notification/           # NotificationPort + adapters (Fcm, WaMe, later WaCloud)
    payments/               # PaymentPort + Razorpay adapter
  specs/                    # Product + SDD
  wireframes/
  .specify/
```

## 3. Separation of concerns (class-friendly)

### Domain (`packages/domain`)
Classes / modules such as:
- `OfferQueueService` — ranked/instant transitions
- `AvailabilityService` — open/busy + conflict checks
- `BookingConfirmService` — deposit → confirm → calendar lock
- `ModerationService` — suspend user, force-cancel (admin)

### Ports (interfaces)
- `AuthPort`, `UserRepository`, `JobRepository`, `OfferRepository`
- `NotificationPort.send(templateId, locale, payload)`
- `PaymentPort.createDeposit(jobId, amountInr)`

### Adapters
- Supabase repositories
- `WaMeNotificationAdapter`, `FcmPushAdapter`
- `RazorpayPaymentAdapter`

### UI
- Screens call hooks/view-models that call use-cases  
- **No** Supabase in presentational components  

## 4. Data loading strategy

- Cursor pagination: `limit=20`, `cursor=…`
- Talent lookbook: metadata + thumbnail URL only
- Job lists: summary DTO; detail fetched on open
- Realtime: subscribe only to active job chat / active offer id; unsubscribe on leave
- Image: progressive sizes; placeholder skeletons

## 5. Security plan

- Supabase RLS: users read own + permitted public talent cards; studios write own jobs
- Service role only on server/edge for admin + webhooks
- Razorpay webhooks verify signatures
- Admin web: separate auth (allowlisted emails or `admin` role claim)
- Audit table for admin actions

## 6. i18n & UI

- Design tokens from wireframe (void/ink/gel/bone)
- Components in `packages/ui` or `apps/mobile/src/ui`
- Fonts: Sora/Instrument for `en`; Noto Sans Telugu / Devanagari for `te`/`hi`
- Customer-perspective pass on every vertical slice

## 7. Testing strategy

| Layer | Focus |
|---|---|
| Domain unit | Offer machine, availability, deposit confirm, moderation |
| Repository | Mocked Supabase client contracts |
| UI | Button/Field/LookCard; offer accept screen |
| E2E (later) | Detox/Maestro on Pixel for J1/J2 |

Coverage goal: **high on `packages/domain`** (near-complete lines); mobile screens pragmatic.

## 8. Local test → Pixel → Play

1. `npx expo start` on laptop (web optional / Expo Go)  
2. Android emulator  
3. USB Pixel + `expo start` or `expo run:android`  
4. EAS preview APK for studios  
5. Play internal track  

See root `README.md`.

## 9. Phased delivery

| Phase | Outcome |
|---|---|
| P0 | Monorepo scaffold, UI kit, auth+i18n, constitution gates |
| P1 | Profiles + calendar |
| P2 | Jobs + lookbook + queue offers |
| P3 | Deposit + chat + reviews + FCM/wa.me |
| P4 | Admin web moderation MVP |
| P5 | Hardening, tests, Hyd pilot |

## 10. Risks

| Risk | Mitigation |
|---|---|
| Expo Go limits Razorpay | Dev client / `expo run:android` early |
| RLS mistakes | Integration tests + security checklist |
| Telugu font layout overflow | Design tokens + QA on Pixel |
| Notification swap pain | Ports from day one |
