# Frame With Me — Constitution

Binding principles for all specs, plans, tasks, and code.  
Every agent change MUST be evaluated against this document.

**Product:** India-first Android marketplace connecting photography/videography **studios** with **freelance crew** (ShootWith.Me model + India customizations).  
**Surfaces:** Android app (Expo) · Admin web (separate) · Shared backend.

---

## I. Security & user data safety (HIGHEST PRIORITY)

Security and personal data protection outrank features, speed of delivery, and convenience.

MUST:
- Treat phone numbers, chats, portfolios, payment IDs, and device tokens as **sensitive PII**
- Validate and sanitize all inputs at API/edge boundaries
- Use least-privilege access (RLS / role checks); never trust the client
- Store secrets only in env / secret managers — never commit keys
- Encrypt in transit (TLS); use platform best practices at rest
- Log admin/support actions that touch user data (who/when/why)
- Support account deletion / data export paths aligned with DPDP intent
- Redact PII from analytics and error reports

MUST NOT:
- Expose other users’ phone/email before deposit/reveal rules allow
- Log OTP codes, access tokens, or full payment payloads
- Ship debug backdoors or hardcoded admin credentials

**After every code change:** agent MUST run the Security checklist in  
`.specify/checklists/post-change-security-memory.md` and fix findings before finishing.

---

## II. Memory efficiency & leak discipline

MUST:
- Prefer pagination / on-demand fetch; never load “all users/jobs” into memory or UI
- Unsubscribe listeners, clear timers, abort fetches on unmount / dispose
- Avoid retaining large image bitmaps; use sized thumbnails + recycle lists
- Cap in-memory caches; prefer query-cache with stale times over global stores of everything
- Profile for leaks when adding realtime subscriptions or chat listeners

**After every code change:** agent MUST explicitly verify no new subscription/timer/ref leaks  
and note the check in the response (see post-change checklist).

---

## III. Performance & perceived speed

Users MUST feel the app is fast.

MUST:
- Skeleton / optimistic UI for primary flows
- Page size defaults (e.g. 20); infinite scroll or “load more”
- Index DB queries used by search (city, date availability, role)
- Defer non-critical work (portfolio full-res, analytics)
- Cache only what the current screen needs

MUST NOT:
- Block first paint on full profile/portfolio downloads
- N+1 query patterns for lists

---

## IV. Notification provider portability

MVP MAY use free/cheap channels (`wa.me`, FCM, email).

MUST:
- Access messaging only through a **NotificationPort** (interface/adapter)
- Keep provider-specific SDKs inside adapter modules
- Allow swapping WhatsApp Cloud API / another BSP without rewriting domain logic
- Keep message templates as data (locale + event type), not hardcoded provider APIs in UI

---

## V. Architecture — separation of concerns

MUST use layered, testable structure (class / module frameworks that fit Expo + TS):

```
UI (screens/components) → ViewModels/Hooks → UseCases/Services → Repositories → DataSources (Supabase/Razorpay/FCM)
```

- Domain rules live in services/use-cases — not in JSX
- Repositories abstract storage; UI never imports Supabase client directly (except composition root)
- Admin web shares domain contracts where possible; separate deployable
- Prefer clear classes or cohesive modules for ports/adapters (NotificationPort, PaymentPort, AuthPort)

---

## VI. UI system — reusable, enterprise-grade

MUST:
- Build from a shared design system (`Button`, `Field`, `Chip`, `CallSheetCard`, `LookCard`, `TabBar`, …)
- Match or exceed wireframe quality (`wireframes/index.html`) — cinema-set visual language
- Support **en / te / hi** via i18n keys only — no hardcoded user-facing English in components
- Prefer ease of use: large tap targets, clear primary CTA, short copy

MUST NOT:
- One-off styled buttons per screen
- Duplicate spacing/typography tokens

---

## VII. Testing

MUST:
- Unit-test domain/use-cases and pure utils heavily
- Component tests for critical UI controls
- Integration tests for offer state machine, deposit confirm, auth
- Aim for high line coverage on domain + repositories; track gaps honestly
- Add regression tests when fixing bugs

---

## VIII. Spec-driven development (Spec Kit)

MUST:
- Change behavior only with updated `spec.md` / `plan.md` / `tasks.md` when requirements shift
- Obey this constitution in every `/speckit-*` and implementation pass
- Keep admin capabilities on **web**, not in the consumer Android app

---

## IX. Customer-perspective gate

Before marking a user-facing task done, run or request the **Customer Perspective Agent**  
(see `.cursor/agents/customer-perspective.md`):

- Can a Hyd studio hire in under 3 minutes without training?
- Can a freelancer manage calendar and accept an offer without confusion?
- Does language switching (te/hi/en) feel first-class?
- Does anything feel slower, scarier, or more complex than WhatsApp?

Fail the gate if ease-of-use is compromised for “clever” architecture.

---

## X. Platform scope reminders

- Android-only MVP; admin = separate web app
- Trust > Uber-style open broadcast for wedding crews (ranked/instant + favorites)
- Hyderabad first; UPI deposit for confirmations
- Free notification channels OK for MVP if ports stay swappable

---

## Amendment

Amendments require updating this file and noting the date + reason in the project README Spec Kit section.
