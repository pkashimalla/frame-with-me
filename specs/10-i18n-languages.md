# 10 — Regional languages (Telugu, Hindi, English)

**Goal:** Photographers & videographers in Hyd / North can use the app in **Telugu**, **Hindi**, or **English**.

**Priority:** First-class from MVP — do **not** hardcode English strings.

---

## 1. Languages (phase)

| Code | Language | Phase |
|---|---|---|
| `en` | English | P0 default fallback |
| `te` | తెలుగు (Telugu) | P0 (Hyd launch) |
| `hi` | हिन्दी (Hindi) | P0 (North-ready + Hyd Hindi speakers) |
| `ta` | தமிழ் (Tamil) | P1 (Chennai) |
| `kn` | ಕನ್ನಡ (Kannada) | P1 (Bengaluru) |

Scripts are **LTR** (no RTL layout work).

---

## 2. What gets translated

| Surface | Translate? |
|---|---|
| App chrome (buttons, tabs, errors, empty states) | **Yes** |
| Onboarding, role labels, offer types | **Yes** |
| System push copy templates | **Yes** (per language) |
| WhatsApp deep-link prefills | **Yes** (P0 simple; Cloud API templates P1) |
| Job notes / chat typed by users | **No** — free text any language |
| Portfolio captions (user) | **No** |
| City / venue names | Keep as user typed; UI labels translated |

---

## 3. How we build it (Expo)

### Stack
- `i18next` + `react-i18next`
- `expo-localization` — detect device locale on first launch
- JSON catalogs: `locales/en.json`, `locales/te.json`, `locales/hi.json`

### Pattern
```tsx
// Never
<Text>Hire Help</Text>

// Always
<Text>{t("studio.hireHelp")}</Text>
```

### Keys (namespaced)
```
auth.welcome.title
studio.tab.board
studio.callSheet
talent.calendar.open
offer.accept
offer.decline
common.continue
```

### Language switch
- Settings → **App language**
- Options: Telugu / Hindi / English
- Persist in AsyncStorage + user profile (`preferred_locale`)
- Changing language re-renders entire app (no restart required)

### First-run
1. If device locale is `te*` → default Telugu  
2. Else if `hi*` → Hindi  
3. Else English  
4. Always allow change on role screen (“Choose language”)

---

## 4. Fonts (critical for Telugu / Hindi)

English display fonts (Instrument Serif / Sora) **won’t cover** Telugu glyphs well.

| Use | Font |
|---|---|
| UI body (all locales) | **Noto Sans** + **Noto Sans Telugu** + **Noto Sans Devanagari** |
| English brand / display only | Instrument Serif (en screens / Latin headlines) |
| Telugu/Hindi headlines | Noto Serif Telugu / Noto Serif Devanagari **or** keep Noto Sans bold |

Load via `@expo-google-fonts/noto-sans-telugu` etc., or bundle TTF.

Rule: if `locale !== en`, use Noto family for **all** UI text to avoid tofu (□).

---

## 5. Layout rules

- Prefer **shorter English source strings**; Telugu/Hindi often run **20–40% longer** — buttons need wrap / min-height  
- Avoid text inside images  
- Keep call-sheet / lookbook labels in `t()` keys  
- Dates: `date-fns` or `Intl` with `te-IN` / `hi-IN` / `en-IN`  
- Currency: always `₹` via `Intl.NumberFormat("en-IN")` (same across locales)

---

## 6. Content process

1. Dev ships keys + English  
2. Native speaker (or pro) fills `te.json` / `hi.json` — **not raw Google Translate for final**  
3. Photographer glossary: Second shooter, Call sheet, Roster — decide Telugu/Hindi loanwords vs transliteration once (e.g. keep “Second shooter” in Latin if industry speaks that way)  
4. QA on real devices with Telugu/Hindi system language  

### Suggested industry terms (draft)
| English | Approach |
|---|---|
| Second shooter | Keep English in all locales (industry term) **or** local gloss in subtitle |
| Call sheet | Translate label; keep English in parentheses first release |
| Roster | Translate (“మీ బృందం” / “आपकी टीम”) |

Final glossary lives in `locales/GLOSSARY.md` (to add when translating).

---

## 7. Backend / notifications

| Item | Spec |
|---|---|
| `users.preferred_locale` | `en` \| `te` \| `hi` |
| Push payload | Server picks template by locale |
| Job content | Store as written; no auto-translate MVP |
| Admin | English OK |

---

## 8. MVP cut

**In MVP**
- `en` + `te` + `hi` for all P0 screens  
- Language picker on first run + settings  
- Correct fonts for te/hi  
- Push strings in 3 languages  

**Out of MVP**
- Auto-translate chat  
- Tamil/Kannada  
- Voice UI in regional languages  

---

## 9. Effort (solo + Cursor)

| Work | Estimate |
|---|---|
| Wire i18n + switcher + fonts | 2–3 days |
| English keys for all MVP screens | 1–2 days (while building UI) |
| Telugu + Hindi translation pass | 2–4 days (native help) |
| QA pass | 1 day |

Cheaper to do **while building** than retrofit later.
