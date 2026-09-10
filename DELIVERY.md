# Class Break delivery

Date: 2026-09-10. Direct playable HTML ZIP for GameGen, with the classroom group cover explicitly selected in the user's final attachment. The GitHub repository retains the complete React/TypeScript source and final cover; the local source checkout is removed after successful push as requested by the user.

## Package

- Name: `class-break.zip`, placed alongside the other games in `noskin-delivery/`.
- ZIP root: built `index.html`, one `poster.webp`, `assets/`, `common/`, and `config/`.
- 45 runtime files, 51,169,177 bytes.
- SHA-256: `bcc39fdd5635a669d7fbeecf9321739cb4721a6180ce78784278de0df142cf12`.
- Cover: lossless WebP, 936 × 1664, exact 9:16. Source `public/poster.webp`, copied to `dist/poster.webp` by Vite; not added to the gameplay manifest.
- ZIP contains no source, dependency directories, Git metadata, test output, prompt documents, or candidate images.

## Checks

- React 19.2.8, TypeScript 7.0.2, Vite 7.3.6, Vitest 3.2.7.
- Existing tests: 28 passed across 3 files (game logic, asset resolution, secret unlock).
- TypeScript: `tsc -b --pretty false` passed.
- Production build: `vite build --configLoader runner` passed; invoked installed Node entry points directly, without changing dependencies or lockfiles.
- ZIP CRC, unique entry names, root index/cover, poster decode and aspect ratio passed.
- All 45 extracted files returned matching bytes over HTTP at `/class-break/`; every ZIP file matches the local build.
- Browser: preload reaches the explicit Enter game gate, entering opens the homepage, all four locale options change UI text, BGM toggle changes state, Lumi can enter a class, complete the 60-second countdown, and reach the time-up result screen. No warning/error logs or broken visible images were observed.
- All four locale files contain the same 47 keys. English is the fresh-session default.

## Assets and fallback

Source images: `public/common/textures/`; audio: `public/common/audio/`; font: `public/common/fonts/chalk_jp.otf`; four locales: `public/config/language/{en,zh-TW,zh-CN,ja}.json`. The built package omits the `public/` prefix.

Existing per-asset resolution remains style → commonPath → local common → local public, with independent failure handling. The package has an empty commonPath and works with local bundled assets at a subpath. No game logic, asset naming, sprite slicing, localization, or loading behavior was changed for this cover delivery.

## Limits

No actual GameGen backend upload was performed. Full gameplay regression, subjective audio listening, and live remote style/commonPath failure scenarios were not re-tested. Existing fallback logic tests passed; the four-language UI smoke test does not establish full translation quality. No new compliance exception was introduced.
