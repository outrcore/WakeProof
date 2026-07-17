# Bugs

There is no application implementation in the repository yet, so there are no verified runtime bugs. This file defines how bugs are classified and tracks known failure hypotheses that must be disproven.

## Severity

| Severity | Definition | Examples | Response |
|---|---|---|---|
| S0 — Safety critical | Alarm cannot be stopped safely, repeated harmful behavior, or data/privacy breach | Endless alarm with no escape; private image uploaded unexpectedly | Stop release, immediate incident response |
| S1 — Core reliability | A scheduled alarm fails, snooze fails to re-alert, wrong alarm routes, or wake-check escalation fails | Missed work alarm; stale recurrence | Block release; investigate as production incident |
| S2 — Major | Core mission unusable for a meaningful segment but deterministic fallback works | Camera falsely rejects repeatedly; barcode scanner unavailable | Prioritize current milestone |
| S3 — Moderate | Degraded or confusing experience without core failure | Incorrect streak; delayed UI update | Schedule normally |
| S4 — Minor | Cosmetic, copy, spacing, or low-impact issue | Truncation on one screen | Batch with polish |

## Bug report template

```markdown
### Summary

### Severity

### Environment
- App version:
- iOS/watchOS version:
- Device:
- Locale/time zone:
- AlarmKit authorization:
- Camera/Health permissions:
- App foreground/background/terminated:

### Preconditions

### Exact steps

### Expected

### Actual

### Did a system alert occur?

### Could the alarm be stopped safely?

### Snooze or recurrence involved?

### Diagnostic bundle ID

### Screenshots/video
Do not attach private target or attempt photos unless explicitly redacted and consented.

### Reproducibility
- [ ] Always
- [ ] Intermittent
- [ ] Once
```

## Initial failure watchlist

| ID | Failure hypothesis | Severity if confirmed | Required test |
|---|---|---:|---|
| BUG-RISK-001 | AlarmKit alert does not appear after app termination | S1 | Repeated physical-device lifecycle matrix |
| BUG-RISK-002 | Snooze countdown does not re-alert | S1 | 100-cycle automated/manual soak |
| BUG-RISK-003 | Recurring alarm disappears after first fire | S1 | Multi-day recurrence test |
| BUG-RISK-004 | App Intent routes to wrong alarm session | S1 | Concurrent alarms with unique protocols |
| BUG-RISK-005 | Local alarm exists but AlarmKit record is missing | S1 | Reconciliation after deletion/reboot |
| BUG-RISK-006 | Alarm fires at wrong local time after time-zone change | S1 | Travel simulation and real travel |
| BUG-RISK-007 | Daylight-saving transition duplicates or skips alarm | S1 | Spring/fall boundary tests |
| BUG-RISK-008 | Photo accepts a screenshot or screen replay | S2 | Adversarial replay corpus |
| BUG-RISK-009 | Photo rejects honest target after lighting change | S2 | Multi-light and low-light corpus |
| BUG-RISK-010 | Camera permission revoked during active alarm | S1/S2 | Revoke before and during session |
| BUG-RISK-011 | Emergency escape is unavailable or loops | S0 | Every mission and error-state path |
| BUG-RISK-012 | Subscription expiry disables ability to stop alarm | S0 | Entitlement transition tests |
| BUG-RISK-013 | Multiple alarms overwrite shared handoff state | S1 | Overlap and rapid-fire tests |
| BUG-RISK-014 | Force-close during proof loses terminal state | S2 | Kill/relaunch at every transition |
| BUG-RISK-015 | Delayed check is missed without escalation | S1 | Background/terminated wake-check test |
| BUG-RISK-016 | Accessibility user cannot complete or escape | S0/S2 | VoiceOver, Switch Control, motor paths |
| BUG-RISK-017 | Raw photo or barcode appears in analytics/logs | S0 | Privacy log audit |
| BUG-RISK-018 | Test alarm follows a different path than real alarm | S1 | Path and event-schema comparison |
| BUG-RISK-019 | Alarm sound stops before required mission can begin | S1/product blocker | AlarmKit handoff spike |
| BUG-RISK-020 | Device reboot invalidates scheduled alarms silently | S1 | Reboot and reconcile tests |

## Incident policy for missed alarms

A report that “the alarm did not ring” is never closed as user error without evidence.

Investigation must separate:

1. alarm was not scheduled;
2. AlarmKit authorization was unavailable;
3. system alert failed;
4. alert occurred but user did not perceive it;
5. App Intent handoff failed;
6. mission UI failed;
7. snooze/re-alert failed;
8. recurrence was missing;
9. time calculation was wrong;
10. telemetry was insufficient.

Every S1 incident should produce one of:

- a reproducible defect;
- an instrumented hypothesis and new test;
- a clear unsupported-system condition shown in Reliability Center;
- a product change that removes ambiguity.

## Regression rule

Every confirmed S0–S2 bug requires a regression test or documented reason that automation is impossible. “Fixed manually” is not sufficient.
