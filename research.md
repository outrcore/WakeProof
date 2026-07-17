# Research

This document records evidence, open questions, and experiments. Product claims must distinguish observed facts, planning assumptions, and hypotheses.

## Established observations

- A meaningful segment repeatedly snoozes and experiences difficulty becoming fully alert after waking.
- Mission-based alarm apps already offer math, memory, typing, movement, barcode, photo, and multi-mission flows.
- A single mission does not prove sustained wakefulness.
- Photo verification has an inherent false-accept/false-reject tradeoff.
- Alarm reliability failures dominate user trust.
- Apple provides AlarmKit on iOS 26 for system-level alarms.
- Apple Watch supports a 30-minute smart-alarm extended runtime session.
- Consumer wearables infer sleep stages imperfectly compared with polysomnography.
- Evidence on sleep-stage-specific sleep inertia is mixed and affected by circadian phase, prior sleep, and measurement choice.

## Planning assumptions to validate

- Heavy snoozers will pay for stronger proof and stay-awake verification.
- Three verified mornings is a better activation/paywall unit than a timed trial.
- Multi-frame registration materially improves photo robustness.
- A delayed wake check reduces return-to-bed behavior.
- Commitment lock windows improve outcomes without causing excessive escape or deletion.
- UGC centered on failed cheating can acquire users efficiently.
- A meaningful retained-user segment owns and wears Apple Watch overnight.

## Open technical questions

### AlarmKit

- Exactly when does system audio stop after each alert action?
- Can the required mission remain psychologically and technically coupled to the alert?
- How does recurrence behave after stop, snooze, update, app removal, and reboot?
- What states are exposed through `alarmUpdates`?
- How should one-shot fired alarms be reconciled after AlarmKit deletes them?
- How do overlapping alarms present?
- What happens during OS updates or device restore?

### Photo proof

- Which Vision representations are stable across viewpoint and lighting?
- What local-keypoint method is performant enough on supported devices?
- Which replay heuristics provide value without excessive false rejects?
- What registration guidance yields the best honest-pass rate?
- How should thresholds adapt per user?
- How can accessibility alternatives preserve proof quality?

### Stay-awake check

- What delay best predicts return-to-bed behavior?
- Does one follow-up check suffice?
- Is a different mission more effective than repeating the first?
- How should escalation avoid waking partners repeatedly?
- What user feedback can estimate actual return to sleep?

### Subscription

- Does one free alarm support organic growth or reduce paid conversion too much?
- Does limited lifetime pricing accelerate early cash or damage recurring revenue?
- Which paywall moment preserves trust?
- How price-sensitive are students versus shift workers?

### Apple Watch / Smart Wake

- Can the smart-alarm session access sufficiently timely heart-rate and motion signals without inappropriate workout semantics?
- What is the real battery impact?
- What happens if the session does not start?
- Can phone and Watch alarms coexist without double-alert confusion?
- Does Smart Wake improve alertness or only perceived sophistication?
- What percentage of WakeProof’s retained users wear Watch overnight?

## Experiment queue

| ID | Hypothesis | Experiment | Success metric |
|---|---|---|---|
| R-001 | Delayed check reduces return to bed | A/B one check vs none | Lower self-reported return to bed |
| R-002 | Multi-frame beats single-image matching | Offline honest/adversarial corpus | Better ROC and lower false reject |
| R-003 | Random liveness blocks screen replay | Replay attack test | Higher rejection with small honest cost |
| R-004 | Three-morning activation increases conversion quality | Cohort comparison | Net revenue with equal/better refund |
| R-005 | Lock window improves outcomes | Opt-in beta | More completed wakes, acceptable escape rate |
| R-006 | Cheat Test improves sharing | Onboarding A/B | Share/referral lift |
| R-007 | Smart Wake improves alertness | Later randomized crossover | Alertness lift with no late-wake increase |

## Source register

### Product and market

- CDC sleep data: https://www.cdc.gov/nchs/products/databriefs/db559.htm
- Snoozing study: https://www.nature.com/articles/s41598-025-99563-y
- RevenueCat subscription benchmarks: https://www.revenuecat.com/state-of-subscription-apps/
- Apple Small Business Program: https://developer.apple.com/app-store/small-business-program/

### Apple alarm and watch technology

- AlarmManager: https://developer.apple.com/documentation/alarmkit/alarmmanager
- Alarm configuration and intents: https://developer.apple.com/documentation/alarmkit/alarmmanager/alarmconfiguration/alarm(schedule:attributes:stopintent:secondaryintent:sound:)
- Alarm scheduling: https://developer.apple.com/documentation/alarmkit/alarmmanager/schedule(id:configuration:)
- AlarmKit WWDC session: https://developer.apple.com/videos/play/wwdc2025/230/
- Watch extended runtime sessions: https://developer.apple.com/documentation/watchkit/using-extended-runtime-sessions
- Watch smart-alarm haptics: https://developer.apple.com/documentation/watchkit/wkextendedruntimesession/notifyuser(haptictype:repeathandler:)

### Apple Health and privacy

- HealthKit overview: https://developer.apple.com/documentation/healthkit
- Sleep analysis type: https://developer.apple.com/documentation/HealthKit/HKCategoryTypeIdentifier/sleepAnalysis
- Health design guidance: https://developer.apple.com/design/human-interface-guidelines/healthkit
- App Review Guidelines: https://developer.apple.com/app-store/review/guidelines/

### Sleep-stage and inertia evidence

- Sleep inertia review: https://pubmed.ncbi.nlm.nih.gov/12531174/
- Sleep-stage null-effect study: https://pubmed.ncbi.nlm.nih.gov/10188130/
- Circadian sleep inertia study: https://journals.sagepub.com/doi/10.1177/0748730408318081
- Wearable validation against PSG: https://academic.oup.com/sleepadvances/article/6/2/zpaf021/8090472
- Smart alarm stage-prediction paper: https://pubmed.ncbi.nlm.nih.gov/33018943/
- Light intervention: https://pubmed.ncbi.nlm.nih.gov/35102669/

## Research standards

- Prefer Apple documentation for API behavior.
- Prefer primary peer-reviewed papers for scientific claims.
- Distinguish lab outcomes from consumer real-world effectiveness.
- Record study size and limitations.
- Do not treat competitor marketing copy as validation.
- Date every market snapshot.
- Re-run current searches before final App Store copy or health claims.
