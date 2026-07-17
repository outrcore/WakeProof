# Subscription

All prices and packaging are launch hypotheses and must be validated. They are not promises to users or permanent commitments.

## Monetization principles

1. Reliability and safety are never premium.
2. The user must experience a successful real wake-up before a strong paywall.
3. No paywall, ad, upsell, rating prompt, or cancellation flow appears during an active wake session.
4. The annual plan should be the default value proposition.
5. Weekly subscriptions are excluded at launch.
6. Health data, camera data, or mission content must never be used for advertising.
7. A user with an expired subscription can always manage and stop existing alarms safely.
8. Subscription-state failures must degrade toward safety, not toward a trapped alarm.

## Recommended launch products

| Product | Candidate price | Role |
|---|---:|---|
| Monthly | $8.99 | Flexible option and price anchor |
| Annual | $39.99 | Default and primary plan |
| Founders lifetime | $69.99 | Limited early cohort only |

Revisit $49.99 annual pricing only after strong retention and low refund rates are demonstrated.

## Activation period

Give a new user full product access for the first **three verified mornings**.

Why this is preferable to an arbitrary three-day timer:

- value is measured in actual mornings;
- installing on a weekend does not waste the trial;
- the paywall can follow a demonstrated success;
- it creates a natural product story: “WakeProof worked three times.”

The entitlement logic must define edge cases:

- What counts as a verified morning?
- Does a test alarm count? **No.**
- Does emergency escape count? **No.**
- Does a missed delayed check count? **No.**
- Does a protocol without physical proof count? Product decision required.
- How are time-zone changes handled?
- Can reinstalling reset the activation period? Prefer durable App Store transaction/app-account token strategies without requiring an account.

## Free tier

- One active alarm
- One registered target
- Standard photo or barcode proof
- Basic math or typing task
- One delayed wake check
- Test alarm
- Reliability Center
- Emergency escape
- Full AlarmKit reliability
- Alarm management after subscription expiry

## WakeProof Pro

- Unlimited active alarms
- Strict Proof photo verification
- Multi-stage protocols
- Multiple targets
- Rotating and adaptive missions
- Multiple delayed wake checks
- Commitment lock windows
- Advanced fallback configuration
- Travel profiles
- Wake analytics and trends
- Creator protocol packs
- Friend accountability
- Apple Watch companion features
- Smart Wake Window when released
- Advanced share-card customization

## Paywall placement

### Recommended

- After the third successful verified wake-up
- From a Pro feature preview
- From Settings or subscription management
- After viewing a meaningful trend or protocol recommendation

### Prohibited

- While the alarm is ringing
- While a camera or barcode mission is active
- Before emergency escape
- Immediately after a failed proof attempt
- During snooze countdown
- During a missed wake-check escalation
- In a way that obscures how to stop an alarm

## Initial experiments

| Test | Variant A | Variant B | Primary metric | Guardrail |
|---|---|---|---|---|
| Trial model | Three verified mornings | Seven-day StoreKit trial | Paid conversion | Refund and complaint rate |
| Annual price | $39.99 | $49.99 | Net revenue per install | Conversion and refund rate |
| Paywall timing | After third success | After first real success | Paid conversion | D7 retention |
| Free alarm limit | One | Two | Paid conversion | Organic retention and ratings |
| Lifetime | Limited $69.99 | No lifetime | Cash generation | Cannibalization |
| Annual framing | “Best value” | “Cost per morning” | Annual selection | Trust and clarity |

Do not run many experiments simultaneously in a small cohort. Every experiment needs a predeclared decision rule.

## Key metrics

- paywall view rate;
- trial or activation completion;
- download-to-paid conversion;
- annual-plan selection;
- revenue per install;
- refund rate;
- subscription cancellation reason;
- renewal rate;
- paid D30 and D90 retention;
- free-to-paid conversion after a successful wake;
- support contacts per payer;
- app-rating difference between free and paid users.

## Unit-economics rule

Paid acquisition should not scale until expected contribution value per install exceeds fully loaded acquisition cost with a meaningful margin. Organic UGC and referral distribution are therefore core business capabilities, not optional marketing decoration.

## Subscription failure behavior

When StoreKit state is unavailable:

- continue already-scheduled safety-critical behavior;
- do not unexpectedly disable an alarm;
- do not unlock paid editing indefinitely unless the entitlement cache permits it;
- surface a non-blocking account-status message after the wake session;
- retry entitlement reconciliation later;
- record the event without collecting sensitive mission content.

## Cancellation and downgrade

A downgrade must never silently delete alarms. Instead:

1. show which alarms exceed the free-tier limit;
2. let the user select the one alarm that remains active;
3. keep all alarms visible but safely disabled until resolved;
4. warn before the next affected wake time;
5. never require resubscription to silence or delete an alarm.
