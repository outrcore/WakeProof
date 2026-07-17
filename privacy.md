# Privacy

WakeProof interacts with alarms, private spaces, camera imagery, motion, and potentially health data. Privacy must be designed into the architecture rather than added before App Review.

## Data principles

- Collect the minimum necessary data.
- Process camera and health signals on device by default.
- Ask for permissions in context.
- Explain the direct user benefit.
- Do not require an account for core use.
- Do not use sensitive data for advertising, marketing profiles, or third-party data mining.
- Make deletion understandable and complete.
- Prefer derived, non-reversible representations over raw imagery.
- Keep analytics free of user-authored or sensor-derived sensitive content.

## Camera data

### Target registration

Default behavior:

1. Capture a short local burst.
2. Extract visual representations.
3. Store protected representations on device.
4. Delete raw frames after successful extraction.
5. Allow the user to delete or re-register the target.

Do not upload registration images by default.

### Alarm-time attempts

- Live camera only.
- Process frames transiently.
- Delete raw frames after scoring.
- Store only reason codes and coarse confidence bands in session history.
- Never include an attempt image in a wake card.
- Never include images in analytics.
- Debug capture requires a separate explicit opt-in and local retention limit.

### Barcode data

Store a protected hash or minimally necessary representation where feasible. Do not send product identifiers or QR contents to analytics.

## Apple Health and Watch data

When introduced:

- request only specific types needed for the active feature;
- request access when the user enables that feature, not at first launch;
- describe the benefit in plain language;
- treat unavailable data and denied read access as normal;
- keep health samples local unless the user explicitly chooses an export;
- never use health data for ad targeting or creator segmentation;
- never claim diagnosis or treatment;
- do not write inferred sleep stages without a separate evidence and policy review.

User-facing copy should say “Apple Health,” not “HealthKit,” except in developer documentation.

## Analytics

Allowed examples:

- alarm scheduling result;
- alert lifecycle reason code;
- mission type;
- pass/fail/escape;
- verification duration;
- coarse confidence band;
- app/OS/device class;
- paywall and transaction state;
- referral activation.

Prohibited examples:

- raw photos;
- embeddings;
- barcode value;
- custom target name;
- typed phrase;
- exact wake location;
- exact health values;
- sleep-stage timeline;
- contact or friend content;
- free-form incident text without redaction.

Use an explicit privacy filter before every analytics event leaves the process.

## Identifiers

- Use installation-scoped random identifiers.
- Hash alarm and session identifiers before analytics.
- Avoid IDFA.
- Do not create cross-app identity.
- Rotate identifiers when the user resets analytics data.
- Keep subscription transaction identifiers only where required for entitlement reconciliation.

## Accounts and cloud

MVP has no required account.

Future account features must separate:

- authentication identity;
- subscription entitlement;
- social/accountability data;
- health data;
- camera target data.

No cloud feature should silently opt in existing private data.

## Data retention

Initial proposal:

| Data | Default retention |
|---|---|
| Alarm configuration | Until user deletes |
| Target representation | Until target or app data deleted |
| Raw registration frames | Deleted immediately after extraction |
| Raw attempt frames | Deleted immediately after scoring |
| Wake-session summary | User-configurable; default 90 days |
| Local diagnostics | 14 days |
| Server analytics | Minimum necessary; define before launch |
| Support attachments | Case-specific and consented |

Retention must match the published privacy policy and implemented deletion behavior.

## User controls

Provide:

- delete target;
- delete wake history;
- reset analytics identifier;
- export non-sensitive history;
- manage Apple Health permissions through system settings;
- disconnect accountability relationships;
- delete account if accounts are introduced;
- clear local diagnostics.

## App Store and policy constraints

Apple’s current guidelines require special protection for health, fitness, medical, camera, and motion data and prohibit using such data for advertising or marketing data mining.

Primary references:

- https://developer.apple.com/app-store/review/guidelines/
- https://developer.apple.com/documentation/healthkit
- https://developer.apple.com/design/human-interface-guidelines/healthkit
- https://developer.apple.com/health-fitness/

## Security review checklist

- File protection configured
- Keychain used for secrets
- Sensitive logs redacted
- No third-party SDK receives camera or health data
- Network inspector confirms no accidental uploads
- Export files require explicit user action
- Share cards contain no sensitive imagery
- Deletion tests pass
- Backup/iCloud behavior documented
- Threat model reviewed after every new sensor or cloud feature
