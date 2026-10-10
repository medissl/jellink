# Jellink · project overview

[Website](https://jellink.vercel.app) · [Browser game](https://jellink.vercel.app) · [Android releases](https://github.com/medissl/jellink/releases)

## Goal

An approachable physics puzzle with one-thumb controls and no real-time pressure in solo. Playtesting informed the balance: varied bodies make placement matter, frost creates a persistent obstacle, and large Blooms reward growing crowds with expressions, clearing power and sequential reactions.

## Implementation

The browser uses plain JavaScript and Canvas 2D with Vite. Android is a native Java/Canvas implementation with native audio, built with Gradle, Java 21 and Android SDK 36. No Expo, WebView, advertising SDK or always-online requirement.

The custom simulation uses a fixed timestep, curved jar constraints, rounded collision bodies and pressure-driven surface deformation. Rendering includes expressions, coordinated motion, progressive frost, a rainbow Fever HUD, glass reflections and tap-origin chain effects. Adaptive effect quality and cached visual work reduce crowded-scene rendering costs; simulation rules stay intact.

The two clients follow the same rules and achievement catalogue. Browser saves are local storage, Android saves are local preferences. Android online sessions are encrypted with Android Keystore. Resetting local progress does not delete an online identity.

## Optional multiplayer

Supabase provides guest authentication, profiles, invitations, lobbies and match checkpoints. Private Realtime Broadcast uses membership policies and separate sender topics: players can publish only to their own channel. Status reads do not simulate physics or compete for a global turn revision.

Versus supports two to five players and runs an independent local jar on each device, sharing a seed and ordinary delivery queue. Opponent progress never replaces your jar. Co-op uses the host's game engine, unique acknowledged guest commands, duplicate protection, alternating accepted drops and compact ordered snapshots with interpolation and idle traffic suppression. Disconnecting pauses the shared game until the pair reconnects; there is no host migration.

Both modes have a host-controlled Ready/Start lobby, countdown, results and rematch lobby. Versus displays up to four opponents live without covering the jar, with time alerts and a suspenseful winner reveal. Scores are device-reported with bounds and sequence checks for casual friend play, rather than advertised as cheat-proof competitive rankings. Solo remains local and offline; leaving a match restores the solo jar. Friend leaderboards compare synced solo personal bests.

Names and bios save while typing, with durable drafts and account-scoped writes. Clickable player portraits open public profile cards. Leaderboards use a fixed scrollable frame. Profiles support cropped 192px JPEG photos, preset portraits, bios and three earned achievement badges. Friends have search, requests, invite/remove actions and optional activity. The Friends panel stays the same size across tabs and scrolls internally. Codes copy with a tap. Guest registration upgrades the same identity with optional email/password sign-in and preserves its friend code. Local solo progress stays on the device.

## Delivery and verification

Vercel builds the website from the private source repository. GitHub Actions tests the engine and native controls, captures real Android screens, builds the native APK and signs it with the existing release identity. A narrowly scoped publishing key transfers only the verified APK, checksum and release metadata to this public repository. The download pipeline verifies the signing certificate before release.

Verification covers gravity, compression, curved boundaries, continuous motion, frost, overflow rescue, anti-spam input, cancellation, sequential chains, save restoration, achievement persistence and online isolation. Browser checks cover two-player drops under delayed background requests, repeated Co-op messages, reconnect, results/rematches, profile photo sharing, fixed Friends layouts and copying codes. Android checks use native controllers and real private Broadcast, alongside emulator touch/render checks. Software-emulator performance checks are recorded internally; they do not guarantee a frame rate on every phone.

## Portfolio and rights

Created by Medissl. This public repository is the project showcase and distribution point. The implementation repository is private; official builds and gameplay screenshots may be shared subject to the [licence](../LICENSE). Fredoka retains its SIL OFL licence.
