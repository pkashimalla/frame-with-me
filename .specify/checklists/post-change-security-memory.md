# Post-change gate — Security & Memory

**Agents MUST complete this after every code change** before claiming work done.  
Copy the result into the chat reply (short form OK).

## Security

- [ ] No secrets/API keys committed or logged
- [ ] New endpoints/queries enforce auth + authorization (RLS or equivalent)
- [ ] Inputs validated (length, type, enum); no raw SQL string concat
- [ ] PII not written to console/analytics (phone, OTP, tokens, UPI ids)
- [ ] File uploads restricted (type/size) if touched
- [ ] Admin actions would be auditable if this change is admin-related
- [ ] Deep links / wa.me payloads don’t leak private job details beyond need

## Memory / lifecycle

- [ ] No new `addListener` / realtime channel / `setInterval` without cleanup
- [ ] React: effects return cleanup; no stale closures holding large lists
- [ ] Lists paginated; no “fetch all” introduced
- [ ] Images use bounded size / recycling-friendly lists
- [ ] AbortController or equivalent for in-flight requests on unmount where applicable

## Constitution

- [ ] Change aligns with `.specify/memory/constitution.md`
- [ ] Notification/payment code goes through ports/adapters if touched
- [ ] UI uses design-system components + `t()` for strings if user-facing

## Result

```
Security: PASS | FAIL — notes: …
Memory:   PASS | FAIL — notes: …
```
