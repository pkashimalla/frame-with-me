# 05 — Messaging, payments & trust

## Messaging (SWM parity + India)

### In-app messenger (P0)
- Thread scoped to a job (studio ↔ hired/offered talent)
- Text messages, timestamps, read state
- Push on new message

### Channel strategy
| Channel | Role |
|---|---|
| In-app | Source of truth (SWM parity) |
| Push | Instant alert |
| WhatsApp deep link | Lean P0: opens chat with prefilled job summary |
| WhatsApp Business API | P1: template “You have a new job offer” with deep link into app |
| Email | P1 digest / receipt |
| SMS | P2 costly fallback |

### SWM parity note
SWM syncs messenger + email + SMS. FWM substitutes **WhatsApp** for SMS as the India primary secondary channel.

### Leakage control (P1)
- Strip phone/email from chat until deposit paid or T−24h reveal window
- Still allow professional coordination via in-app

---

## Payments (India override of SWM)

SWM does **not** process payments. Frame With Me **does** a thin deposit layer.

### Flow
1. Talent accepts offer at agreed day rate  
2. Studio pays **deposit** (default 25%) via Razorpay (UPI / card / netbanking)  
3. Job → **Confirmed**; talent calendar blocked  
4. Remaining balance: studio marks “Paid offline” (UPI) or pays in-app later (P1)  
5. After job → both review  

### Rules (draft)
| Case | Outcome |
|---|---|
| Studio cancels >48h before | Full deposit refund to studio |
| Studio cancels <48h | Partial to talent (e.g. 50% of deposit) — finalize legally |
| Talent cancels / no-show | Deposit returned to studio; talent no-show flag |
| Dispute | Manual ops resolve |

### MVP monetization
- **0% commission** at launch (liquidity)
- Optional later: 8–12% or talent/studio SaaS (SWM-like INR yearly)

---

## Reviews & accountability (SWM parity)

After status **Completed**:
- Studio rates talent (1–5 + tags: punctual, kit, skill, attitude, communication)
- Talent rates studio (pay timely, briefing, respect, food/hours accuracy)
- Reviews public on profiles
- Incomplete reviews nudge for 7 days

---

## Trust signals on talent card

- Avg rating + # jobs  
- Response rate  
- Verified badge (P1)  
- No-show count (internal / soft warning)  
- Favorited by N studios (optional P1)  

---

## Terms
- Platform ToS: both parties act professionally (SWM-style)
- Optional simple freelancer agreement template PDF (P1) — not required to hire
