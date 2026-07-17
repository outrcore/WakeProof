# Release Checklist

A release cannot be approved by “the app builds.” WakeProof requires explicit alarm, safety, privacy, and entitlement evidence.

## Build and source

- [ ] Clean release build succeeds
- [ ] Unit and UI tests pass
- [ ] Static analysis/lint passes
- [ ] No secrets or private test assets in repository
- [ ] Dependencies reviewed
- [ ] Version and build numbers correct
- [ ] Migration tests pass from every supported production schema
- [ ] Release notes written

## Alarm lifecycle

- [ ] One-shot alarm passes
- [ ] Recurring alarm passes
- [ ] Snooze re-alert passes
- [ ] Delayed wake check passes
- [ ] App-terminated flow passes
- [ ] Locked-device flow passes
- [ ] Silent Mode flow passes
- [ ] Focus flow passes
- [ ] Reboot flow passes
- [ ] Time-zone flow passes
- [ ] DST tests pass or are documented for the release period
- [ ] Overlapping alarms pass
- [ ] Local/AlarmKit reconciliation passes
- [ ] Test alarm uses production path

## Safety

- [ ] Emergency escape reachable from every mission state
- [ ] Subscription expiry cannot trap user
- [ ] Camera permission failure has fallback
- [ ] Storage/persistence failure has safe behavior
- [ ] No infinite escalation loop
- [ ] Latest mandatory wake time cannot be moved later implicitly
- [ ] Accessibility alternative exists for required missions

## Photo and mission quality

- [ ] Honest-pass test target met
- [ ] False-reject rate reviewed
- [ ] Known-cheat corpus run
- [ ] Low-light behavior reviewed
- [ ] Median verification time acceptable
- [ ] Barcode fallback passes
- [ ] Cognitive missions support accessibility settings
- [ ] Mission copy has corrective guidance

## Privacy and security

- [ ] Network audit shows no raw photo upload
- [ ] Analytics log audit contains no sensitive values
- [ ] File protection verified
- [ ] Deletion controls tested
- [ ] Privacy policy matches behavior
- [ ] App Store privacy disclosures updated
- [ ] Health permissions requested only if feature is active
- [ ] No health or camera data used for advertising
- [ ] Share cards contain no sensitive data

## StoreKit

- [ ] Products load
- [ ] Purchase succeeds
- [ ] Cancel/failure paths work
- [ ] Restore works
- [ ] Offline entitlement behavior works
- [ ] Refund/revocation tested
- [ ] Activation-morning counting correct
- [ ] Downgrade does not delete alarms
- [ ] Paywall absent from active wake flows

## Accessibility

- [ ] VoiceOver pass
- [ ] Dynamic Type pass
- [ ] Switch Control critical-path pass
- [ ] Reduce Motion pass
- [ ] Contrast and color-independent state pass
- [ ] One-handed critical-path pass
- [ ] Haptic/visual alternatives reviewed

## Observability and support

- [ ] Production event schema verified
- [ ] Reliability dashboard updated for build
- [ ] Diagnostic bundle export works
- [ ] Known issues documented
- [ ] Support runbook updated
- [ ] Incident owner assigned
- [ ] Rollback/feature-flag plan exists

## App Store and launch

- [ ] Metadata is accurate
- [ ] Screenshots match current UI
- [ ] No “uncheatable,” diagnostic, or unsupported optimal-wake claim
- [ ] Terms and privacy links work
- [ ] Subscription disclosure is clear
- [ ] Review notes explain AlarmKit and mission behavior
- [ ] Test account/instructions supplied if needed
- [ ] Creator assets use privacy-safe examples

## Approval

| Role | Name | Date | Result |
|---|---|---|---|
| Engineering |  |  |  |
| Product |  |  |  |
| Reliability |  |  |  |
| Privacy |  |  |  |
| Release owner |  |  |  |
