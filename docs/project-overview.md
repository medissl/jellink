# Jellink · project overview

[Website](https://jellink.vercel.app) · [Browser game](https://jellink.vercel.app) · [Android releases](https://github.com/medissl/jellink/releases)

## Goal

An approachable physics puzzle with one-thumb controls and no real-time pressure in solo. Playtesting informed the balance: varied bodies make placement matter, frost creates a persistent obstacle, and large Blooms reward growing crowds with expressions, clearing power and sequential reactions.

## Implementation

The browser uses plain JavaScript and Canvas 2D with Vite. Android is a native Java/Canvas implementation with native audio, built with Gradle, Java 21 and Android SDK 36. No Expo, WebView, advertising SDK or always-online requirement.

The custom simulation uses a fixed timestep, curved jar constraints, rounded collision bodies and pressure-driven surface deformation. Rendering includes expressions, coordinated motion, progressive frost, a rainbow Fever HUD, glass reflections and tap-origin chain effects. Adaptive effect quality and cached visual work reduce crowded-scene rendering costs; simulation rules stay intact.

The two clients follow the same rules and achievement catalogue. Browser saves are local storage, Android saves are local preferences. Android online sessions are encrypted with Android Keystore. Resetting local progress does not delete an online identity.

## Optional multiplayer

Supabase provides guest authentication, Postgres storage and an authenticated game referee. The server validates room membership, turns and moves and calculates competitive results. Database tables deny direct client writes. Room revision checks prevent simultaneous moves being applied twice. Versus uses a shared seed and compares score, then largest link; Co-op alternates accepted drops into one jar. Solo remains independent. The friends leaderboard compares synced, device-reported solo personal bests. These are separate from server-calculated competitive match results. Opening the board refreshes its ranks; finishing a solo run syncs the record, and reconnecting catches up offline progress. Offline play remains available with a brief connection notice.

Guest accounts require no email. Email recovery needs public mail delivery to be configured and verified; it is not required for friends or invite matches.

## Delivery and verification

Vercel builds the website from the private source repository. GitHub Actions tests the engine and native controls, captures real Android screens, builds the native APK and signs it with the existing release identity. A narrowly scoped publishing key transfers only the verified APK, checksum and release metadata to this public repository. The download pipeline verifies the signing certificate before release.

Verification covers gravity, compression, curved boundaries, continuous motion, frost, overflow rescue, anti-spam input, cancellation, sequential chains, save restoration, achievement persistence and online isolation. Live tests exercised a full three-minute match, correct leaderboard results, friend-request ownership and shared-turn gating. Software-emulator performance checks are recorded internally; they do not guarantee a frame rate on every phone.

## Portfolio and rights

Created by Medissl. This public repository is the project showcase and distribution point. The implementation repository is private; official builds and gameplay screenshots may be shared subject to the [licence](../LICENSE). Fredoka retains its SIL OFL licence.
