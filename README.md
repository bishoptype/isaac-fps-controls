# Isaac FPS Controls

Controls-only improvements for **Isaac FPS Mod 0.5.132**. Rendering/performance changes are maintained separately in [isaac-fps-performance](https://github.com/bishoptype/isaac-fps-performance).

## Changes

- Mouse look uses window coordinates and same-frame cursor/origin projection to cancel camera translation.
- Centered tolerance reduced from 1 to 0.15 render pixels.
- One discarded centered sample replaces the 150ms plus three-sample wait.
- Default sensitivity 0.40 degrees per render pixel; existing saved sensitivity, ADS scaling and pitch limits are preserved. Set 0.40 in mod settings to match the local reference.
- F6 or upper/forward thumb mouse button (Mouse5) toggles FPS mode, once per press.
- Hold LMB to repeat at the existing cooldown; ammo, reload and charged-shot release behavior remain.
- Remove camera recoil/shake while keeping the gun model animation.
- Gun rounds follow the aim pitch without an extra native falling-speed offset. Native lobbed tears retain their original falling component.

## Files

`main.lua`, `fps_settings.lua`, `fps_guns.lua`, `fps_weapons.lua` are ready-to-test replacements for the exact base. `controls.patch` contains the complete diff. **No performance changes or native DLLs are included.**

## Validation

Lua syntax; 84 mouse cases across four scales and three camera offsets; held-fire cooldown/reload/release/pause/charge cases; 48 gun/native-tear pitch cases; F6/Mouse5 press edges. Both split patches reproduce the previously tested combined code byte for byte when applied together. The separately assembled distributions still need the author's own visual and compatibility review.

Mouse input adapted from the user's local First Person v2.3 controls; this uses centered window input, not a native raw-input implementation.

## Base version and installation

Requires the original **Isaac FPS Mod 0.5.132** and its REPENTOGON runtime/assets. This repository is a patch set, not a standalone mod.

For the exact original base: close the game, back up the matching files, and replace only the `.lua` files from this repository. For a newer or locally modified base, merge the diff instead of overwriting files. Restore your backups to undo the changes. Do not delete saves.

**Using both repositories:** both patches apply independently to the original 0.5.132 code, and both application orders have been checked. Apply `controls.patch` and `performance.patch` with `git apply --check` followed by `git apply` for each patch. Do not copy both replacement `main.lua` files on top of each other: the second would overwrite the first repository's changes.

No automatic room recording, recording archives, new diagnostic callbacks, or experimental GPU triangle merging are included. The original mod's manual diagnostics are not enabled by these patches. No saves, game executables or game assets are shipped.

## Credits and licensing

Original Isaac FPS Mod code belongs to its respective authors. Implementation and regression testing assisted by OpenAI Codex. No blanket license or relicensing of the original Lua mod is granted here. This private author-review package retains original ownership; resolve original licensing before any public redistribution.
