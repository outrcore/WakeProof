# Metrics

## North-star metric

**Verified wake-ups per weekly active user**

A verified wake-up ends only after the required protocol and delayed wake check succeed or after a documented safe fallback completes. Merely dismissing an alarm is not a successful outcome.

## Metric hierarchy

### Trust and reliability

- expected alerts;
- actual system alerts;
- missed-alert incidents per 10,000 eligible alarms;
- snooze re-alert success;
- recurrence success;
- correct-session routing;
- crash-free wake sessions;
- reconciliation discrepancies;
- emergency-escape reachability;
- support contacts per 1,000 alarms.

### Activation

- AlarmKit authorization completion;
- test-alarm completion;
- first alarm created;
- first target registered;
- first real alarm scheduled;
- first verified wake-up;
- time from install to first verified wake-up.

### Verification quality

- honest-pass rate;
- false-reject rate;
- known-cheat rejection rate;
- attempts per successful proof;
- median proof duration;
- camera-system failure rate;
- barcode fallback rate;
- emergency-escape rate;
- reason-code distribution.

### Wake effectiveness

- physical proof completion;
- cognitive mission completion;
- delayed-check pass;
- missed-check escalation;
- user-reported return to bed;
- self-reported morning alertness;
- snoozes per alarm;
- time from first alert to terminal completion.

### Retention

- D1, D7, D30 verified-wake retention;
- weekly verified wake-ups;
- retained alarms per user;
- streak continuation;
- protocol-edit frequency;
- free and paid cohort retention;
- retention segmented by heavy-snoozer self-identification.

### Monetization

- activation-period completion;
- paywall view;
- purchase start and completion;
- download-to-paid conversion;
- annual-plan selection;
- revenue per install;
- refund rate;
- renewal;
- downgrade;
- cancellation reason;
- paid retention.

### Growth

- wake-card creation;
- share completion;
- referral link sent;
- referred install;
- referred first verified wake-up;
- creator protocol import;
- organic App Store conversion;
- creative-level paid acquisition metrics.

## Guardrail metrics

A growth or revenue experiment fails if it materially worsens:

- missed-alert rate;
- escape reachability;
- false-reject rate;
- support complaints;
- refund rate;
- App Store rating;
- accessibility completion;
- privacy incidents;
- latest-wake compliance.

## Event taxonomy

### Alarm

- `alarm_created`
- `alarm_updated`
- `alarm_enabled`
- `alarm_disabled`
- `alarm_schedule_requested`
- `alarm_schedule_succeeded`
- `alarm_schedule_failed`
- `alarm_reconciled`
- `alarm_alert_observed`
- `alarm_snoozed`
- `alarm_realert_observed`
- `alarm_stopped`

### Wake session

- `wake_session_created`
- `wake_session_routed`
- `wake_session_route_failed`
- `mission_started`
- `mission_attempt_rejected`
- `mission_passed`
- `emergency_escape_started`
- `emergency_escape_completed`
- `wake_check_scheduled`
- `wake_check_passed`
- `wake_check_missed`
- `wake_session_completed`

### Monetization

- `activation_morning_completed`
- `paywall_viewed`
- `purchase_started`
- `purchase_completed`
- `purchase_failed`
- `entitlement_changed`
- `subscription_restored`

### Reliability

- `reconciliation_discrepancy`
- `authorization_changed`
- `diagnostic_test_started`
- `diagnostic_test_passed`
- `diagnostic_test_failed`
- `incident_report_started`
- `incident_report_submitted`

## Event privacy

Every event is passed through the privacy rules in [privacy.md](privacy.md). No event may contain images, health samples, barcode values, typed content, exact locations, or free-form target names.

## Decision dashboards

### Daily reliability

- eligible alarms;
- alert success;
- snooze success;
- route success;
- delayed-check escalation;
- incidents by app/OS/device version.

### Weekly product

- first verified wake-up;
- verified wake retention;
- protocol completion funnel;
- proof rejection reasons;
- escape rate;
- share/referral funnel.

### Monthly business

- paid conversion;
- annual mix;
- revenue per install;
- renewal and refunds;
- acquisition channel;
- support cost;
- cohort contribution estimate.

## Smart Wake experiment metrics

When introduced:

- fixed-time vs Smart Wake alertness;
- latest-time compliance;
- Watch session start success;
- signal availability;
- algorithm confidence;
- haptic alert success;
- Watch battery impact;
- support incidents;
- retained use after four weeks.

Never declare Smart Wake successful based only on sleep-stage prediction accuracy.
