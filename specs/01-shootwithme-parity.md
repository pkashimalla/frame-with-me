# 01 — ShootWith.Me feature parity

Source audit: shootwith.me (Home, Features, Find Talent, Get Hired, Pricing, FAQs, Blog: first job / Instant Offer / rates).  
Every SWM capability below **must** appear in Frame With Me (mobile), unless marked deferred.

Legend: **P0** = MVP · **P1** = post-MVP · **P2** = later

---

## 1. Account types & career ladder

| SWM feature | Detail | FWM status |
|---|---|---|
| Studio account | Hire assistants, seconds, leads | **P0** |
| Assistant profile | Minimal experience; learn + earn; can start free/low rate | **P0** |
| Second shooter profile | Own gear + portfolio; independent coverage | **P0** |
| Lead / associate shooter | Seasoned pro covers for other studios; SWM suggests 5+ yrs lead experience | **P0** |
| Dual use | Same person can get hired and hire (studio + talent) | **P0** |
| Climb the ladder | Progress assistant → second → lead | **P1** (role upgrade path) |

---

## 2. Talent profile

| SWM feature | Detail | FWM status |
|---|---|---|
| Bio | Short about | **P0** |
| Profile picture | Avatar | **P0** |
| Location | City / area for search | **P0** |
| Portfolio | Work samples | **P0** |
| Hourly / default rate | Set own rate | **P0** (INR day rate default; hourly optional) |
| Interactive availability calendar | Days on / off | **P0** |
| Working radius | Cap local matching; studios prefer nearby | **P0** |
| Experience level | Shown on profile / filters | **P0** |
| Gear list / preferences | Camera, lenses, lights, etc. | **P0** |
| Roles available | Which roles they accept | **P0** |
| Shooting style | Represented on profile | **P1** |
| Reviews collected | After jobs | **P0** |

---

## 3. Studio side — find talent

| SWM feature | Detail | FWM status |
|---|---|---|
| Studio profile | Studio identity | **P0** |
| Search database (not job board) | Studio finds talent; talent does not spam-apply first | **P0** |
| Filter: date / availability | Must be free on job date | **P0** |
| Filter: location | Event location vs talent | **P0** |
| Filter: rate | Budget ceiling | **P0** |
| Filter: gear | Required kit | **P0** |
| Filter: experience | Role / years | **P0** |
| Filter: reviews / rating | Quality signal | **P0** |
| Curate shortlist | Assemble top options | **P0** |
| Favorites / go-to list | Save preferred talent for future searches | **P0** |
| Consistent profile layout | Same card structure for every talent | **P0** |

---

## 4. Jobs / events

| SWM feature | Detail | FWM status |
|---|---|---|
| Hire Help / create job | Entry point for studios | **P0** |
| Job name | Label | **P0** |
| Date | Shoot date | **P0** |
| Event type | Wedding, mitzvah, etc. | **P0** (India event types) |
| Additional job info / notes | Brief for candidates | **P0** |
| Role needed | Assistant / second / lead | **P0** |
| Job detail log | Both sides see who was hired + job details | **P0** |
| Manage upcoming hired jobs | Organized list of bookings | **P0** |

---

## 5. Offer queue (core SWM differentiator)

| SWM feature | Detail | FWM status |
|---|---|---|
| Job queue | Ordered list of selected talent | **P0** |
| Ranked Offers | Offer one-at-a-time in rank order | **P0** |
| User-defined response window | Timeout then auto-advance | **P0** |
| Decline → next in queue | Automatic | **P0** |
| Timeout → next in queue | Automatic | **P0** |
| Never offer to more than one person at a time (Ranked) | Exclusive sequential offer | **P0** |
| Instant Offers | Blast to all selected; first accept wins | **P0** |
| Accept / decline on talent side | Clear actions | **P0** |
| Expired offers hurt visibility (SWM guidance) | Soft ranking signal | **P1** |

---

## 6. Messaging & notifications

| SWM feature | Detail | FWM status |
|---|---|---|
| Built-in messenger | In-app chat | **P0** |
| Email sync / notify | Email for updates | **P1** |
| SMS sync / notify | SMS for updates | **P2** (cost); India uses WhatsApp instead |
| Unified conversation history | Don’t lose threads across channels | **P0** in-app; **P1** channel sync |
| Live chat support (SWM dashboard) | Customer success | **P2** (start with email / WhatsApp support) |

---

## 7. Accountability

| SWM feature | Detail | FWM status |
|---|---|---|
| Two-way reviews after job | Studio ↔ talent | **P0** |
| Professional accountability | Reliability / quality | **P0** |
| Help studios match brand | Reviews as hiring signal | **P0** |

---

## 8. Monetization (SWM model)

| SWM feature | Detail | FWM status |
|---|---|---|
| Studio free | SWM: studios free | **P0** (start free) |
| Talent subscription tiers | SWM: ~$49/yr by role (Assistant / Second / Lead) | **P1** INR pricing |
| No commissions (SWM) | SWM stays out of payments | **See India docs** — FWM adds optional UPI deposit + low take later |
| No contracts via platform (SWM) | Parties handle offline | **P0** optional template **P1** |
| No payment processing (SWM) | Cash/check/Venmo offline | **Overridden for India** — see India customizations |

---

## 9. Positioning / UX principles from SWM

| Principle | FWM |
|---|---|
| Not a Facebook job board | Yes — search + offer, not “post and wait for 30 comments” |
| Talent sets availability and waits for offers | Yes |
| Studios get instant shortlists | Yes |
| Save time vs social media | Yes |
| Entry path for students / beginners (assistant free/low) | Yes |
| Side-income for part-time seconds | Yes |

---

## 10. Explicit SWM non-features (we still document)

SWM deliberately does **not**:

- Handle contracts
- Handle payments

Frame With Me **keeps parity on hiring UX** but **adds India payment/deposit** because no-shows are the #1 local failure mode. See `02-india-customizations.md`.
