# Testing

## Test pyramid

1. Domain unit tests
2. Framework-adapter contract tests
3. Persistence and migration tests
4. Component/UI tests
5. Physical-device lifecycle tests
6. Adversarial photo tests
7. Long-running soak tests
8. Human alpha/beta protocols

Simulator-only success is not evidence of alarm reliability.

## Required device matrix

At minimum:

- oldest supported iPhone class capable of iOS 26;
- current standard iPhone;
- current Pro iPhone;
- at least one device with limited storage and older battery;
- multiple iOS 26 point releases;
- light and dark appearance;
- common Dynamic Type sizes;
- VoiceOver and Switch Control.

For Apple Watch work later:

- older supported Watch;
- current standard Watch;
- current Ultra;
- watchOS point-release matrix;
- paired, disconnected, low battery, charging, and airplane-mode states.

## Alarm lifecycle matrix

For each alarm type—one-shot, recurring, snoozed, delayed check—test:

| State | Required |
|---|---|
| App foreground | Yes |
| App background | Yes |
| App terminated | Yes |
| Phone locked | Yes |
| Silent Mode | Yes |
| Focus active | Yes |
| Low Power Mode | Yes |
| Device rebooted | Yes |
| App updated | Yes |
| Time zone changed | Yes |
| DST transition | Yes |
| Authorization changed | Yes |
| Multiple alarms overlap | Yes |
| Subscription changes | Yes |

Record expected and observed system behavior, not only pass/fail.

## State-machine tests

Cover:

- every valid transition;
- every invalid transition;
- duplicate intent delivery;
- late callbacks;
- restart during each state;
- storage failure;
- clock jump;
- stale protocol version;
- missing alarm;
- orphaned AlarmKit record;
- emergency escape from every active mission;
- delayed check after app termination.

Use an injected clock and deterministic IDs.

## Photo-verification test corpus

### Honest variations

- bright daylight;
- dim room;
- warm and cool lighting;
- flash on/off;
- different angles;
- different distances;
- partial occlusion;
- moved target;
- background clutter change;
- camera lens differences;
- left/right hand;
- motion blur;
- accessibility-assisted capture.

### Adversarial variations

- screenshot on another phone;
- printed photo;
- laptop or tablet display;
- prerecorded video;
- similar-color object;
- same object in a different room;
- cropped image;
- mirror/reflection;
- target held near bed;
- altered brightness/contrast;
- AI-generated substitute image;
- replay with simulated camera motion.

### Metrics

- honest-pass rate;
- false-reject rate;
- cheat-rejection rate by attack;
- median attempts;
- median verification time;
- fallback/escape rate;
- performance and thermal cost.

Never collect a test corpus from real user bedrooms without explicit, informed consent and a documented retention policy.

## Accessibility testing

Required flows:

- create alarm;
- understand next alarm;
- snooze;
- complete each supported mission;
- invoke emergency escape;
- recover from camera failure;
- manage subscription;
- interpret Reliability Center.

Test:

- VoiceOver;
- Dynamic Type;
- Reduce Motion;
- Increase Contrast;
- color-independent status;
- Switch Control;
- one-handed interaction;
- hearing limitations;
- motor limitations;
- cognitive load while half awake.

A physical mission must always have a configured accessible alternative.

## Monetization testing

- first, second, and third verified mornings;
- emergency escape does not count;
- test alarm does not count;
- purchase success/failure/cancel;
- restore purchases;
- offline entitlement cache;
- refund/revocation;
- grace period;
- expiry while alarm scheduled;
- expiry while alarm ringing;
- downgrade with too many alarms;
- reinstall;
- family sharing decision if supported.

## Soak tests

- 100 snooze/re-alert cycles;
- 1,000 schedule/cancel operations;
- 30-day recurring schedule;
- 24-hour app lifecycle with repeated backgrounding;
- photo verifier thermal/memory loop;
- database migration with large session history;
- repeated App Intent delivery.

## Beta test script

Ask testers to intentionally:

- cheat;
- misunderstand onboarding;
- configure an impossible target;
- move the target;
- travel;
- revoke permissions;
- close the app;
- restart the phone;
- edit alarms near the lock window;
- miss the wake check;
- use emergency escape;
- downgrade from Pro;
- use accessibility features;
- report whether they returned to bed.

## Release evidence

Every release candidate needs:

- automated test report;
- physical-device alarm matrix;
- snooze soak result;
- migration result;
- privacy log audit;
- accessibility checklist;
- known-issues review;
- crash-free wake-session result;
- approval against [release-checklist.md](release-checklist.md).
