# Tasks

This backlog is intentionally ordered around risk retirement. Do not start with visual polish or a large mission library.

## Now — Milestone 1: AlarmKit feasibility

### P0

- [ ] **WP-001 — Create minimal iOS 26 Xcode project**
  - Acceptance: builds on a physical iPhone; bundle, signing, and AlarmKit entitlement configured.
- [ ] **WP-002 — Request and display AlarmKit authorization**
  - Acceptance: all authorization states have explicit UI and diagnostics.
- [ ] **WP-003 — Schedule one-shot AlarmKit alarm**
  - Depends on: WP-001, WP-002
  - Acceptance: alert fires at the expected time on a locked physical device.
- [ ] **WP-004 — Schedule recurring AlarmKit alarm**
  - Acceptance: recurrence survives first alert and app restart.
- [ ] **WP-005 — Implement snooze/countdown prototype**
  - Acceptance: snoozed alarm re-alerts repeatedly without requiring app foreground execution.
- [ ] **WP-006 — Add stop and secondary App Intents**
  - Acceptance: actions execute with stable alarm identifier.
- [ ] **WP-007 — Route intent into a wake-session placeholder**
  - Acceptance: exact alarm/session opens idempotently from Lock Screen.
- [ ] **WP-008 — Document when system sound stops**
  - Acceptance: matrix covers stop, secondary action, app foreground, and failed route.
- [ ] **WP-009 — Reconcile local and AlarmKit state**
  - Acceptance: missing, orphaned, and duplicate alarms are detected after launch.
- [ ] **WP-010 — Run lifecycle matrix**
  - Acceptance: results recorded for foreground, background, terminated, Silent Mode, Focus, reboot, time zone, and DST.

### P1

- [ ] **WP-011 — Implement structured OSLog schema**
- [ ] **WP-012 — Add local diagnostic export**
- [ ] **WP-013 — Prototype Reliability Center**
- [ ] **WP-014 — Add automated state-machine test harness**
- [ ] **WP-015 — Test overlapping alarms**
- [ ] **WP-016 — Test authorization revocation and recovery**

## Next — Milestone 2: Domain foundation

### P0

- [ ] **WP-020 — Define Alarm domain model**
- [ ] **WP-021 — Define versioned WakeProtocol model**
- [ ] **WP-022 — Define WakeSession model**
- [ ] **WP-023 — Implement wake-session state machine**
- [ ] **WP-024 — Wrap AlarmKit behind `AlarmScheduling`**
- [ ] **WP-025 — Add injected clock and deterministic recurrence engine**
- [ ] **WP-026 — Add SwiftData repositories and migration tests**
- [ ] **WP-027 — Make test alarm use production code path**
- [ ] **WP-028 — Add idempotent App Intent handoff store**
- [ ] **WP-029 — Add safety-first error taxonomy**

### P1

- [ ] **WP-030 — Create enum-driven navigation shell**
- [ ] **WP-031 — Add settings and permission diagnostics**
- [ ] **WP-032 — Add local incident bundle format**
- [ ] **WP-033 — Define analytics events and privacy filter**
- [ ] **WP-034 — Add feature-flag service for experiments**

## Then — Milestone 3: Physical proof

### P0

- [ ] **WP-040 — Build guided target-registration flow**
- [ ] **WP-041 — Capture short multi-view registration burst**
- [ ] **WP-042 — Extract local visual representations**
- [ ] **WP-043 — Build live multi-frame attempt capture**
- [ ] **WP-044 — Add randomized liveness instruction**
- [ ] **WP-045 — Implement composite verification score**
- [ ] **WP-046 — Add honest-failure guidance**
- [ ] **WP-047 — Implement barcode registration and proof**
- [ ] **WP-048 — Implement emergency escape**
- [ ] **WP-049 — Guarantee fallback after camera failure**

### P1

- [ ] **WP-050 — Build adversarial image corpus**
- [ ] **WP-051 — Test screen, print, and substitute-object attacks**
- [ ] **WP-052 — Add low-light and flash guidance**
- [ ] **WP-053 — Add local threshold calibration**
- [ ] **WP-054 — Add accessibility alternatives**
- [ ] **WP-055 — Add privacy-safe verifier diagnostics**

## Then — Milestone 4: Stay-awake loop

- [ ] **WP-060 — Implement math mission**
- [ ] **WP-061 — Implement typing mission**
- [ ] **WP-062 — Add mission rotation**
- [ ] **WP-063 — Schedule delayed wake check**
- [ ] **WP-064 — Re-alert after missed check**
- [ ] **WP-065 — Implement commitment lock window**
- [ ] **WP-066 — Add protocol presets**
- [ ] **WP-067 — Add session outcome and streak**
- [ ] **WP-068 — Generate privacy-safe wake card**
- [ ] **WP-069 — Measure return-to-bed baseline and outcome**

## Monetization and alpha

- [ ] **WP-080 — Configure StoreKit products**
- [ ] **WP-081 — Implement three-verified-mornings activation**
- [ ] **WP-082 — Implement free/Pro entitlement policy**
- [ ] **WP-083 — Build annual-first paywall**
- [ ] **WP-084 — Restore purchases and offline cache**
- [ ] **WP-085 — Test expiry during every alarm state**
- [ ] **WP-086 — Recruit 20–30 adversarial alpha testers**
- [ ] **WP-087 — Create alpha test script**
- [ ] **WP-088 — Build incident intake workflow**
- [ ] **WP-089 — Review pricing after alpha data**

## Beta and launch

- [ ] **WP-100 — External TestFlight setup**
- [ ] **WP-101 — App Store privacy disclosures**
- [ ] **WP-102 — Privacy policy**
- [ ] **WP-103 — Terms of use**
- [ ] **WP-104 — Accessibility audit**
- [ ] **WP-105 — Localization-ready copy**
- [ ] **WP-106 — App Store screenshots and preview**
- [ ] **WP-107 — Creator seeding kit**
- [ ] **WP-108 — Referral link design**
- [ ] **WP-109 — Support runbook**
- [ ] **WP-110 — Production release checklist**

## Post-PMF discovery

- [ ] **WP-200 — Apple Watch companion feasibility**
- [ ] **WP-201 — Apple Health read-only trend prototype**
- [ ] **WP-202 — Smart-alarm extended-runtime spike**
- [ ] **WP-203 — Smart Wake Window evidence review**
- [ ] **WP-204 — Watch battery and reliability study**
- [ ] **WP-205 — Friend accountability prototype**
- [ ] **WP-206 — Creator protocol links**
- [ ] **WP-207 — Home automation research**
- [ ] **WP-208 — Android opportunity assessment**

## Repository setup

- [ ] Choose a license before publishing source code.
- [ ] Add `.gitignore` for Xcode and Swift.
- [ ] Add branch protection after the initial code scaffold.
- [ ] Add issue labels: `alarm-reliability`, `photo-proof`, `wake-check`, `safety`, `privacy`, `monetization`, `watch`, `research`.
- [ ] Add milestones matching roadmap gates.
- [ ] Add bug, feature, and research issue templates.
- [ ] Add pull-request template with test evidence.
- [ ] Add CI for build, unit tests, linting, and secret scanning.
