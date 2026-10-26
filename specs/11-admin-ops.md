# 11 — Admin web ops

Separate **web app** for platform team. Not in Android APK.

## Capabilities (MVP)

| Action | Effect |
|---|---|
| Suspend / ban user | Block auth; hide from search; cancel open offers |
| Force-cancel job | Terminal state; notify both parties; deposit policy |
| Flag refund | Ops marks deposit refund; executes via PaymentPort |
| Verify badge | Toggle verified on talent |
| View user/jobs (support) | Least privilege; audited |
| Audit log | Immutable-ish append of admin actions |

## Non-goals
- Full analytics BI
- Editing portfolios as admin (unless abuse takedown hide)

## Auth
Allowlisted operators only (`admin` role claim).
