# Changelog

## 1.0.0 — First stable public release

- Promoted the accepted free, non-commercial Tension Clock release candidate to 1.0.0. Countdown mechanics, persistence schema, permissions, player visibility, Roll Router, Story Beats, HUD controls, sound selection, and DPCGL/license terms are unchanged.

## 0.9.0 — Release candidate for owner testing

### Final licensing, attribution, branding, and sound-layout amendment

- Corrected the release model to free, non-commercial Foundry distribution and the original code license to free proprietary terms: all of a user's own worlds, streamed/recorded actual plays where permitted, private modifications, backups, and player access without separate licenses. The legal copyright holder name remains to be inserted before public release.
- Reviewed official DPCGL 2.0 and SRD 2.0; moved Daggerheart™ Compatible to descriptive text, changed the public title to **Tension Clock**, and added separate third-party notices. The technical module ID and saved settings are unchanged.
- Aligned all four Sound Browse controls and paths as grouped fields, retaining Foundry’s native audio FilePicker, blank defaults, local mute/volume, and the prior removal of bundled audio.
- Browse now uses Foundry's host-selected audio FilePicker implementation, opens near the field's existing sound or the most recently selected audio, and rejects non-audio selections using Foundry's supported audio extensions. The Sound dialog layout and sound playback remain unchanged.
- Recorded the owner’s manual GM Only test with separate GM and Player clients as PASS. This is owner-reported rather than reproduced by this build environment.
- **Free Foundry VTT distribution gate resolved:** DPCGL 2.0 section 1.9.1 permits non-commercial sharing on whitelisted Foundry VTT; section 4.1 attribution is provided in third-party notices. No commercial-cover logo is required for this free distribution. No mechanics, settings, or code changed in the correction.


### User-Selected Sound Amendment

- Removed four bundled WAV cues and their hard-coded playback paths. Fresh installs have no configured sounds.
- Added four GM world sound paths in the Director’s **Sounds** dialog, with Foundry’s native audio file picker. Existing local Sounds, Volume, and Reduced Motion controls are preserved.
- Missing audio fails without affecting Countdown state; old paths to the removed bundled files are ignored and cleared when sound settings are saved. No Countdown data migration.

### GM Player HUD Presentation Control

- Added **Show to Players** to the GM Director. A small module socket request opens each player's existing HUD, restores it if minimized, and recovers an off-screen position. Repeated requests reuse an open HUD; Countdown visibility and saved data are unchanged.
- The action handler checks GM permission and records a short authorization marker through Foundry's permission-checked world setting before broadcasting. Receiving clients validate the marker rather than trusting a sender ID supplied in a socket payload. Live multiplayer behavior still requires owner verification.

- Reviewed the v14 manifest, kept the permanent module ID, set version 0.9.0, and clarified the public product description without adding unassigned release URLs.
- Removed the manifest's descriptive `license` text because it was not a selected software license. The later amendment above supplies a proprietary license; bundled sound redistribution is resolved.
- Replaced development chronology in the front-facing README with installation, first-use, controls, visibility, and release limits; added a specific owner acceptance checklist and RC test report.
- Verified that existing `schemaVersion: 1` data needs no conversion. Added a serialized v0.8-shaped upgrade fixture and preserved all existing Countdown behavior and presentation code.
- Excluded development tests and the earlier stabilization report from the runtime ZIP; retained source, styles, README, changelog, and RC documentation.
- **Status:** v0.9 RC; free distribution under the applicable DPCGL provision is cleared by this review. See `RC-TEST-REPORT.md` for the copyright-name insertion and remaining live checks before public release. No 1.0 promotion was made.

## 0.8.0 — Stabilization and stress testing

- Preserve malformed saved Countdown records and display a GM repair warning, while keeping unaffected clocks usable. Reject an invalid world-setting root without silently replacing it with empty data.
- Reject blank Set Value input instead of treating it as zero. Show “Missing Scene” when a saved Scene association no longer resolves.
- Keep the currently routed roll in place during rapid rolls; limit the waiting queue to 32, warn once at capacity, and leave excess rolls in chat.
- Drop stale queued Beat and completion presentations when later state changes or an archive makes them irrelevant. Avoid duplicate presentation processing for a repeated same-revision setting notification.
- Guard scene and roll hooks against malformed saved state with diagnostic errors rather than uncaught exceptions.
- Eight Node suites pass, including rapid mixed Director/HUD actions, 10 loop cycles, 20 Beats, 20 Templates, 260 history changes, linked results, malformed-record preservation, and rapid roll routing.
- **Release gate remains open:** real Foundry multiplayer, server persistence, viewport/audio testing, and security review of GM-only data stored in a shared world setting are not verified here. See `STABILIZATION-REPORT.md`.

