# Aster-VRM-Root-Editor

Android-first, browser-side editor for VRM 0.x / VRM 1.0 GLB containers.

## V1 features
- Load VRM/GLB and preview it with Three.js + `@pixiv/three-vrm`.
- Detect scene-level RootModel candidates.
- Detect top-level skeleton joint candidates from glTF skin joint hierarchies.
- Edit Position, Rotation (degrees), and Scale independently for RootModel and Root Bone.
- Export by patching the GLB JSON chunk while preserving the original BIN and other chunks.

## Enable GitHub Pages
Open **Settings → Pages → Deploy from a branch → main → / (root)**. Then visit https://evitalove123.github.io/Aster-VRM-Root-Editor/.

## Important limitations
- Root Bone detection is heuristic: it finds top-level joints in glTF skin joint sets. Review the selected node before editing.
- RootModel detection uses the active glTF scene's top-level nodes.
- The editor patches node transforms and preserves other GLB chunks; it does not rewrite inverse bind matrices or recalculate skin weights. Moving a skinned skeleton root may therefore change deformation or animation behavior. Test exported files in a VRM viewer and target apps.
- Center RootModel sets the selected scene-root translation to zero; it is not an automatic geometric recentering algorithm.
- Make a copy of important VRM files before editing.

## Libraries
- Three.js
- @pixiv/three-vrm

No Unity or UniVRM dependency. Files are processed locally in the browser; they are not uploaded to a server.
