# Risk Register

Scoring:

- Probability: 1 low → 5 high
- Impact: 1 low → 5 existential
- Exposure = probability × impact

## Active risks

| ID | Risk | P | I | Exposure | Mitigation | Trigger |
|---|---|---:|---:|---:|---|---|
| RSK-001 | AlarmKit handoff cannot preserve the required user experience | 3 | 5 | 15 | Physical-device feasibility gate before product build | Sound stops or route fails under common state |
| RSK-002 | Snooze or recurrence is unreliable | 2 | 5 | 10 | Soak tests, reconciliation, visible diagnostics | Any unexplained missed re-alert |
| RSK-003 | Photo verifier is too easy to cheat | 4 | 4 | 16 | Multi-frame, liveness, adversarial corpus, adaptive thresholds | High screen/substitute acceptance |
| RSK-004 | Photo verifier rejects honest users | 4 | 5 | 20 | Guided capture, reason codes, fallback, per-user calibration | High repeat-attempt or escape rate |
| RSK-005 | User becomes trapped in alarm | 2 | 5 | 10 | Emergency escape invariant and accessibility testing | Any unreachable stop path |
| RSK-006 | Market sees product as Alarmy clone | 4 | 4 | 16 | Proof-of-wake positioning, stay-awake loop, reliability brand | Creative and review language centers on generic puzzles |
| RSK-007 | Subscription backlash | 3 | 4 | 12 | Functional free tier, no weekly plan, prove value first | Refunds, one-star reviews, low renewal |
| RSK-008 | Organic growth fails and paid CPI exceeds value | 4 | 4 | 16 | Productized sharing, creator seeding, unit-economics gate | CAC above contribution value |
| RSK-009 | Health or “optimal wake” claims create policy risk | 3 | 5 | 15 | Defer Smart Wake, conservative language, evidence review | App Review concern or unsupported copy |
| RSK-010 | Sensitive photo or health data leaks | 2 | 5 | 10 | Local processing, privacy filter, no raw analytics | Network/log audit finds sensitive value |
| RSK-011 | Watch feature consumes roadmap before PMF | 4 | 3 | 12 | Explicit entry criteria in smart-wake.md | Watch work starts before core SLO/retention |
| RSK-012 | Scope expands into generic sleep platform | 4 | 4 | 16 | MVP non-goals and gate-based roadmap | Sleep tracker work displaces alarm reliability |
| RSK-013 | Accessibility alternatives weaken proof or exclude users | 3 | 5 | 15 | Accessible protocol design from MVP | User cannot complete or must disable app |
| RSK-014 | Competitor copies visible features | 5 | 3 | 15 | Moat in calibration, data, trust, distribution | Large incumbent launches equivalent flow |
| RSK-015 | Public repo exposes proprietary anti-cheat details | 3 | 3 | 9 | Keep high-level docs public; review code/license and threat details | Attack playbook becomes trivial |
| RSK-016 | Support burden is unusually high | 4 | 4 | 16 | Reliability Center, diagnostic bundles, narrow device scope | Contacts per 1,000 alarms exceed target |
| RSK-017 | Low ratings from a small number of alarm incidents | 4 | 5 | 20 | Staged beta, incident response, no premature launch | Reliability-related review spike |
| RSK-018 | User behavior makes outcome impossible to verify | 3 | 3 | 9 | Honest positioning and outcome surveys | “Verified” users still return to bed frequently |
| RSK-019 | App is associated with shame or harmful punishment | 3 | 4 | 12 | Supportive copy, safety controls, no coercive defaults | User/press feedback flags harm |
| RSK-020 | Financial commitment creates legal/payment complexity | 3 | 4 | 12 | Defer; legal and App Review review | Feature enters active roadmap |

## Highest-priority risk retirements

1. RSK-001 — AlarmKit handoff
2. RSK-004 — Honest photo rejection
3. RSK-003 — Photo cheating
4. RSK-017 — Rating damage from incidents
5. RSK-006 — Clone positioning
6. RSK-008 — Acquisition economics

## Risk review cadence

- At every milestone gate
- Before TestFlight expansion
- Before each App Store release
- After every S0/S1 incident
- Before adding a new sensor, permission, backend, or monetization mechanism
- Quarterly competitor and policy review

## Risk acceptance rule

A risk can be accepted only when:

- the user impact is understood;
- a named owner exists;
- a detection mechanism exists;
- the fallback is documented;
- the release decision records why the exposure is acceptable.

“Competitors do it” is not an acceptable risk rationale.
