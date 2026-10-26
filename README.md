# Frame With Me

India-first **Android** marketplace for photography/videography studios to hire freelance crew  
(assistants, second shooters, leads, cine, drone) — inspired by [ShootWith.Me](https://shootwith.me/), built for Indian multi-day weddings.

| Surface | Who | Tech (planned) |
|---|---|---|
| Mobile app | Studios & freelancers | Expo → Android |
| Admin web | Platform team only | Separate web app |
| Backend | Shared | Supabase + Razorpay + FCM |

---

## Spec-Driven Development (Spec Kit)

This repo is run **spec-first**. Do not invent product behavior in code without updating specs.

| Artifact | Path |
|---|---|
| **Constitution** (binding rules) | [`.specify/memory/constitution.md`](.specify/memory/constitution.md) |
| Active feature pointer | [`.specify/feature.json`](.specify/feature.json) |
| **MVP spec** | [`specs/001-mvp-android/spec.md`](specs/001-mvp-android/spec.md) |
| **Plan** | [`specs/001-mvp-android/plan.md`](specs/001-mvp-android/plan.md) |
| **Tasks** | [`specs/001-mvp-android/tasks.md`](specs/001-mvp-android/tasks.md) |
| Post-change security/memory gate | [`.specify/checklists/post-change-security-memory.md`](.specify/checklists/post-change-security-memory.md) |
| Customer UX agent | [`.cursor/agents/customer-perspective.md`](.cursor/agents/customer-perspective.md) |
| Agent entry | [`AGENTS.md`](AGENTS.md) |

### Constitution highlights
1. **Security & user data safety** — highest priority  
2. **Memory-safe** code — no leaks; checklist after every change  
3. **On-demand loading** — paginate; feel fast  
4. **Notification ports** — free `wa.me` now, Cloud API later without rewrite  
5. **SoC** — UI → use-cases → repositories → adapters  
6. **Reusable UI** + **en / te / hi**  
7. **Strong domain tests**  
8. **Admin = web only**  
9. **Customer-perspective gate** for ease of use  

### Optional: install Spec Kit CLI
```bash
uv tool install specify-cli
# then use /speckit-specify, /speckit-plan, /speckit-tasks, /speckit-implement in your agent
```
Manual SDD artifacts are already present under `.specify/` and `specs/001-mvp-android/`.

---

## Wireframes (try UX now)

Open in Chrome/Edge:

[`wireframes/index.html`](wireframes/index.html)

- Cinema-set UI, lookbook hiring, call sheets, shoot calendar  
- Language: **English / తెలుగు / हिन्दी** (pill on phone or Language screen)  

Implementation must **meet or beat** this wireframe.

---

## Product docs (research)

| Doc | Purpose |
|---|---|
| [specs/00-product-overview.md](specs/00-product-overview.md) | Vision |
| [specs/01-shootwithme-parity.md](specs/01-shootwithme-parity.md) | SWM feature map |
| [specs/02-india-customizations.md](specs/02-india-customizations.md) | India extras |
| [specs/03-functional-requirements.md](specs/03-functional-requirements.md) | FR list |
| [specs/07-mvp-scope.md](specs/07-mvp-scope.md) | Lean MVP cut |
| [specs/09-android-platform.md](specs/09-android-platform.md) | Android-only |
| [specs/10-i18n-languages.md](specs/10-i18n-languages.md) | i18n |
| [specs/11-admin-ops.md](specs/11-admin-ops.md) | Admin web |

---

## First-time mobile developer — how you’ll test

You have a **Google Pixel** and will test on **laptop first**. App code is not scaffolded yet; when it is:

### A. Laptop (every day)
1. Install [Node.js LTS](https://nodejs.org/)  
2. Install [Android Studio](https://developer.android.com/studio) → create a Virtual Device  
3. From repo (after `apps/mobile` exists):
   ```bash
   cd apps/mobile
   npm install
   npx expo start
   ```
4. Press `a` to open the **emulator**, or use Expo Dev Tools  

### B. Google Pixel (USB)
1. On phone: **Settings → Developer options → USB debugging ON**  
2. Connect USB; allow debugging  
3. Same Wi‑Fi as PC for Expo Go, **or**:
   ```bash
   npx expo run:android
   ```
   (needed later for Razorpay / full native modules)

### C. Share APK with studios
```bash
npm i -g eas-cli
eas login
eas build --platform android --profile preview
```

### D. Play Store
`eas build --platform android --profile production` → upload **AAB** to Play Console (Internal testing first).

Full detail: `specs/009` / plan.md §8.

---

## Planned architecture (separation of concerns)

```
apps/mobile  →  ViewModels/Hooks  →  packages/domain (use-cases)
                                      ↓
                                 Repositories
                                      ↓
                         Supabase / Razorpay / FCM / wa.me adapters

apps/admin   →  same domain moderation use-cases (web UI)
```

---

## Status

| Item | Status |
|---|---|
| Wireframes | Done |
| Spec Kit constitution + MVP spec/plan/tasks | Done |
| Cursor rules + customer agent | Done |
| Expo app / admin code | **Not started** — next: Phase 0 tasks |

---

## Next step

Implement **T001** in `specs/001-mvp-android/tasks.md` (scaffold Expo monorepo) when you say go.
