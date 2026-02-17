# viverse-avatar-mvp

This repository produces a VIVERSE Studio upload-compatible WebGL MVP package for app id `hd87jpxy88`.

## What this includes

Source files are stored in `web-src/` and copied into generated `dist/` for packaging:

- `index.html` with VIVERSE SDK UMD load (`https://www.viverse.com/static-assets/viverse-sdk/index.umd.cjs`)
- Auth flow wiring:
  - Creates `globalThis.viverseClient = new globalThis.viverse.client({ clientId, domain })`
  - Runs `checkAuth()` on `window.load`
  - If auth is undefined, runs `loginWithWorlds()` for SSO refresh
  - Displays `account_id` and token expiry fields when authenticated
- "Fetch Avatar" button with explicit Avatar SDK TODO stub and user-facing status output
- `Build/` placeholder structure (not a real Unity runtime in this environment)
- `TemplateData/style.css`

## Generated artifact

- `dist/`
- `AvatarMVP_hd87jpxy88.zip` (created by zipping the **contents** of `dist/`, so `index.html` is at ZIP root)

## Build/package steps

```bash
rm -rf dist AvatarMVP_hd87jpxy88.zip
cp -R web-src dist
cd dist && zip -r ../AvatarMVP_hd87jpxy88.zip .
```

## Upload to VIVERSE Studio

1. Open VIVERSE Studio upload for Web content.
2. Upload `AvatarMVP_hd87jpxy88.zip`.
3. Confirm ZIP root contains:
   - `index.html`
   - `Build/`
   - `TemplateData/`

## Real vs stub in this MVP package

- Real:
  - VIVERSE SDK script load
  - Client initialization/auth flow scaffolding
  - UI flow and status handling
- Stub (explicit):
  - Avatar SDK API request to resolve final `.vrm` URL (left as TODO because endpoint/method availability can differ by SDK version)
  - Unity WebGL runtime binaries in `Build/`

## Next steps for full Unity integration

1. Produce an actual Unity WebGL build and replace `dist/Build/*` with Unity-generated loader/framework/data/wasm files.
2. Bridge fetched avatar `vrmUrl` from page JS into Unity (e.g., JS interop + C# handler).
3. Replace TODO avatar API stub with official SDK/API call once endpoint contract is finalized.
