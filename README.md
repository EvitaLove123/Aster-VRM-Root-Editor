# Aster-VRM-Root-Editor

Android-first, browser-side editor for VRM 0.x / VRM 1.0 GLB containers.

## V1.3 features
- Load VRM/GLB and preview it with Three.js + `@pixiv/three-vrm` (with a standard GLB preview fallback).
- Auto-frame the model using its 3D bounds; resize-aware preview and touch-friendly OrbitControls.
- Detect scene-level RootModel candidates and top-level skeleton root candidates.
- Bone Multi-Select: searchable checklist of detected skin joints, VRMC_springBone joints, VRM 0.x secondaryAnimation bones, and bone-like named nodes (including hair/ear/tail names).
- Select all detected bones or clear the selection.
- Apply shared Position offsets, Rotation offsets (degrees), and Scale multipliers to selected bones while preserving each bone's individual starting transform.
- Edit Position, Rotation (degrees), and Scale independently for RootModel and Root Bone.
- Read glTF nodes stored as either TRS or a 4×4 matrix; edited nodes are written back as TRS.
- Reset the selected node, center the selected RootModel translation, or discard all edits and restore the original preview.
- Export by patching the GLB JSON chunk while preserving the original BIN and other chunks.

## Enable GitHub Pages
Open **Settings → Pages → Deploy from a branch → main → / (root)**. Then visit https://evitalove123.github.io/Aster-VRM-Root-Editor/.

## Important limitations
- Bone detection is best-effort. Some custom hair/ear/tail rigs may use unlabelled nodes or extension layouts that are not detected; search the list and inspect the model's hierarchy when needed.
- Root Bone detection is heuristic: it finds top-level joints in glTF skin joint sets. Review the selected node before editing.
- RootModel detection uses the active glTF scene's top-level nodes.
- Group edits apply local TRS offsets/multipliers to each selected node; they do not calculate mirrored transforms or preserve physical spring simulation constraints.
- The editor patches node transforms and preserves other GLB chunks; it does not rewrite inverse bind matrices or recalculate skin weights. Moving a skinned skeleton root may therefore change deformation or animation behavior. Test exported files in a VRM viewer and target apps.
- Center RootModel sets the selected scene-root translation to zero; it is not an automatic geometric recentering algorithm.
- Make a copy of important VRM files before editing.

## Libraries
- Three.js
- @pixiv/three-vrm

No Unity or UniVRM dependency. Files are processed locally in the browser; they are not uploaded to a server.
