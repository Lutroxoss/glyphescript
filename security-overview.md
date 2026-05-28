# GlypheScript — Security & Data Handling Overview

> One-pager for IT security review. Covers what data the app accesses, where it stores it, what network traffic it generates, and what permissions it requests. Last updated 2026-05-28.

## At a glance

| Aspect | Behavior |
|---|---|
| **Platform** | Windows-only (10/11, x64). No macOS / Linux builds produced or distributed. |
| **Data residency** | 100% local. Everything stored in the user's Windows `%APPDATA%\GlypheScript\` folder. |
| **Telemetry** | None. No analytics, no usage reporting, no crash reporting to any server. |
| **Cloud sync** | None. No account system. No login. No remote backup. |
| **Code signing** | ✅ **Signed.** Installer signed via Microsoft Trusted Signing as of v1.1.0-beta.2. Publisher cert recognized by Windows SmartScreen — no "Unknown publisher" warning. |
| **Network traffic** | One default outbound path (update check), all user-toggleable. Detailed below. |
| **Auto-update** | Checks `github.com/Lutroxoss/glyphescript/releases/latest.yml` on launch. Toggleable off in Settings → Updates. |
| **Crash reports** | Written to local `crash.log` file. Never transmitted. User chooses if/when to attach it to a bug report. |
| **Auth / credentials** | None stored. App does not handle passwords or tokens. |
| **MCP integration (optional)** | Local-only inter-process pipe between the app and a Claude Desktop subprocess on the same machine. No remote access. |
| **License** | Apache License 2.0. Source publicly auditable. |
| **Privacy policy** | https://glyphescript.app/privacy |

## What the app does

GlypheScript is a step-by-step guide creator for documenting workflows. It listens for mouse clicks and keystrokes during a **user-initiated recording session**, captures screenshots of the user's screen at each click, and saves them along with text annotations to a local file. The user explicitly starts and stops recording; nothing is captured outside an active recording session.

Typical use cases: writing customer-service SOPs, IT runbooks, training material, software walkthroughs.

## What data is stored, and where

All data lives under `%APPDATA%\GlypheScript\`. No registry writes outside the file-association keys under `HKCU\Software\Classes\` (and only if the user has those associations enabled).

| File / folder | Contents |
|---|---|
| `db.json` | All guides, steps, annotations as JSON. Plain-text, user-readable. |
| `uploads/` | PNG screenshots captured during recordings. |
| `settings.json` | User preferences (capture defaults, backup folder, theme, etc.). |
| `crash.log` | Local-only error log. |

The user can delete the entire folder to fully remove all app data. The app does not write to any other system location.

## Network behavior — full list

GlypheScript makes outbound HTTPS connections **only** in these cases:

1. **Update check on launch (user-toggleable).** Reads `https://github.com/Lutroxoss/glyphescript/releases/latest.yml` (or `beta.yml` for opted-in beta users) to check if a newer version is available. Same HTTP request any browser makes when visiting GitHub. **Disable** in Settings → Updates → "Check for updates on launch."
2. **Manual external link clicks (user-initiated only).** When the user clicks "Documentation," "Privacy policy," "GitHub releases," or similar links in Settings/About, the system browser opens the URL. No data leaves the app — just a URL handoff to the OS.

GlypheScript does **not** send any user data, screenshots, telemetry, or crash reports to any external server. No analytics SDK. No third-party reporting libraries.

### Optional integration — Claude Desktop (MCP)

If the user pastes the GlypheScript MCP config snippet into Claude Desktop and restarts Claude Desktop, the app spawns a subprocess (`GlypheScript.exe --mcp-stdio`) and communicates with it via a local named pipe. **No remote endpoint involved.** Claude Desktop itself has its own network behavior governed separately by Anthropic; that's outside GlypheScript's scope.

This integration is **off by default** — it only activates if the user explicitly configures Claude Desktop with the snippet from Settings → About.

## Permissions requested

GlypheScript runs as a standard Windows desktop app (**no admin elevation required**). It uses:

| Permission | Why | Source |
|---|---|---|
| Screen capture (`desktopCapturer`) | Take screenshots of the user's screen when they click during a recording session. | Built into Electron / Chromium; no separate Windows permission prompt. |
| Global mouse + keyboard listener (`uiohook-napi`) | Detect clicks and keystrokes during an active recording session. **Listener is registered when "Start Recording" is clicked and unregistered on Stop** — not active outside a recording. | npm package; cross-platform input hook. |
| File I/O in `%APPDATA%\GlypheScript\` | Save guides, screenshots, settings. | Standard userland write — no admin needed. |
| Network egress to `github.com` | Update check only. User-toggleable. | electron-updater. |

The app does **not** request or use: clipboard access, camera, microphone, location services, contacts, push notifications, or admin/elevation.

## Update integrity

- Updates are distributed via GitHub Releases as **code-signed `.exe` installers**.
- Code-signing publisher: verified via Microsoft Trusted Signing (identity-verified individual publisher; the same trust chain Windows uses for any commercial signed installer).
- Each release also includes a SHA-512 `blockmap` so the auto-updater can validate delta integrity.
- The installer's signature is verifiable by right-clicking the `.exe` → Properties → Digital Signatures.

## Supply chain

- Source code is publicly auditable at `https://github.com/Lutroxoss/glyphescript`.
- Built on Electron 34 + React 18 — both mainstream, actively maintained projects.
- All dependencies declared in `package.json` / `package-lock.json`; reproducible with `npm install`.
- `npm audit` is run as part of release prep. No known critical CVEs at the last published-version cut.
- An SBOM (CycloneDX or SPDX) can be generated on request if your review requires one.

## Vendor info

- **Developer:** Lutroxi (`lutroxoss@proton.me`)
- **License:** Apache License 2.0 — see `LICENSE` in the repository root
- **Privacy policy:** https://glyphescript.app/privacy
- **Support:** GitHub Issues at `https://github.com/Lutroxoss/glyphescript/issues`, or the email above for security-specific reports

## For IT — independent verification

If your org wants to confirm any of the above without taking our word for it:

1. **Confirm no telemetry / no unexpected egress** — install the app, run Wireshark / Process Monitor while exercising recording + editing features. The only outbound traffic should be the GitHub `latest.yml` / `beta.yml` request at launch (and only if "Check for updates on launch" is enabled).
2. **Confirm local-only storage** — verify all writes land in `%APPDATA%\GlypheScript\`. No registry writes outside `HKCU\Software\Classes\` (file association only).
3. **Verify the digital signature** — right-click `GlypheScript Setup x.x.x.exe` → Properties → Digital Signatures. Should show a valid Trusted Signing chain.
4. **Review source** — public GitHub repo above. Reproduce the binary from source with `npm install && npm run build` to confirm the installer matches what's in the repo.
5. **Check dependency tree** — run `npm audit` against the repo to confirm no critical CVEs.

## Contact for security questions

`lutroxoss@proton.me` or open an issue at https://github.com/Lutroxoss/glyphescript/issues.

For responsible disclosure of any security finding, please use the email above directly rather than a public issue.
