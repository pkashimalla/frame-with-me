# 06 — Agentic features

Differentiators beyond ShootWith.Me. **Assistive, not fully autonomous** for wedding-critical hires.

---

## Agent principles

1. Studio always confirms before offers go live  
2. Agent may auto-advance Ranked queue (already SWM automation) and suggest backups  
3. Never hide rates or invent availability  
4. Log every agent action for audit  

---

## A1 — Hire assistant (P1)

**Input (voice or text):**  
“Need one second shooter and one cine for Saturday sangeet in Madhapur, budget 8k each, Telugu OK, own 70-200 preferred.”

**Output:**
- Parsed job draft (dates, roles, location, budgets, gear, language)
- Ranked shortlist with reasons
- One-tap “Start Ranked Offer” / “Start Instant Offer”

---

## A2 — Smart shortlist (P1)

Ranks talent using: availability, radius, rate fit, gear, rating, response rate, past work with this studio, style tags.

---

## A3 — Queue chase (P1)

On decline/timeout:
- Notify studio
- Optionally auto-append similar backups (studio opt-in)
- Draft WhatsApp/push copy

---

## A4 — Freelancer co-pilot (P1)

- “Jobs I can take this weekend”
- Suggest rate adjustments if low offer volume (SWM FAQ guidance, automated gently)
- Draft decline messages

---

## A5 — No-show recovery (P1)

If confirmed talent cancels <24h:
- Instant Offer to favorites + available nearby
- Suggest +₹ bump for urgency

---

## Out of scope for early agents

- Auto-accept jobs for talent without confirmation  
- Auto-pay anyone  
- Client/couple facing booking  

---

## Tech notes (lean)

- LLM for parse + ranking explanation  
- Deterministic filters in SQL/PostGIS for availability/radius/rate  
- Hard caps on API spend  
