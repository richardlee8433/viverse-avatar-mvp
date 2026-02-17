# AGENTS.md

This repository is used only for generating a VIVERSE WebGL MVP build artifact.

## Goal
Produce a WebGL build output compatible with VIVERSE Studio upload requirements.

## Output Requirements (CRITICAL)

1. Final artifact must be:
   - dist/ folder
   - AvatarMVP_hd87jpxy88.zip

2. ZIP structure must follow:

   AvatarMVP_hd87jpxy88.zip
   ├── index.html
   ├── Build/
   ├── TemplateData/

3. index.html must be at ZIP ROOT.
   Do NOT nest under another folder.

4. Must load latest VIVERSE SDK:
   https://www.viverse.com/static-assets/viverse-sdk/index.umd.cjs

5. Do NOT modify unrelated repository files.

6. Do NOT require git operations or PR merges.

7. Print final ZIP file tree before finishing task.

## Scope

This MVP includes:
- HTC account authentication via VIVERSE SDK
- Fetch authenticated user avatar (.vrm URL)
- Render avatar in Unity WebGL
- No Persona integration yet
- No WebSocket required
