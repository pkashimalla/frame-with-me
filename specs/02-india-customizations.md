# 02 — India customizations

These are **additions / overrides** on top of ShootWith.Me parity. Mobile-first.

---

## 1. Roles beyond SWM

| Role | Why India |
|---|---|
| Assistant | Same as SWM |
| Second shooter (photo) | Same as SWM |
| Lead / associate photographer | Same as SWM |
| Cinematographer / videographer | Multi-cam wedding films |
| Drone operator | Common wedding add-on |
| Reel / content shooter | Same-day Instagram reels |
| Photo / video editor | Post-production freelancers (P1) |
| Hybrid photo+video | Common day-rate ask |

---

## 2. Event model (multi-function weddings)

SWM: single job date + event type.  
FWM: support **multi-day / multi-function** packages.

### Event types (India)

- Telugu wedding functions (Pellikoduku, Pellikuturu, etc.)
- Haldi / Mehendi / Sangeet / Barat / Wedding / Reception
- Muslim Nikah / Christian wedding / Sikh Anand Karaj
- Engagement / Pre-wedding
- Corporate / birthday / housewarming / store launch
- Destination wedding (outstation flag)

### Job fields (extra)

| Field | Notes |
|---|---|
| City + venue area | e.g. Hyderabad, Gachibowli |
| Function list | Haldi, Wedding, Reception with dates/times |
| Call time / wrap estimate | Indian crew culture |
| Food / stay provided? | Outstation |
| Travel allowance | If outside radius |
| Dress code | Black / ethnic / studio kit |
| Language preference | Telugu / Hindi / Tamil / English |
| Day rate (INR) | Default pricing unit (not only hourly) |

---

## 3. Pricing units

| SWM | FWM India |
|---|---|
| Hourly rate primary | **Day rate (INR)** primary |
| USD | INR |
| — | Optional half-day / hourly for corporate |
| — | City rate guide (suggested ranges, non-binding) |

Suggested launch ranges (Hyderabad, indicative):

- Assistant: ₹1,500–4,000 / day  
- Second shooter: ₹5,000–12,000 / day  
- Cine: ₹6,000–15,000 / day  
- Drone: ₹5,000–12,000 / day  
- Lead associate: higher, city-dependent  

---

## 4. Payments & trust (override SWM “no payments”)

SWM avoids payments. **India requires light escrow for trust.**

| Feature | Spec |
|---|---|
| UPI / Razorpay deposit | Default **25%** of agreed day rate on accept (configurable 20–40%) |
| Balance | Offline UPI/NEFT or in-app later |
| Calendar block | Date locked on confirmed deposit |
| Contact reveal | Phone optional hidden until deposit / reveal window (P1) |
| Platform fee | MVP: **0%** to maximize liquidity; later 8–12% or SaaS |
| PAN note | Soft prompt if yearly payouts may need TDS (P2) |

---

## 5. Notifications (WhatsApp-first)

| Channel | Priority |
|---|---|
| Push (FCM) | P0 |
| In-app | P0 |
| WhatsApp `wa.me` deep link / prefilled | P0 lean |
| WhatsApp Cloud API templates | P1 when volume justifies |
| Email | P1 |
| SMS | P2 fallback |

Notify on: offer received, offer expiring, accepted, declined, queue advanced, deposit due/paid, review request, no-show report.

---

## 6. Verification & safety

| Feature | Phase |
|---|---|
| Phone OTP login | P0 |
| Optional Aadhaar/PAN self-declare | P1 |
| Gear selfie / portfolio review (manual admin) | P1 |
| No-show flag | P0 |
| Block / report user | P0 |
| Soft ID badge “Verified” | P1 |

---

## 7. Language & localization

| Feature | Phase |
|---|---|
| App UI **English + Telugu + Hindi** | **P0** — see `10-i18n-languages.md` |
| Language picker (first run + settings) | P0 |
| Job notes / chat any language (no force-translate) | P0 |
| Tamil / Kannada UI | P1 |
| INR formatting, IST timezone | P0 |

---

## 8. City GTM constraints

| Feature | Spec |
|---|---|
| Launch city lock | Soft: Hyd first; show empty states for other cities |
| Travel / outstation jobs | Flag + TA field |
| Local radius default | e.g. 25–40 km metros |

---

## 9. Agentic (India workflow)

Natural language hire:

> “Need 1 second + 1 cine for Sat sangeet in Madhapur, budget 8k each, Telugu preferred”

Agent shortlists → proposes queue → studio confirms → ranked/instant offer.  
See `06-agentic-features.md`.

---

## 10. What we deliberately do **not** copy from Indian CRMs (v1)

- Full GST invoicing to couples  
- Couple lead CRM / proposal builder  
- Album delivery / face-match galleries  

Stay a **crew hiring mobile app**, not Studio Mithra clone.
