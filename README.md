# Meshy Combat Range

An **in-engine firing demo** of a realistic, multi-theme combat character roster — every character generated via the **Meshy AI API**, rigged + multi-clip animated, and validated in **Godot 4.6.3** (the same engine the Gogi game pipeline targets). This is the Mode-A roster preview: what a pre-staged realistic-character library would actually ship.

## ▶ Play it

**[Launch the demo »](https://joseb33w.github.io/meshy-combat-range/)** — loads in the browser, works on phone (give it ~10–15s on first load; it's a real game engine).

- **Pick a character** (bottom row) — 4 heroes / 4 enemies across 6 themes
- **Switch clips** — idle / walk / run / jump / crouch / walk-back / dodge / aim / fire / reload / hit / death (+ victory for heroes)
- **FIRE** — the weapon actually fires: muzzle flash + tracer, colored per weapon
- **Drag** to orbit

## The roster — 8 characters, 8 themes

| Character | Theme | Role | Weapon |
|---|---|---|---|
| Vanguard | Heavy assault | Hero | Heavy pistol |
| Spec-Ops Soldier | Modern military | Hero | Assault rifle |
| Specter | Stealth ops | Hero | Plasma rifle |
| Warden | Guardian knight | Hero | Sawed-off shotgun |
| Cyber Enforcer | Cyberpunk | Enemy | Arm-cannon |
| Alien Stalker | Sci-fi horror | Enemy | — (melee) |
| Infected Trooper | Horror | Enemy | — (melee) |
| Reaver | Mutant brute | Enemy | — (claws) |

Weapons are mounted to the right-hand bone and aimed down the **forearm** direction (not the wrist twist), so guns point naturally in every pose; the three creatures are melee (no weapon).

## What each character is

- **24-bone Mixamo rig**, **12–13 animation clips merged into one GLB** (heroes 13 with a victory emote, enemies 12)
- A **separate weapon prop** driven from the right-hand bone's pose (orthonormalized, so it never inherits skeleton scale → no stretch), firing forward down the barrel with a muzzle-flash + tracer VFX
- All clips converted to **in-place** (root motion zeroed) so characters stay centered
- Generated realistic + PBR, remeshed, rigged, 1K webp textures
- **Every clip verified to drive the rig** in Godot 4.6.3 (24 bones, all clips animate)

## How it was built

```
per character:  text-to-3D (forced T-pose) → PBR refine → remesh (<300k faces)
                → auto-rig (Mixamo) → 12–13 animation clips
                → merge into one AnimationLibrary (headless Godot)
                → gltf-transform (1K webp, meshopt off) → validate
per weapon:     text-to-3D → refine → optimize → attach to RightHand bone
demo:           Godot 4.6.3, gl_compatibility, nothreads web export
```

Characters are intentionally hard-surface / armored (no loose flowing cloth) so the auto-rig never stretches the mesh on extreme poses.

_Isolated proof-of-concept — no app integration yet. Generated on a Meshy **Studio** plan → owned + host-legal._
