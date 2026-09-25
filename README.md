https://github.com/jmart2769gaming/daggerheart-tension-clock/blob/main/module.json

# Tension Clock

**Version 1.0.0 — first stable public release.** Tension Clock is a Daggerheart™ Compatible Foundry VTT module that turns Countdowns into a table-facing GM tool with Story Beats, Dynamic challenges, Action Roll routing, player HUDs, and escalating visual tension. It is an independent third-party product.

## Features

- Standard, Progress, Consequence, Linked Dynamic, and Long-Term Countdowns; optional randomized starts and three loop behaviors.
- Story Beats with skipped-value detection, completion presentations, optional GM-selected local sound cues, and reduced-motion controls.
- A GM Roll Router offers detected Action Rolls for explicit approval. Applying a roll never advances every clock automatically.
- A movable player HUD, GM Advance/Regress controls on its cards, scene association, Templates, Quick Create, Archive/Restore, and a bounded History.

## Requirements and installation

Designed for **Foundry VTT v14** with the **Daggerheart** game system. Daggerheart system 2.9.4 structured roll data was inspected during development; compatibility with newer system revisions and real v14 gameplay still needs owner testing. No CDN or Forge account is required by this module.

Extract the ZIP into Foundry's `Data/modules` folder so the final path is `Data/modules/daggerheart-tension-clock/module.json`. Enable **Tension Clock** in a Daggerheart world. The ZIP has one `daggerheart-tension-clock/` root folder. No update/download URL has been assigned yet.

## Quick start

1. As GM, click **Countdown Director** in the token controls toolbar, then **Quick Create**.
2. Enter a name, starting value, and outcome. Choose a Scene or keep it Global.
3. Use **Advance** to reduce the remaining value by one. At zero, the Countdown completes and shows its outcome; the GM resolves what happens in the fiction.
4. Use **Show HUD** on the toolbar to reopen the display after hiding it. GM HUD cards have Advance and Regress; players have no control buttons.

The GM can click **Show to Players** in the Director header to open connected players' existing HUDs. It restores minimized windows and brings off-screen HUDs into view where possible. This sends a small presentation request after recording an authorization marker separately from Countdown data; each player still sees only clocks allowed by that clock's visibility option. It does not save a persistent player HUD preference.

The GM can also set a value, pause/resume, complete, reset, duplicate, archive/restore, or delete a clock from the Director. Delete requires confirmation. Archived clocks retain their state and are excluded from the player HUD and Roll Router.

## Countdown types

Standard, Progress, and Consequence clocks count down to zero. Linked Dynamic is a parent challenge with independently managed Progress and Consequence sides. **Apply Roll Result** applies the Daggerheart Dynamic Countdown table to both sides in one GM action; either side may still be advanced manually. Long-Term advances manually after rests and is not offered by the automatic Action Roll Router. A looping clock starts a new cycle after triggering; Increasing/Decreasing loops adjust the next starting value by one within the module's 1–999 limit. Random formulas resolve when starting a new run, not on reload; Reset retains the currently resolved start.

## Story Beats

Optional Beats trigger when downward movement reaches or crosses their values. Multiple crossed Beats are recorded in order and shown together. Regressing does not replay them. Reset clears triggered Beat state; Reset Beat History clears only those flags. Completion at zero takes presentation priority over crossed Beats. Beats are a Tension Clock storytelling feature.

## Action Roll integration

With the default **Action Roll Integration** enabled, a completed structured Daggerheart `dualityRoll` ChatMessage can open one GM-only Roll Router. The GM chooses which eligible clocks to affect and can apply one roll to multiple clocks, at most once per clock. Standard advances by one; Linked Dynamic uses the same advancement table as manual Apply Roll Result. If the structured message cannot determine success, the GM chooses Success or Failure. No chat HTML scraping or automatic clock advancement is used. Up to 32 rolls can wait in the router; further rolls remain in chat for manual handling.

Integration uses the message ID, `message.system.roll` or `message.rolls[0]`, action type, critical/Hope/Fear/total fields, and structured difficulty/target information. This was based on the inspected Foundryborne Daggerheart 2.9.4 source; later system data changes may require an update.

## Visibility

| Tension Clock option | Player HUD |
| --- | --- |
| Public | Name, exact numbers, progress, outcome |
| Obscured | Name and relative progress; outcome on completion |
| Ominous | Presence and name, without progress or exact outcome until the generic completion notice |
| GM Only | No player HUD card or presentation |

These labels describe module presentation, not official Daggerheart rules. **Owner manual test — PASS:** in a real game with separate GM and Player clients, the owner reports that the GM could access a GM Only Countdown while the Player could not see or access that information. Automated checks also cover player HUD filtering. The owner did not supply a separate raw world-setting inspection or general security audit; the test result is limited to the reported scenario.

## Templates and settings

Five built-in Templates appear without saving duplicate copies. GMs may save, duplicate, rename, or delete custom Templates; they store configuration rather than runtime value or triggered Beat state. **Action Roll Integration** and **Debug Logging** are world settings. **Sounds**, **Sound Volume**, and **Reduced Motion** are local client settings and do not alter Countdown data. The GM can open **Sounds** from the Countdown Director and select optional **Advance**, **Story Beat**, **Critical**, and **Completion** files using Foundry's host-provided audio picker. Browse starts near that field's selected file or a recently selected audio file when available. These four paths are world settings, blank by default and shared with connected clients; each client's own Sounds and Volume controls still apply. Tension Clock supports optional event sounds selected by the GM. Audio files are not bundled with the module. The GM is responsible for selecting audio they are permitted to use. Debug logging is off by default.

## Compatibility and known limitations

- Built for Foundry v14 and Daggerheart; the owner reports a passing GM Only two-client visibility test. Real v14 sound-picker layout, audio, other multiplayer behaviors, and full server restart verification remain outstanding. See [release verification](RC-TEST-REPORT.md).
- The module is GM controlled. It does not resolve narrative consequences, automatically advance every roll, or automate Long-Term rest progression.
- One GM client serializes its own writes; concurrent edits by multiple GMs have not been tested against conflicts.
- Tension Clock is offered free of charge as a proprietary module. Permitted use in all your worlds, private modification, backups, and player access are documented in [LICENSE.md](LICENSE.md); the copyright holder’s legal name awaits insertion before public release. Daggerheart Public Game Content and Adaptive Content retain their separate DPCGL permissions and attribution in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md). The module must remain free to access and use under the non-commercial Foundry VTT provision. No event audio files are bundled.

## Development and release review

Run `node --test tests/*.test.mjs` from the module folder for the nine automated suites. See [CHANGELOG.md](CHANGELOG.md), [release verification](RC-TEST-REPORT.md), and [OWNER-TEST-CHECKLIST.md](OWNER-TEST-CHECKLIST.md). Saved data remains at `schemaVersion: 1`; this release performs no destructive migration. The DPCGL free Foundry distribution gate is resolved. Insert the copyright holder's legal name in `LICENSE.md` before public distribution.