## 0.7.1 — GM controls on the compact HUD

- Added GM-only Advance and Regress to each HUD card and each side of a Linked Dynamic HUD.
- Reused the Director’s authoritative action handlers and status restrictions; player markup contains no controls.
- Seven Node suites pass, including HUD actions, linked-side targeting, completed-state disabling, and direct player-handler rejection. Live Foundry click and responsive layout verification remains necessary.


## 0.7.0 — Premium UI, UX, and Accessibility

- Established a reusable dark fantasy palette, typography scale, spacing, borders, and semantic type accents for the Director and dialogs.
- Strengthened Director and Countdown card hierarchy; remaining value, status, current Scene, next Beat, and primary action are easier to scan. Linked Dynamic retains its primary Apply action with secondary challenge controls gathered into More.
- Polished the player HUD and linked presentation with large values, clearly labeled competing sides, readable pressure states, and a static Last Chance marker at a publicly visible value of one. Completion and Beat panels have distinct visual weight.
- Refined Quick Create, editor section headings, Beat sub-cards, Template cards, History timeline, and Roll Router styling. The v0.5 single-scroll editor and fixed action footer are unchanged.
- Added keyboard focus treatments, descriptive tooltips, viewport-aware initial window sizing, stronger contrast, and reduced-motion coverage. Prevented Ominous HUD cards from exposing pressure stages or exact-value hints through markup.
- Preserved v0.6 state, persistence, synchronization, Countdown mechanics, and structured roll detection. No automatic advancement or new rules.

### Tests and limits

Seven Node suites pass, including 6→0 escalation, linked and Beat behavior, randomized loops, Quick Create, Templates, Archive/Restore, Roll Router, and player markup privacy at value one. Live Foundry v14 visual/keyboard/resizing, audio, Dice So Nice, multiplayer, and server-restart verification require a running game client and were not performed here. Browser screenshots are omitted because this environment has no Foundry client.

### Reserved for after 1.0

Optional stream-position presets and alternate visual themes. Neither was implemented in v0.7.


## 0.6.0 — The GM’s Toolbox

- Added five built-in starter Templates and persistent custom Template management; creation from a Template opens the existing editor with editable defaults.
- Added Quick Create and fresh Countdown duplication, with original random formulas resolved only when a new clock is created.
- Organized the Director by status with an archived section, collapsed dashboard controls, current Scene and next Beat hints, and a compact More menu.
- Added Archive/Restore without resetting value, Beats, or status; archived clocks are excluded from the player HUD and Roll Router.
- Added a GM History of the latest 200 meaningful events, with confirmed clearing independent of game state.
- Preserved v0.5 editor scroll layout and existing rule, router, presentation, and sound routines.

### Validation and limits

Seven Node test suites pass, including fresh duplication, templates, archive/restore, bounded history, Quick Create, and a 23-clock Director fixture. A live Foundry v14 session is still needed to verify actual resizable window scrolling and buttons, scene/multiplayer sync, Daggerheart rolls, audio, and persistence across a server restart.


## 0.5.0 — Advanced Countdowns and Editor Scrolling

- Bounded Create/Edit to viewport height; one inner scroll region and a persistent footer.
- Added GM-resolved and persisted randomized starts through Foundry Roll, with explicit Reset versus Reroll/New Run.
- Added Loop, Increasing Loop (+1), and Decreasing Loop (−1), a persistent loop count, safe termination, and Beat re-arming.
- Added manual Long-Term Countdowns and excluded them from Action Roll Router eligibility.
- Loop trigger and next cycle are persisted in one update; completion plays once, while a short HUD banner indicates the new cycle.
- Existing records load with defaults for all new fields; v0.4 presentation, visibility, and GM controls remain.

### Exact SRD behavior and limits

