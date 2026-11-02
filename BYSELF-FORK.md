# byself fork of auto_updater_windows

Fork of `auto_updater_windows` 1.0.0 by LeanFlutter
(https://github.com/leanflutter/auto_updater, packages/auto_updater_windows, MIT licence – see LICENSE).

Only change (2 Nov 2026): the bundled WinSparkle is upgraded from **0.8.1 to 0.9.4**
(official binaries from https://github.com/vslavik/winsparkle/releases/tag/v0.9.4,
unmodified; debug .pdb files and 32-bit files left out), and two paths point to
the new folder: `windows/CMakeLists.txt` and the `#include` at the top of
`windows/auto_updater.cpp` (plus the x64 exception in `windows/.gitignore`).

Why: WinSparkle 0.9+ verifies updates with **EdDSA (Ed25519)** signatures, the same
kind Sparkle 2 uses on the Mac, so byself signs Mac and Windows updates with one key.
0.8.1 only supports the deprecated DSA signatures.

Apart from that include path, the plugin's C++ and Dart code are unchanged. Every WinSparkle function it calls
exists in 0.9.4 (checked against include/winsparkle.h).

The public key is supplied by the app (Windows resource `EdDSAPub` of type `EDDSA`
in windows/runner/Runner.rc), not by this package.
