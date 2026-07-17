# Design Principles

WakeProof is used under unusual conditions: low light, impaired attention, urgency, irritation, and often one-handed interaction. Standard polished-app assumptions are insufficient.

## 1. Design for 5:30 a.m.

- One primary action per screen.
- Large hit targets.
- Minimal reading.
- No hidden gestures for critical actions.
- No fragile multi-step navigation.
- High contrast without blinding the user.
- Copy names the next required action.

## 2. Make state obvious

The user should always know:

- whether the alarm is still active;
- what step they are on;
- why an attempt failed;
- whether a delayed check is coming;
- when snooze will re-alert;
- how to reach emergency escape;
- whether tomorrow’s alarm is protected.

## 3. Trust is calmer than punishment

The brand can be energetic and entertaining, but the product should not humiliate users.

Prefer:

- “Let’s verify the target.”
- “The room is too dark—turn on flash.”
- “Wake check missed. We’re ringing again.”

Avoid:

- “You failed.”
- “Lazy mode.”
- shame, insults, or manipulative guilt as defaults.

## 4. Strict but recoverable

Every challenge can fail honestly. The interface should:

1. explain the likely problem;
2. offer an immediate corrective action;
3. preserve the alarm state;
4. offer an accessible alternative;
5. expose emergency escape without making it the easiest first action.

## 5. No dark patterns in distress

Never show:

- paywall;
- ad;
- rating prompt;
- referral prompt;
- notification upsell;
- health-permission request;
- account creation;
- long legal text

during an active alarm or recovery path.

## 6. Privacy must be visible

- Explain that target photos are processed locally.
- Show exactly what a wake card contains before sharing.
- Never use a bedroom or bathroom thumbnail in history by default.
- Use neutral target icons or user-selected labels.
- Keep health insights visually separate from alarm reliability.

## 7. Recommend, then customize

Start with a clear preset such as Maddie Mode. Do not make a half-awake user configure twenty sliders before the first test alarm.

Progressive disclosure:

1. choose target;
2. choose wake time;
3. run test;
4. use recommended protocol;
5. customize advanced strictness later.

## 8. Latest time dominates

In every scheduling UI, distinguish:

- earliest acceptable wake time;
- latest mandatory wake time;
- snooze duration;
- delayed-check time.

No feature may silently shift the latest mandatory time later.

## 9. Accessibility is a protocol property

Accessibility is not a settings toggle added after missions are built. Each protocol must know its alternative completion path.

Examples:

- physical movement alternative;
- camera framing assistance;
- VoiceOver-readable instructions;
- typing alternative;
- haptic and visual alert combination;
- extra time without reducing latest-wake guarantee.

## 10. Success should feel shareable

The completion screen can show:

- wake time;
- protocol;
- snoozes resisted;
- rejected shortcut count;
- streak;
- follow-up check passed.

It must not show:

- captured image;
- exact target location;
- health values;
- private room label;
- partner/friend identity without consent.

## Core screen set

- Onboarding
- Alarm list
- Alarm editor
- Protocol editor
- Target registration
- Test alarm
- Active alert handoff
- Physical mission
- Cognitive mission
- Delayed-check countdown
- Wake check
- Emergency escape
- Completion
- Reliability Center
- Subscription
- Settings/privacy

## Visual direction

Candidate direction:

- dark, calm pre-sleep surfaces;
- bright, decisive active-wake surfaces;
- bold typography;
- minimal ornament during alarms;
- distinctive proof/check visual language;
- motion used for state transition, not decoration;
- system-consistent controls where reliability matters.

Brand exploration should happen after the AlarmKit gate, not before.
