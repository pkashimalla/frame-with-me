# 09 — Android-only platform spec

**Decision:** Frame With Me ships **Android only** for v1 / MVP.  
**iOS:** out of scope until Hyd liquidity is proven. Do not design, test, or budget for App Store in this phase.

---

## Target devices

| Item | Spec |
|---|---|
| OS | Android **8.0 (API 26)+** |
| Form factor | Phone primary; tablet unoptimized OK |
| Architecture | arm64-v8a (plus armeabi-v7a if Expo default includes it) |
| Distribution | **Google Play** (internal → closed → production) |
| Sideload | Optional APK for studio beta testers only |

---

## Framework

| Choice | Detail |
|---|---|
| App | **Expo (React Native)** — TypeScript |
| Why | One codebase later portable to iOS; Android-first now; Cursor-friendly |
| Build | EAS Build for Android AAB/APK |
| OTA | Expo Updates optional P1 |

Even though Expo can target iOS, **CI and release pipelines are Android-only** until a future phase.

---

## Android-specific capabilities (P0)

| Capability | Use |
|---|---|
| FCM push | Offers, accept/decline, deposit, chat, reviews |
| Deep links | `https://` App Links and/or custom scheme `framewithme://` into offer/job |
| Razorpay Android SDK / Checkout | UPI deposit |
| Image picker / camera | Profile + portfolio |
| Background/killed push | Offer + expiry reminders must wake via FCM |
| Permissions | Camera, notifications, fine location optional (city text OK for MVP) |

---

## Explicitly not in Android v1

- iOS / TestFlight / Apple Developer account work  
- Apple Pay  
- iMessage / APNs  
- Wear OS  
- Android tablet-specific layouts  
- Instant Apps  

---

## Backend (shared, not OS-specific)

- Supabase: Auth (phone OTP), Postgres, Storage, Realtime  
- Razorpay  
- WhatsApp `wa.me` (no native WA SDK required)  

---

## Release checklist (Android)

1. Play Console account (~one-time fee)  
2. Package id e.g. `me.framewith.app`  
3. Signing key / EAS credentials  
4. Privacy policy URL (required for Play)  
5. Data safety form (phone, photos, payments)  
6. Internal testing track → Hyd studios  
7. Production rollout  

---

## Dev workflow

```
frame-with-me/
  apps/mobile/     # Expo Android app
  packages/…       # shared types later
  specs/           # this folder
```

Commands (target):

- `npx expo start` — local  
- `eas build --platform android` — store build  
- **Never** require `--platform ios` in MVP docs or scripts  

---

## Acceptance

MVP is done when a Hyd studio and freelancer can complete hire → deposit → chat → review **on Android phones from Play (or internal track)** with no iOS dependency.
