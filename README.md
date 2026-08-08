# SayStory releases

Installer downloads and the in-app auto-updater feed for **SayStory** — private, local dictation that
turns speech into polished text: press a hotkey, speak, release, and cleaned-up text lands at your
cursor in whatever app you're using. Speech-to-text and text cleanup run **locally** — no cloud STT
or cloud LLM in the default path, no telemetry, no accounts.

The application source lives in the private repo [3D-Stories/saystory](https://github.com/3D-Stories/saystory);
this repo hosts only the public installer downloads and the updater feed.

## Download

Grab the newest installer from the [**latest release**](https://github.com/3D-Stories/saystory-releases/releases/latest):

| Platform | Installer |
| --- | --- |
| **Windows** x64 (NVIDIA RTX-class GPU recommended) | `SayStory-windows-x64-setup.exe` |
| **macOS** 13.3+ (Apple Silicon) | `SayStory-darwin-universal.dmg` |

The macOS `*.app.tar.gz` + `.sig` assets are the signed artifacts the in-app updater consumes; you
don't download those by hand.

### First run
- **Windows:** the v1 installer is unsigned, so SmartScreen will warn — choose **"More info → Run
  anyway."** First-run setup detects your hardware (CUDA on NVIDIA GPUs), recommends STT + cleanup
  models, checks microphone permission, and offers the model downloads.
- **macOS:** open the `.dmg` and drag **SayStory** to Applications. The app is ad-hoc signed for
  now, so Gatekeeper blocks a plain double-click on first open: **right-click the app, choose
  Open, then Open again.** After that, grant **microphone** access (to hear you) and
  **accessibility** access (to type at your cursor).

Optional stronger cleanup on either platform: install [Ollama](https://ollama.com) and pull a local
model — SayStory finds it automatically over localhost.

## Minimum requirements

| | Windows | macOS |
|---|---|---|
| OS | Windows 10 or 11, 64-bit | macOS 13.3 or newer |
| CPU | AVX2 + BMI2 (Intel "Haswell" 2013 or newer, any AMD Ryzen) | Apple Silicon (M1 or newer) |
| GPU | Optional — an NVIDIA GPU speeds up transcription | Neural Engine used automatically |
| Disk | ~600 MB app + models (below) | ~30 MB app + models (below) |
| Network | Model downloads only | Model downloads only |

Model downloads are one-time: speech models 0.2–1.5 GB each, cleanup models 1.3–5.7 GB each.
While dictating, expect free memory use roughly the size of the cleanup model you chose. Nothing
is sent to a cloud at runtime.

## Auto-update

SayStory updates itself from the feed at `releases/latest/download/latest.json`. Update checks are
**opt-in** — enable them in Settings. Every update is cryptographically signed (the `.sig` assets),
so the updater only installs builds published here.

## Privacy

Local by default — your voice stays on your device. No transcript text in logs, no telemetry, and no
audio retention beyond the local, opt-in transcript history (dictations into password managers are
never retained). The full privacy policy ships with the app.

---

_Latest release: **v0.2.101**. What changed in each release: [CHANGELOG.md](CHANGELOG.md). This
page always points at the newest build; older versions remain available under
[Releases](https://github.com/3D-Stories/saystory-releases/releases)._
