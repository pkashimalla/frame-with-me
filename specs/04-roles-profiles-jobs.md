# 04 — Roles, profiles, jobs & offer flows

## Role definitions

### Studio
Business or lead photographer/videographer who needs to hire crew for booked client work.

### Assistant
Entry-level. Helps with bags, lights, herding guests, basic support. Portfolio optional. May start at ₹0–low day rate to get reviews.

### Second shooter
Has own camera body + portfolio. Captures additional angles under studio direction; can work independently for stretches of the day.

### Lead / associate shooter
Covers a full job representing the hiring studio. High trust; strong portfolio and reviews required (soft gate: experience years + reviews).

### India specialists
Cinematographer, drone, reel shooter, editor (editor P1).

A user may hold **multiple roles** with different rates.

---

## Profile fields (talent)

```
identity: name, photo, phone, city
roles: [assistant, second, lead, cine, drone, reel, editor]
bio, style_tags[]
experience_years
gear: { bodies[], lenses[], lights[], drone?, other }
rates: { day_inr, half_day_inr?, hourly_inr? } per role
radius_km
languages[]
availability: calendar dates → available | busy | blocked
portfolio: media[]
stats: rating_avg, jobs_completed, response_rate, no_show_count
verification: phone_ok, badge?
```

## Profile fields (studio)

```
name, logo, city, about
typical_events[]
favorites: talent_ids[]
```

---

## Create job flow (studio) — mirrors SWM “Hire Help”

1. Tap **Hire Help**
2. Enter: Job name, date(s)/functions, event type, venue/area, role(s), offered day rate, notes
3. Search / filter talent OR pick from Favorites
4. Add people to **Job Queue** (reorder)
5. Choose offer type:
   - **Ranked Offer** (default)
   - **Instant Offer** (urgent)
6. Set response window
7. Start offer queue
8. Wait for Accept → Deposit → Confirmed

---

## Ranked Offer state machine

```
QUEUED → OFFERED (talent N) → ACCEPTED → DEPOSIT_PENDING → CONFIRMED
                           ↘ DECLINED → offer N+1
                           ↘ EXPIRED  → offer N+1
                           ↘ CANCELLED (studio)
If queue empty → UNFILLED
```

Invariant: at most **one** active OFFERED talent in Ranked mode.

---

## Instant Offer state machine

```
OFFERED_PARALLEL to all queue members
First ACCEPTED → others EXPIRED_LOST
→ DEPOSIT_PENDING → CONFIRMED
```

---

## Talent offer UX (mobile)

- Push + home badge: “New offer — Sat Wedding, ₹8,000, Madhapur”
- Screen: job summary, studio rating, map/area, countdown timer
- Actions: Accept / Decline
- On Accept: pay/confirm deposit instructions (Razorpay)

---

## Availability rules

- Search only returns talent marked **available** on all required function dates
- Accepting a confirmed job marks those dates **busy**
- Talent should sync personal calendar before accept (guidance copy, SWM-style)
