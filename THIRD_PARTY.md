# Third-party components

bTunes is closed source (LICENSE.md). It is built on the open-source components below, each under its own licence; those licences apply to those components. Dependencies are used as libraries, not copied into bTunes' source, unless a line says otherwise. Each one's transitive dependencies carry their own notices (the lock files list them: `app/package-lock.json`, `app/src-tauri/Cargo.lock`, `dsp/Cargo.lock`, `plughost/Cargo.lock`).

## The app

- Tauri 2 (https://tauri.app), MIT OR Apache-2.0: the desktop shell, with `tauri-plugin-dialog` and the `@tauri-apps/api` and `@tauri-apps/plugin-dialog` npm packages. Copyright the Tauri Programme within The Commons Conservancy. On Windows the app uses Microsoft Edge WebView2 through `WebView2Loader.dll` (Microsoft, distributed under the WebView2 runtime terms).
- React and React DOM 19 (https://react.dev), MIT. Copyright Meta Platforms, Inc. and affiliates.
- Ajv (https://ajv.js.org), MIT: song file schema checks. Copyright Evgeny Poberezkin.
- Rust crates used by the app (`app/src-tauri`): `serde` and `serde_json` (MIT OR Apache-2.0), `notify` (CC0-1.0), `keyring` (MIT OR Apache-2.0), `tar` (MIT OR Apache-2.0), `sha2` and `md-5` (RustCrypto, MIT OR Apache-2.0), `chrono` (MIT OR Apache-2.0), `tiny_http` (MIT OR Apache-2.0), `ureq` (MIT OR Apache-2.0), `lofty` (MIT OR Apache-2.0), `urlencoding` (MIT).

## The plugin helper (`btunes-plughost`)

- clack (`clack-host`, `clack-extensions`, https://github.com/prokopyl/clack), MIT OR Apache-2.0, and `clap-sys` (MIT OR Apache-2.0): CLAP plugin hosting.
- `vst3` 0.3 (https://github.com/coupler-rs/vst3-rs), MIT OR Apache-2.0: VST3 bindings. VST is a trademark of Steinberg Media Technologies GmbH.
- `libloading` (ISC), `base64` (MIT OR Apache-2.0), `tungstenite` (MIT OR Apache-2.0); in the 'live' build also `cpal` (Apache-2.0) and `rtrb` (MIT OR Apache-2.0).
- Surge XT (GPL-3.0) and Vital (GPL-3.0, with a separate licence for its presets and the Vital app): **not included**. bTunes loads only the copy the user installed (`docs/plugins.md`).

## The engine (Python)

- Core: NumPy (BSD-3-Clause), SciPy (BSD-3-Clause), soundfile (BSD-3-Clause, with libsndfile, LGPL-2.1), pyloudnorm (MIT), jsonschema (MIT).
- Optional extras, not shipped with bTunes: `pedalboard` (GPL-3.0, Spotify), `dawdreamer` (GPL-3.0), `vita` (GPL-3.0, Vital's engine as a Python module), `matchering` (GPL-3.0). They are not in the bTunes download: when the engine is set up on a computer (Settings > Install), the engine's installer fetches them from PyPI onto that computer, and the engine runs without them where they will not install.
- FFmpeg (LGPL-2.1 or GPL depending on the build) is used when present on the computer; it is not included.

## The synths (`dsp/`)

- `libm` (MIT), and for the engine's Python module PyO3 (MIT OR Apache-2.0) and the `numpy` crate (BSD-2-Clause).

## Sounds

- Demo drum samples (`bd_tek`, `hat_gem`, `hat_zild`, `perc_snap`, `elec_snare`, `drum_splash_hard`) are from the Sonic Pi sample pack (https://sonic-pi.net), CC0 1.0 (public domain). They are fetched by the render worker, not kept in the repository.
- The demo's Vital presets `massive saws` and `nice lead` are third-party presets released under the Unlicense. The demo's `V-bass` preset and vocal (`ace-dry.wav`) are fetched onto the render worker with them for the demo only; neither ships in the repository.
- No commercial audio is in bTunes or its repository.
