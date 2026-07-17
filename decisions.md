# Decisions

This is a lightweight Architecture and Product Decision Record. Decisions remain in this file until the volume justifies separate ADR files.

## Status meanings

- **Accepted:** Current default.
- **Provisional:** Chosen for now; requires validation.
- **Deferred:** Intentionally postponed.
- **Rejected:** Considered and not selected.
- **Superseded:** Replaced by a later decision.

---

## D-001 — Position as proof of wakefulness

- **Status:** Accepted
- **Decision:** WakeProof will not compete primarily on the number of puzzle types. It will compete on credible physical proof, reliable re-alert, and stay-awake verification.
- **Rationale:** Mission bundling is already common. The strongest unmet need is end-to-end wake reliability.
- **Revisit trigger:** Evidence that users choose breadth over wake effectiveness despite equal reliability.

## D-002 — Use a three-stage wake protocol

- **Status:** Accepted
- **Decision:** Product model is physical proof → optional cognitive task → delayed wake check.
- **Rationale:** One action can be completed on autopilot and does not prove the user remained awake.
- **Revisit trigger:** Beta data shows a simpler protocol achieves equivalent outcomes.

## D-003 — Target iOS 26+ for MVP

- **Status:** Provisional
- **Decision:** Build around AlarmKit rather than attempting a broad legacy-notification implementation.
- **Rationale:** System-level alarm delivery and lifecycle are central to trust.
- **Revisit trigger:** Addressable-market loss outweighs reliability gains, or AlarmKit cannot satisfy core handoff behavior.

## D-004 — AlarmKit lifecycle is the first engineering gate

- **Status:** Accepted
- **Decision:** No polished product build proceeds until physical-device scheduling, snooze, recurrence, routing, and reconciliation are understood.
- **Rationale:** A failed alarm invalidates all other product work.
- **Revisit trigger:** None; only supersede with an equivalent reliability gate.

## D-005 — Local-first and accountless by default

- **Status:** Accepted
- **Decision:** Core alarms, protocols, photo representations, and session summaries live on device. No account is required for MVP.
- **Rationale:** Faster onboarding, stronger privacy, reduced backend risk, and more credible handling of private spaces.
- **Revisit trigger:** Accountability, cross-device sync, or recovery has validated demand that cannot be met locally.

## D-006 — Multi-frame registration and proof

- **Status:** Accepted
- **Decision:** Photo targets are registered and verified through short guided captures, not one static image.
- **Rationale:** Provides viewpoint, motion, and liveness evidence and improves robustness.
- **Revisit trigger:** A simpler approach meets honest-pass and cheat-rejection targets.

## D-007 — Always provide emergency escape

- **Status:** Accepted
- **Decision:** Every active alarm has a bounded, deliberate fallback path.
- **Rationale:** Travel, injury, moved objects, permissions, camera failure, and environmental changes make absolute lock-in unsafe.
- **Revisit trigger:** Never remove; mechanics may change.

## D-008 — Reliability is not premium

- **Status:** Accepted
- **Decision:** System alarm delivery, snooze, test alarm, Reliability Center, and emergency escape remain available without Pro.
- **Rationale:** Safety and trust cannot be used as coercive upsells.
- **Revisit trigger:** Never remove; packaging details may change.

## D-009 — Three verified mornings before strong paywall

- **Status:** Provisional
- **Decision:** New users receive full access through three successful real mornings.
- **Rationale:** Aligns trial with experienced value.
- **Revisit trigger:** Conversion, abuse, or retention data supports a better model.

## D-010 — Initial pricing hypothesis

- **Status:** Provisional
- **Decision:** $8.99 monthly, $39.99 annual, limited $69.99 founders lifetime; no weekly plan.
- **Rationale:** Annual-first packaging fits a recurring habit product while maintaining an approachable entry price.
- **Revisit trigger:** Cohort conversion, renewal, refund, and unit-economics data.

## D-011 — Defer Smart Wake Window

- **Status:** Accepted
- **Decision:** Apple Watch/Apple Health “optimal wake” does not enter MVP.
- **Rationale:** It adds watchOS runtime, sensor, battery, permission, evidence, and support complexity before core reliability is proven. It also risks confusing the deterministic latest-wake promise.
- **Revisit trigger:** Core SLOs hold, retention is established, Watch ownership is material among users, and a physical-device spike proves a hard latest-wake fallback.

## D-012 — Apple Health is read-only first

- **Status:** Accepted
- **Decision:** When introduced, begin with post-wake insights using user-authorized data. Do not write sleep-stage data or make diagnostic claims.
- **Rationale:** Lower privacy, accuracy, and App Review risk.
- **Revisit trigger:** A specific user benefit requires writing data and passes privacy review.

## D-013 — No ads during high-stakes flows

- **Status:** Accepted
- **Decision:** No advertising during alarms, snooze, missions, wake checks, emergency escape, or reliability recovery.
- **Rationale:** Ads conflict with safety, trust, and health-data restrictions.
- **Revisit trigger:** None.

## D-014 — Smart Wake remains probabilistic

- **Status:** Accepted
- **Decision:** Future marketing will use “wake window” or “lighter-sleep estimate,” not guaranteed “optimal time.”
- **Rationale:** Wrist wearables infer stages imperfectly and the evidence on stage-specific sleep inertia is mixed.
- **Revisit trigger:** Strong independent clinical evidence and validated product accuracy.

## D-015 — Health and camera data never drive ads

- **Status:** Accepted
- **Decision:** No health, motion, camera, or photo-derived data may be used for advertising, marketing profiles, or third-party data mining.
- **Rationale:** User trust and Apple policy.
- **Revisit trigger:** None.
