# Reliability

WakeProof is a high-stakes utility. Reliability is a user-facing feature and the primary release gate.

## Reliability model

Separate the wake lifecycle into independently measurable layers:

1. **Intent:** user configured an enabled alarm.
2. **Scheduling:** WakeProof successfully registered the expected AlarmKit record.
3. **System alert:** AlarmKit entered the alerting state at the expected time.
4. **Handoff:** the user action routed to the correct wake session.
5. **Mission:** the proof flow remained usable.
6. **Snooze:** countdown ended and re-alert occurred.
7. **Wake check:** delayed verification occurred or escalated.
8. **Completion:** terminal session state was persisted.
9. **Reconciliation:** app and system state agreed after restart.

A generic “alarm failed” event is not sufficient.

## Initial internal SLO targets

These are engineering targets, not public guarantees.

| Measure | Target |
|---|---:|
| Scheduled eligible alarms produce expected AlarmKit alert | ≥ 99.99% |
| Snoozed alarms re-alert | ≥ 99.99% |
| Alert action routes to correct session | ≥ 99.9% |
| Crash-free wake sessions | ≥ 99.9% |
| Delayed checks either present or deterministically escalate | ≥ 99.9% |
| Alarm state reconciles after restart | ≥ 99.99% |
| Emergency escape reachable from every mission state | 100% in test matrix |
| Sensitive data in analytics/logs | 0 events |

“Eligible” must be explicitly defined to exclude states the system prevents and that Reliability Center clearly communicates, such as denied AlarmKit authorization.

## User-visible Reliability Center

Show:

- AlarmKit authorization status
- Next enabled alarm and local time
- Whether local and system records agree
- Last successful test alarm
- Camera permission
- Notification/alert dependencies if applicable
- Time-zone and daylight-saving review status
- Watch readiness when Watch support exists
- Last reliability incident summary
- A one-tap test-alarm flow

Avoid false certainty such as a green “guaranteed” badge.

## Alarm reconciliation triggers

Run reconciliation on:

- app launch and foreground activation;
- AlarmKit authorization change;
- AlarmKit alarm update sequence;
- alarm create/edit/delete;
- significant time change;
- time-zone change;
- app version migration;
- device reboot detection where possible;
- subscription entitlement change;
- Watch connectivity change later.

## Safety invariants

- Every active alarm can be stopped through a documented path.
- Subscription status cannot remove the stop path.
- Mission failure cannot create an infinite alert loop.
- Snooze cannot silently disable recurrence.
- Local edits must not leave an orphaned system alarm.
- Deleting local state must not prevent stopping a system alert.
- A probabilistic smart wake can never move the alert past the latest mandatory time.
- The test alarm uses the same scheduling and routing path as production.

## Diagnostic event schema

Minimum privacy-safe fields:

- event name;
- event timestamp;
- installation-scoped anonymous ID;
- hashed alarm ID;
- hashed wake-session ID;
- app build;
- OS version;
- device family;
- prior and new state;
- AlarmKit authorization state;
- reason code;
- duration;
- recurrence type;
- whether app was active/backgrounded/terminated when known.

Never include:

- raw photo;
- photo embedding;
- barcode payload;
- typed phrase;
- exact room target name unless user-authored text is locally redacted;
- health samples;
- exact location;
- contact information.

## Incident response

### S0/S1 workflow

1. Preserve local diagnostic bundle with user consent.
2. Determine whether a system alert occurred.
3. Determine whether the local alarm and AlarmKit record matched.
4. Reconstruct state transitions.
5. Reproduce on the same OS/device class.
6. Add or improve regression coverage.
7. Decide whether release rollback, feature flag, or hotfix is required.
8. Publish an internal incident note.

### Release blocking rules

Block release when:

- any known S0 exists;
- any unmitigated S1 exists;
- AlarmKit behavior changed on the target OS and has not been revalidated;
- snooze soak test fails;
- emergency escape path fails;
- analytics privacy audit fails;
- migration can lose or duplicate enabled alarms.

## Reliability experiments

- 100 consecutive snooze cycles
- 30-day recurring alarm soak
- Rapid create/edit/delete stress
- Multiple alarms within five minutes
- Force-quit at every state transition
- Reboot before alert
- Clock adjustment forward/backward
- Time-zone travel
- DST spring and fall transitions
- Low battery and Low Power Mode
- Storage pressure
- Camera permission changes
- App update between scheduling and alert
- Entitlement expiry between scheduling and alert

## Public communication

When a real incident affects users:

- acknowledge the concrete failure;
- state affected versions and conditions when known;
- provide a safe workaround;
- do not blame the user;
- do not claim an alarm was reliable merely because the app did not crash;
- document the fix and validation performed.