SRD 2.0 p. 91 enumerates random starts; repeating loops; starts increasing/decreasing by one each loop; and long-term advancement after rests. The SRD does not define randomized Reset behavior: Reset retains this run’s resolved start, while New Run explicitly rerolls. Decreasing loops finish after the cycle that starts at one to prevent a zero-value restart; the module limits values to 999. Linked pair sides remain fixed-start in this version. No automatic rest hook was added.

### Tests

Six Node suites pass, covering existing v0.4 regressions and random start validation, unchanged reload, Reset/New Run, two cycles of a Beat, increasing/decreasing loop safety, long-term router exclusion, loop completion sound, and HUD synchronization. A live Foundry v14 session is needed to verify actual editor wheel/scrollbar behavior at 0–20 Beats and short browser heights, as well as Foundry dice, audio, and multiplayer behavior.


## 0.4.0 — Cinematic Tension and Visual Identity

- Added derived Calm, Building, Danger, Critical, and Complete styling with larger HUD values and distinct linked Progress/Consequence pressure.
- Added short CSS-only value and stage entrances, with both client setting and operating system reduced-motion support.
- Grouped multi-value Beat crossings into a single ordered, temporary announcement; completion takes presentation priority and leaves Beat history intact.
- Made completion and Beat announcements automatically dismissible and nonmodal.
- Added optional local sound cues (one highest-priority cue per synchronized change) with client volume and mute settings.
- Added GM-only local Preview and Director card collapse without changing Countdown records.
- Preserved the v0.3 action-roll router, manual Dynamic results, persistence, and visibility boundaries.

### Tests and limitations

Five Node suites passed, including 6→0, priority stages, skipped Beat ordering, linked changes, visibility, manual controls, roll routing, and client synchronization simulations. Live Foundry v14 visual/audio/multiplayer and reduced-motion verification remains necessary; this workspace cannot run a Foundry game client.


## 0.3.0 — GM Action Roll Router

- Inspected Foundryborne Daggerheart 2.9.4 structured DualityRoll ChatMessages; detect completed player Action Rolls through Foundry's `createChatMessage` hook.
- Added an ON by default Action Roll Integration setting and small, nonmodal GM Roll Router. Only the GM's Apply advances a clock; multiple eligible clocks can receive one roll.
- Linked applications reuse the v0.2 Dynamic result routine, including Beat crossing and completion. Standard clocks advance once; standalone Progress/Consequence remain manual.
- Persisted per-message/per-Countdown application records so a repeated hook or reopened view cannot apply the same roll to the same clock twice.
- Moved the manual Apply Roll Result button above the linked clocks and exposed all five advancement amounts in its selection dialog.

### Source and limits

The detected document is `ChatMessage.type === "dualityRoll"`, with the evaluated `message.system.roll`/`rolls[0]` and structured action type, critical and Hope/Fear getters, difficulty/targets, source Actor, user, and message ID. The Daggerheart Tag Team flow emits a single final combined ChatMessage; its interim rolls do not create separate messages. A missing structured success/difficulty is left for the GM to choose. Confirm behavior in a live Foundry v14 world; this workspace cannot execute real Dice So Nice, Help an Ally, Tag Team, multiplayer, or server-restart sessions.

### Automated results

All four Node.js tests pass: five outcomes, advantage/disadvantage/Experience-shaped roll inputs, uncertain success, Tag Team final, eligible-scene filtering, OFF setting, duplicate prevention, multiple clocks, Beat crossings and completion, and the existing v0.2 suite. These are structured-source simulations, not live Daggerheart rolls.

## 0.2.0 — Countdown Beats and Linked Dynamic polish

- Added optional, persistent Story Beats with unique IDs, editing, GM history, player visibility, and a temporary dismissible presentation.
- Crossed Beats fire in descending value order after multi-step advancement; Reset clears them, while Regress does not replay them.
- Added manual official Dynamic roll-result selection, applying both sides together without roll automation.
- Added linked challenge resolve, keep, and reset controls, plus compact paired HUD and clearer GM grouping.
- Preserved the v0.1 world-setting persistence, Countdown controls, scene association, and visibility behaviors.

### Automated results

`model.test.mjs`, `beats-dynamic.test.mjs`, and `interaction.test.mjs` passed under Node.js 24. These cover 6→0, Beat crossing including skipped values, linked result sequence 12/10→10/10→10/7→9/6, Reset, Beat identity, GM/client state changes, visibility, scene switching, and paired persistence through serialization. Live Foundry v14 visual/multiplayer/server restart checks require an actual game session.
