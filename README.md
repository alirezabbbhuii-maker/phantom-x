# Phantom X

Phantom X is a VPN client for Android with a redesigned Jetpack Compose interface.
Created by **Alireza Moghyasi**.

It is a fork of [FoxyVPN](https://github.com/Vauth/FoxyVPN) by Vauth, used under the MIT license.
The original copyright notice stays in `LICENSE`.

## Build the APK on GitHub

1. Create a **private** repository and upload this project.
2. Open **Settings > Secrets and variables > Actions** and add two secrets:
   `PHANTOM_EMAIL` and `PHANTOM_PASSWORD` (your Firefox account). Leave them out to show the normal sign-in screen.
3. Open **Actions > Phantom X build > Run workflow**.
4. When it finishes, download `phantomx-debug-apk` from the run page and install the APK.

On first launch the app shows a welcome screen (Persian) with two options: continue with the default account
(only shown when the two secrets exist) or sign in with your own Firefox account, with a short guide to create one.

The credentials are read at build time and are not stored in the source code.
Anyone who receives the APK can extract them, so keep the build for your own use.

## Features added in this version

- Creator badge on the home and welcome screens.
- **Tools** card on the home screen: tunnel speed test, "Fastest server" search and one-tap copy of the exit IP.
- **Recent logs** section on the home screen with copy-all and a shortcut to the full log screen.
- Settings > **Bypass Iranian apps** (on by default): banking, payment, taxi, shopping and other Iranian apps skip the VPN automatically.
- Settings > **Fast IPv6 fallback** (on by default): apps such as Telegram skip IPv6 immediately instead of waiting for a timeout.
- Stability work: faster dead-link detection, a single 403 no longer takes the whole tunnel down, one retry for streams that die while opening, longer idle timeout for long-lived connections.

See `CHANGELOG.md` for details.

## Publish on GitHub

1. Create a repository (private is recommended, see the note above about the build-time credentials) and upload every file in this folder, including the hidden `.github` folder.
2. The Gradle build downloads the native tunnel library ([hev-socks5-tunnel](https://github.com/heiher/hev-socks5-tunnel), version 2.17.1) by itself with `git` the first time it builds, so nothing has to be added to `app/src/main/jni` and no manual step is needed.
3. Open **Actions > Phantom X build > Run workflow** to get a debug APK (`phantomx-debug-apk`).
4. To publish a release, push a tag such as `v1.1.4`. The workflow then builds the release APK and attaches it to a GitHub Release.
   An APK can only be installed when it is signed, so add these secrets first:
   `SIGNING_KEYSTORE_BASE64`, `SIGNING_KEY_ALIAS`, `SIGNING_KEY_PASSWORD`, `SIGNING_STORE_PASSWORD`.
   Without them the release APK is unsigned.
