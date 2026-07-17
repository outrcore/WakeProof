# Roadmap

The roadmap is gate-based rather than calendar-based. A milestone is complete only when its exit criteria are demonstrated on physical devices.

## Milestone 0 — Product operating system

**Goal:** Establish the product thesis, architecture, risks, metrics, and execution rules before code expands.

### Deliverables

- [x] Product brief
- [x] Feature classification
- [x] Subscription hypothesis
- [x] Architecture proposal
- [x] Reliability and testing policies
- [x] Smart-wake decision
- [x] Initial backlog and risk register
- [ ] Select code license
- [ ] Establish issue labels and milestones
- [ ] Add ADR template
- [ ] Add pull-request template

### Exit criteria

- Every MVP feature maps to the core wake promise.
- Deferred features have explicit revisit triggers.
- The next engineering gate has a binary pass/fail definition.

---

## Milestone 1 — AlarmKit feasibility gate

**Goal:** Prove the complete alarm lifecycle before building polished UI.

### Required spike

1. Schedule a one-shot AlarmKit alarm.
2. Schedule a recurring AlarmKit alarm.
3. Attach stop and secondary App Intents.
4. Route an alert action to the exact WakeProof session.
5. Snooze and verify the system re-alerts.
6. Reconcile AlarmKit state with the local store.
7. Repeat while the app is:
   - foregrounded;
   - backgrounded;
   - force-quit or terminated;
   - behind the Lock Screen;
   - under Silent Mode;
   - under a Focus;
   - after device reboot;
   - after time-zone changes;
   - across daylight-saving transitions.
8. Test permission denial and later authorization.
9. Test overlapping and rapidly edited alarms.

### Exit criteria

- A written behavior matrix exists for every tested state.
- Snooze re-alert is demonstrated repeatedly on at least two physical iPhone models.
- The mission handoff semantics are understood, including when system sound stops.
- Known gaps have deterministic fallbacks.
- No design work is allowed to mask an unresolved lifecycle failure.

**Kill/rethink condition:** If the system cannot support a trustworthy mission handoff and re-alert lifecycle, redesign the product around the behavior AlarmKit can guarantee before continuing.

---

## Milestone 2 — Domain foundation

**Goal:** Build a testable alarm and wake-session engine independent of SwiftUI screens.

### Scope

- Alarm model and recurrence model
- Mission protocol model
- Wake-session state machine
- AlarmKit adapter
- Local persistence
- Alarm reconciliation service
- App Intent router
- Structured local logging
- Test alarm
- Reliability Center foundation
- Dependency injection and clock abstraction

### Exit criteria

- State-machine tests cover all valid and invalid transitions.
- Local and system alarm state can be reconciled after restart.
- The test alarm exercises the same path as a real alarm.
- No business logic is embedded exclusively in view code.

---

## Milestone 3 — Physical proof

**Goal:** Force a credible out-of-bed action without trapping honest users.

### Scope

- Photo target registration using a short guided scan
- Live multi-frame camera capture
- No photo-library or pasteboard submission
- Randomized capture instruction
- Local feature extraction and matching
- Basic liveness/replay resistance
- Barcode/QR mission
- Guided alignment and low-light handling
- Emergency escape
- Verification diagnostics for beta

### Exit criteria

- Honest-pass target is met across representative lighting and device conditions.
- Known cheats are tested and measured.
- Camera permission revocation has a safe fallback.
- No raw target or attempt image leaves the device by default.
- The user can always stop the alarm through a bounded emergency path.

---

## Milestone 4 — Stay-awake loop

**Goal:** Measure success as remaining awake, not merely completing a mission.

### Scope

- Optional cognitive mission
- Math and typing challenges
- Rotating challenge variants
- Delayed wake check
- Escalation and re-alert
- Commitment lock window
- Session outcome and streak
- Privacy-safe wake card
- Missed-check diagnostics

### Exit criteria

- A missed delayed check always enters a documented escalation path.
- Users cannot accidentally create an endless or impossible loop.
- Wake cards contain no photo, health, exact-location, or sensitive room data.
- Beta users report lower return-to-bed behavior than their baseline.

---

## Milestone 5 — Monetization and private alpha

**Goal:** Validate willingness to pay without weakening trust.

### Scope

- Three verified mornings of full access
- Free-tier entitlements
- StoreKit 2 products
- Annual-first paywall
- Restore purchases
- Subscription-state resilience
- Purchase and refund analytics
- Private alpha with adversarial testers

### Alpha cohort

Start with 20–30 people who self-identify as heavy snoozers. Explicitly ask them to:

- spoof photos;
- use similar colors and substitute objects;
- alter lighting;
- revoke permissions;
- edit alarms at the last moment;
- force-quit and reboot;
- travel across time zones;
- miss wake checks;
- trigger emergency escape;
- attempt every known shortcut.

### Exit criteria

- No unresolved severity-0 or severity-1 bugs.
- Alarm reliability meets the alpha SLO.
- Honest photo pass and escape rates are within target.
- At least one pricing/paywall hypothesis can be evaluated with clean data.

---

## Milestone 6 — TestFlight beta

**Goal:** Validate retention, reliability, onboarding, and support load at broader scale.

### Scope

- 100–500 external testers
- Crash and alarm-incident monitoring
- In-app incident report with diagnostic bundle
- Accessibility pass
- Localization-ready strings
- App Store metadata draft
- Support runbook
- UGC creator seeding

### Exit criteria

- Reliability SLO holds across the beta cohort.
- D7 verified-wake retention is directionally strong.
- Photo false rejects do not dominate support.
- Subscription cancellation and refund reasons are understood.
- At least five repeatable creative concepts produce credible content.

---

## Milestone 7 — App Store launch

**Goal:** Launch a narrow, trusted product with organic distribution potential.

### Launch scope

- iPhone-first iOS 26+ app
- Core wake protocol
- Photo, barcode, math, and typing
- Snooze and delayed wake check
- Commitment lock
- Emergency escape
- Reliability Center
- Free and Pro plans
- Referral-ready links and wake cards

### Exit criteria

- Release checklist complete.
- Privacy policy and App Store disclosures match actual data behavior.
- Support and incident response are staffed.
- No health, sleep-stage, or “uncheatable” claim appears without support.
- Production telemetry can distinguish alert, routing, mission, and wake-check failures.

---

## Milestone 8 — Post-PMF expansion

Ordered by evidence, not excitement:

1. Apple Watch companion for haptic alerts and lightweight confirmations
2. Apple Health read-only insights after waking
3. Friend accountability
4. Creator protocol packs
5. Smart Wake Window beta
6. Apple Watch live inference improvements
7. Social wake races
8. Carefully reviewed commitment stakes
9. Android feasibility

See [smart-wake.md](smart-wake.md) for the criteria required before Smart Wake enters active development.
