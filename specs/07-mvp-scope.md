# 07 — MVP scope (ultra-lean Android)

Goal: production-usable **Android-only** app for **Hyderabad** crew hiring at minimal cash cost.

**Platform lock:** Google Play / Android phones only. No iOS work in this phase (`09-android-platform.md`).

---

## In MVP (must ship)

### Accounts
- Phone OTP login  
- Studio and/or Talent mode  

### Talent
- Profile: photo, bio, city, roles, gear, day rate INR, radius, availability calendar  
- Portfolio (limited images)  

### Studio
- Studio profile  
- Favorites  
- Hire Help → create job (incl. multi-function dates)  
- Search/filter talent  
- Job queue  
- **Ranked Offers** + **Instant Offers**  
- Response timer + auto-advance  

### Trust
- Razorpay deposit on accept  
- Two-way reviews  
- Report / block  

### Comms
- In-app job chat  
- FCM push  
- WhatsApp `wa.me` deep links for offers  

### Ops
- Hyd city focus  
- Basic job list for both sides  

### Languages (P0)
- **English + Telugu + Hindi** UI via i18next  
- Language picker on first run + settings  
- Noto fonts for Telugu / Devanagari  
- Details: `10-i18n-languages.md`  

---

## Explicitly out of MVP

- iOS  
- WhatsApp Cloud API  
- Full agent NL hire (ship rules-based matching first; agent P1)  
- GST/CRM/proposals for couples  
- Email/SMS sync  
- Contact masking  
- Subscription billing  
- Platform commission  
- Editor marketplace  
- Tamil / Kannada UI (P1)  
- Auto-translate of chat / job notes  
- Live chat support  

---

## Success metrics (Hyd, first 90 days)

| Metric | Target |
|---|---|
| Active studios | 40–60 |
| Verified freelancers | 200+ |
| Peak-Saturday jobs posted | Growing weekly |
| Fill rate (offers → confirmed) | ≥50% then →60% |
| Deposit completion on accept | ≥70% |

---

## Suggested stack (cost)

- Expo (Android)  
- Supabase (Auth, Postgres, Storage, Realtime)  
- Razorpay  
- FCM  
- Optional cheap LLM later  

---

## Build order

1. Auth + profiles + availability  
2. Jobs + search + favorites  
3. Ranked / Instant offers + push  
4. Deposit + confirm  
5. Chat + reviews  
6. WA deep links + polish  
7. (P1) Agent + Cloud API WA  

---

## Traceability

Every SWM feature from `01-shootwithme-parity.md` is either:

- **In MVP**, or  
- Explicitly **P1/P2** with reason (cost / India substitute / non-critical)

India overrides from `02-india-customizations.md` that are P0 are in MVP (day rates, multi-function, UPI deposit, WA deep link, extra roles: at least cine + drone on profile).
