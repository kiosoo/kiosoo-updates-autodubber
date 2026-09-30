# AutoDubber Studio Updates

Signed update manifests and optional component catalog for AutoDubber Studio.

Release assets contain optional runtime and model packs. Large ZIP files are not committed directly to this repository.

## Current release

- Core installer: AutoDubber Studio `1.8.8`
- Whisper: CPU-only by default; it does not depend on a shared NVIDIA runtime.
- OmniVoice: optional `omnivoice-runtime` `0.2.0` component, using an isolated Torch `2.8.0 + cu128` worker.
- GPU behavior: the worker detects the installed NVIDIA driver/GPU and reports a structured preflight result; CUDA failure can fall back to a fresh CPU worker.
- The OmniVoice runtime is published as four multipart ZIP assets under the existing `components-v1.8.4` component release (the runtime itself is unchanged). The app verifies every part and the reconstructed archive SHA-256 before extraction.
- The v1.8.8 installer uses the signed `verified_auto` update path: the app downloads it in the background, verifies the signed manifest and SHA-256, closes itself, and starts the installer through the detached update helper.
