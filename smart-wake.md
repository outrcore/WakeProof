# Smart Wake Strategy

## Decision

**Do not include Apple Watch/Apple Health “optimal wake time” in the MVP.**

Build WakeProof’s deterministic core first: the alarm must fire by the user’s chosen time, require credible proof, re-alert after snooze, and verify that the user stayed awake.

Smart Wake should remain a documented post-PMF expansion called **Smart Wake Window**, not the central launch promise.

## Why defer it

### 1. It changes the product promise

WakeProof’s first promise is deterministic:

> “You will be alerted by your latest acceptable wake time, and the app will verify your wake protocol.”

Smart wake is probabilistic:

> “The app estimates a favorable moment within a window.”

Combining them too early creates confusing failure attribution. If a user feels tired, was the stage estimate wrong, did the Watch disconnect, was the sensor data sparse, or did the core alarm fail?

### 2. It requires another critical device

A Watch-dependent feature excludes users who:

- do not own an Apple Watch;
- charge it overnight;
- do not wear it consistently;
- disable health permissions;
- have poor Watch battery;
- have an unsupported or disconnected device.

The core value must work on iPhone alone.

### 3. Apple provides a path, but it is a separate engineering product

Apple’s WatchKit supports a **smart alarm** `WKExtendedRuntimeSession`:

- scheduled to start within the next 36 hours;
- runs in the background;
- lasts up to 30 minutes;
- can monitor heart rate and motion;
- can trigger repeating haptics and a system alarm alert.

That is promising, but it requires:

- a watchOS target;
- background-mode entitlement;
- scheduling and cancellation reconciliation;
- battery and resource testing;
- phone/watch state coordination;
- hard fallback at the latest wake time;
- failure handling when the Watch is unavailable.

Apple documentation:
- https://developer.apple.com/documentation/watchkit/using-extended-runtime-sessions
- https://developer.apple.com/documentation/watchkit/wkextendedruntimesession/
- https://developer.apple.com/documentation/watchkit/wkextendedruntimesession/notifyuser(haptictype:repeathandler:)

### 4. “Optimal” is scientifically stronger than the evidence supports

Sleep inertia is real, and waking from slow-wave sleep can be associated with worse impairment in some research. Other controlled work has found no detectable effect of sleep stage at awakening, while circadian phase, prior sleep loss, and task type also matter.

Consumer wrist wearables infer sleep stages from indirect signals rather than EEG. A 2025 comparison of six commercial wearables against polysomnography found significant differences for several sleep measures, including light sleep, even though performance varied by stage and device.

Therefore, future language should be:

- “lighter-sleep estimate”;
- “Smart Wake Window”;
- “tries to wake you at a more favorable moment”;
- “always alerts by your latest time.”

Avoid:

- “guaranteed optimal wake time”;
- “clinically accurate sleep stage”;
- “prevents sleep inertia”;
- diagnostic claims.

Evidence:
- https://pubmed.ncbi.nlm.nih.gov/12531174/
- https://pubmed.ncbi.nlm.nih.gov/10188130/
- https://academic.oup.com/sleepadvances/article/6/2/zpaf021/8090472
- https://pubmed.ncbi.nlm.nih.gov/33018943/

### 5. Health data raises privacy and policy obligations

Apple Health data is sensitive. Access must be requested in context and used only for a direct user benefit. Health, fitness, motion, and camera-derived information must not drive advertising or marketing profiles.

Apple sources:
- https://developer.apple.com/documentation/healthkit
- https://developer.apple.com/design/human-interface-guidelines/healthkit
- https://developer.apple.com/app-store/review/guidelines/

## Recommended sequence

### Phase A — iPhone proof-of-wake MVP

No Apple Health permission. No Watch requirement.

Measure:

- scheduled alert reliability;
- snooze re-alert;
- physical-proof success;
- delayed-check success;
- return-to-bed self-report;
- retention and willingness to pay.

### Phase B — Apple Health read-only insights

After the core wake session is complete, optionally read authorized historical data:

- sleep duration;
- Apple-provided sleep stages;
- heart rate;
- resting heart rate;
- HRV;
- respiratory rate where available.

Initial use cases:

- compare wake outcomes with prior-night duration;
- show trends without causal claims;
- identify whether Watch-owning users are a large segment;
- learn which data is actually present and timely.

Do not use this phase to dynamically change tonight’s alarm.

### Phase C — Apple Watch companion

Add:

- haptic reinforcement;
- next-alarm status;
- simple wake-check confirmation;
- permission and connectivity diagnostics;
- Watch battery readiness;
- optional mission handoff.

Prove that Watch support increases success rather than adding support incidents.

### Phase D — Smart Wake Window beta

User configures:

- **earliest acceptable time**;
- **latest mandatory time**;
- window of 15 or 30 minutes;
- desired haptic/sound behavior;
- deterministic fallback.

Within the window:

1. Start the Watch smart-alarm session.
2. Read permitted motion and heart-rate signals.
3. Compute a local wake-readiness score.
4. Alert when score crosses a conservative threshold.
5. If no threshold is reached, alert at the latest mandatory time.
6. Begin the normal WakeProof protocol on iPhone.
7. Record confidence and outcome without claiming clinical stage certainty.

### Phase E — Personalized model

Only after enough opt-in outcome data exists:

- personalize thresholds by user;
- account for habitual wake pattern;
- model signal availability and confidence;
- include prior-night duration and historical patterns;
- evaluate whether the model improves self-reported alertness and protocol completion.

## Entry criteria for active development

Smart Wake Window moves from deferred to active only when all are true:

- Core iPhone alert SLO is met for at least two production releases.
- Snooze and delayed-check incidents are below threshold.
- D30 retention supports continued investment.
- A meaningful percentage of retained users own and wear an Apple Watch overnight.
- Watch smart-alarm sessions are reliable on a representative device matrix.
- A deterministic latest-time fallback is proven.
- Legal/privacy review is complete.
- The team has a testable outcome metric beyond “the algorithm ran.”
- Marketing language has been reviewed for evidence and App Review risk.

## Product metric for Smart Wake

Do not optimize for predicted sleep stage alone.

Primary experiment outcome:

> Difference in self-reported wake alertness and verified-protocol completion between fixed-time and Smart Wake Window mornings.

Guardrails:

- no increase in late wake-ups;
- no increase in missed alarms;
- no material Watch battery complaints;
- no increase in support incidents;
- no deceptive confidence presentation.

## Commercial role

Smart Wake can become:

- a Pro retention feature;
- an Apple Watch acquisition hook;
- a differentiated upgrade after trust is established;
- a content angle for quantified-self and fitness users.

It should not be allowed to delay the initial product or dilute the “Prove you’re awake” brand.
