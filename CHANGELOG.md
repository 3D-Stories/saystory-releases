# Changelog

What changed in each published release. Grab the newest installer from the
[latest release](https://github.com/3D-Stories/saystory-releases/releases/latest).

## 0.2.101 — 2026-08-08

### New

- macOS support ships: universal DMG, WhisperKit transcription on Apple Silicon, file logging.
- The WhisperKit large-v3 turbo speech model joins the catalog.
- The sherpa-onnx speech engine lands behind a gate (groundwork for more model families).
- Windows install can register an elevated autostart task, chosen at install time.

### Fixed

- Model download and delete now address the exact model you picked, not its shared slot.
- The chosen speech model is honoured on Windows, and a sideloaded selection is no longer erased.
- Sideloaded multi-file models read as downloaded, and their card actions resolve correctly.
- A CUDA transcription crash from an uninitialized batch (heap corruption) is patched.
- When the CUDA transcriber keeps faulting, the app now falls back to CPU transcription.
- The model picker shows clear "In use" and "Downloaded" states.
- A crashed transcription engine no longer takes a finished transcription with it.

### Under the hood

- The speech-model catalog is pinned to one source shared by every platform, guarded in CI.
- Which speech model actually ran is now recorded in the (metadata-only) diagnostic log.
- The Windows build pins an AVX2 + BMI2 instruction floor with a guard.
- Installer contents are asserted at build time so a broken bundle cannot ship quietly.

## 0.2.76 — 2026-07-29

The previous public release.

## Earlier releases

0.2.61 (2026-07-24) · 0.2.60 (2026-07-23) · 0.2.50 (2026-07-11) · 0.2.49 (2026-07-11) ·
0.2.39 (2026-07-09) · 0.2.38 (2026-07-09, first tagged release).
