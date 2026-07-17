# WakeProof

**WakeProof is a proof-of-wakefulness alarm for people who can outsmart ordinary alarms.**

> The alarm rings, gets the user out of bed, verifies that they completed a real-world wake protocol, and checks that they stayed awake.

WakeProof is intentionally not another generic alarm with a long list of puzzles. Its wedge is a reliable, anti-cheat wake sequence built around three outcomes:

1. **Get out of bed.**
2. **Turn the brain on.**
3. **Stay awake.**

## Current product decision

Build the smallest reliable iOS product first:

- iOS 26+ and AlarmKit
- photo and barcode proof
- math and typing challenges
- real snooze that re-alerts
- a delayed wake check
- commitment lock windows
- an emergency escape
- local-first data and verification

Apple Watch, Apple Health, sleep analytics, and a probabilistic “smart wake window” are intentionally deferred until the core alarm has demonstrated reliability and product-market fit. See [smart-wake.md](smart-wake.md).

## Documentation index

| Document | Purpose |
|---|---|
| [product.md](product.md) | Product thesis, users, jobs, positioning, and non-goals |
| [roadmap.md](roadmap.md) | Milestones, gates, sequencing, and exit criteria |
| [features.md](features.md) | Feature inventory and MVP/later/not-planned classification |
| [subscription.md](subscription.md) | Packaging, pricing hypotheses, paywalls, and experiments |
| [framework.md](framework.md) | Engineering architecture, platform stack, state machine, and conventions |
| [tasks.md](tasks.md) | Executable backlog with priorities, dependencies, and acceptance criteria |
| [bugs.md](bugs.md) | Bug policy, severity model, incident handling, and initial risk watchlist |
| [decisions.md](decisions.md) | Product and engineering decision log |
| [competitors.md](competitors.md) | Competitor snapshot and strategic implications |
| [smart-wake.md](smart-wake.md) | Apple Watch/Apple Health “optimal wake” strategy |
| [reliability.md](reliability.md) | Reliability SLOs, telemetry, reconciliation, and failure policy |
| [testing.md](testing.md) | Device, lifecycle, camera, accessibility, and adversarial test plans |
| [privacy.md](privacy.md) | Camera, health-data, analytics, retention, and consent rules |
| [metrics.md](metrics.md) | North-star metric, event taxonomy, product metrics, and guardrails |
| [launch.md](launch.md) | Beta, App Store, UGC, referral, and launch-gate strategy |
| [research.md](research.md) | Evidence, source register, open questions, and experiment queue |
| [risk-register.md](risk-register.md) | Product, technical, commercial, legal, and operational risks |
| [design-principles.md](design-principles.md) | UX rules for a high-stakes, half-awake user |
| [release-checklist.md](release-checklist.md) | Required checks before beta and production releases |

## Working rules

- Reliability is a feature, not infrastructure hidden beneath the product.
- No paywall, ad, rating prompt, or upsell may interrupt an active alarm, mission, snooze, fallback, or emergency escape.
- Every scheduled alarm has a persisted local record and a corresponding system-alarm record.
- The app never claims that photo verification is impossible to cheat.
- Health or sleep-stage claims require evidence, transparent methodology, and conservative language.
- A missed alarm is handled as a production incident.
- Features do not enter the build simply because a competitor has them; they must strengthen WakeProof’s core promise.

## North-star metric

**Verified wake-ups per weekly active user**

The product succeeds when users reliably complete wake protocols and remain awake—not when they merely open the app, solve a puzzle, or dismiss an alert.

## Status

Product documentation baseline established July 2026. The next gate is the physical-device AlarmKit lifecycle spike defined in [roadmap.md](roadmap.md).
