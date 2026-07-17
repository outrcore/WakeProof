# Features

## Classification rules

- **MVP:** Required to prove WakeProof’s differentiated core promise.
- **Soon after launch:** Strengthens retention or distribution without destabilizing the core.
- **Experimental:** Requires evidence, opt-in framing, and deterministic fallback.
- **Deferred:** Valuable but distracts from the initial wedge.
- **Not planned:** Conflicts with trust, safety, privacy, or positioning.

## MVP feature matrix

| Area | Feature | Why it exists | Acceptance summary |
|---|---|---|---|
| Alarm | One-shot and recurring alarms | Basic product requirement | Persisted locally and represented in AlarmKit |
| Alarm | Real snooze | Directly fixes the reported competitor failure | Always creates a visible post-alert countdown and re-alert |
| Alarm | Test alarm | Builds trust before bedtime | Uses the production scheduling and routing path |
| Alarm | Reliability Center | Makes failures diagnosable | Shows authorization, next alarm, sync status, and test result |
| Protocol | Three-stage wake protocol | Product differentiation | Physical proof → optional cognitive task → delayed check |
| Photo | Guided target registration | Improves honest matching | Multi-view capture with quality feedback |
| Photo | Live multi-frame proof | Raises cost of spoofing | Camera only; no library, pasteboard, or screenshot input |
| Photo | Basic liveness | Rejects common screen/replay attempts | Uses motion, optical flow, and randomized instruction |
| Barcode | Barcode/QR proof | Deterministic physical alternative | Exact registered payload required |
| Cognitive | Math | Familiar cognitive task | Difficulty and quantity configurable within safe limits |
| Cognitive | Typing | Activates attention without domain knowledge | Rotating phrases; tolerant of accessibility settings |
| Stay awake | Delayed wake check | Prevents immediate return to bed | Missed check enters escalation/re-alert |
| Commitment | Lock window | Stops bedtime self-sabotage | Critical alarm settings become protected before wake time |
| Safety | Emergency escape | Prevents trapping the user | Always available, bounded, deliberate, and recorded |
| Privacy | Local-first verification | Protects private room imagery | No raw image upload by default |
| Monetization | Free + Pro entitlements | Supports adoption and revenue | Reliability remains free |
| Sharing | Privacy-safe wake card | Supports UGC and referrals | Never contains captured photo or health data |
| Accessibility | Alternative mission path | Avoids physical exclusion | Every required action has an accessible fallback |

## Mission design

### Physical proof missions

#### Photo target

Register a fixed target such as:

- bathroom sink;
- coffee maker;
- refrigerator;
- front door;
- office desk;
- medication station.

Photo verification is a confidence score, not a binary promise of impossibility. The UI must say “Strict Proof” or “live photo proof,” not “uncheatable.”

#### Barcode or QR

Best for users who want deterministic matching. The target should be placed far enough from bed to require movement. The app should warn when the registered code is detected as physically too convenient only if such a claim can be made from user configuration—not through hidden surveillance.

#### Movement gate

A future or optional supporting signal, not sufficient proof by itself. Step counts and device motion can be gamed and can exclude users with mobility limitations.

### Cognitive missions

Cognitive missions supplement physical proof. They are not treated as sufficient evidence of wakefulness because users may learn to complete them while barely awake.

Candidate rotations:

- arithmetic;
- phrase typing;
- sentence reconstruction;
- short memory pattern;
- odd-one-out;
- grammar correction;
- contextual question drawn from a user-approved local set.

Grammar is a useful content variant, not a product wedge.

### Stay-awake missions

- tap a delayed check;
- repeat a shortened physical proof;
- complete a different cognitive task;
- scan a second location;
- confirm activity through a configured accessible alternative.

## Default protocol presets

| Preset | Physical proof | Cognitive proof | Delayed check | Commitment |
|---|---|---|---|---|
| Maddie Mode | Strict photo | Rotating short task | 5 minutes | 60-minute lock |
| Early Shift | Barcode | Optional math | 3 minutes | 90-minute lock |
| Exam Morning | Photo | Typing + memory | 7 minutes | 8-hour lock |
| Gym Morning | Photo at gear/coffee | None | 5 minutes | 30-minute lock |
| Travel Critical | Barcode or photo | Typing | 3 and 8 minutes | 12-hour lock |
| Accessible Focus | User-selected non-physical proof | Typing or memory | Configurable | Configurable |

Presets are editable templates, not medical or behavioral prescriptions.

## Soon after launch

- Multiple photo targets per alarm
- Adaptive challenge rotation
- Friend accountability notification
- Creator protocol links
- Referral rewards
- Home-screen widgets
- Lock Screen and Dynamic Island refinements
- Shortcuts/App Intents for creating and testing alarms
- Apple Watch companion for haptic reinforcement
- Optional Apple Health read-only trend insights
- Travel profile and automatic time-zone review
- Additional languages
- More accessible input modes

## Experimental

- Smart Wake Window using Apple Watch
- On-device personalized photo thresholds
- Confidence-based fallback selection
- Wake protocol recommendations
- Return-to-bed risk prediction
- Friend-selected mission
- User-funded commitment stakes
- Home automation actions after verified wake
- Light-based wake support

Every experiment must preserve a hard latest-wake fallback.

## Deferred

- Full sleep tracker
- Snore and audio recording
- Sleep score
- Sleep coaching
- AI voice packs
- Social feed
- Large sound-content library
- Android
- Family administration dashboard
- Clinical or workplace deployment

## Not planned

- Ads during alarms or missions
- Payment required to silence an alarm
- Health-data-based advertising
- Uploading private photos by default
- Claims of diagnosing sleep disorders
- Claims that the app is impossible to cheat
- Hidden disabling of the emergency escape
- Unlimited punishment loops
- Features that can move the latest wake time later without explicit consent
