---
name: multi-resolution-character-transfer
description: Create reusable multi-resolution character transformation workflows that preserve one character's identity while changing visual representation across live action, 2D animation, high-detail pixel art, low-resolution pixel art, and extreme low-resolution sprites. Use when a user wants prompts, reference-image plans, or a one-take video prompt for sequences such as a character entering a monitor, traveling through a digital network, losing resolution across devices, then restoring back to the original form. Default to Seedance 2.5 for 30-second one-take video prompts unless another model is requested.
---

# Multi-Resolution Character Transfer

Build a production-ready reference pack and video prompt that transforms one character through multiple digital representations without redesigning the character.

Treat the transformation as **information-density change**, not costume change, age change, or character replacement.

## Workflow

1. Establish the character invariants.
2. Design the representation ladder.
3. Create one standalone reference-image prompt per state.
4. Create one standalone background prompt per required environment.
5. Assign references to stable slots such as `@Image 1`, `@Image 2`, etc.
6. Build the video timeline around representation changes and device/network transitions.
7. Add camera-language changes that match each representation state.
8. Add sound-design degradation/restoration that mirrors visual resolution.
9. Run the continuity checklist before returning the final prompt.

## 1. Establish character invariants

Extract or define only the identity traits that must survive every transformation:

- adult age and age impression
- face shape and key facial traits
- hairstyle and hair color
- one or two strong identity markers, such as a ribbon, glasses, earrings, or hairpin
- clothing silhouette and major colors
- body proportions
- footwear
- dominant palette

Keep the invariant list short enough to repeat inside every reference prompt.

Never let a rendering change alter these invariants unless the user explicitly asks for a redesign.

If no strong identity marker exists, choose the most visually stable existing feature rather than inventing a new accessory.

## 2. Design the representation ladder

Use this default ladder unless the user specifies another sequence:

1. **Live-action master** — photographic identity reference.
2. **2D animation master** — same person, same design, clean animation rendering.
3. **High-detail pixel art** — approximately 64-96 px character information.
4. **Low-resolution pixel art** — approximately 32x48 px character information.
5. **Extreme low-resolution sprite** — approximately 16x24 px character information.

Make each stage visibly lower in information density than the previous stage.

Do not merely apply a pixel texture to a high-resolution illustration. For pixel stages, explicitly reduce:

- facial information
- shading bands
- number of colors
- hair detail
- clothing folds
- contour complexity
- animation smoothness

Preserve the strongest identity marker as long as possible, even if it becomes only a few pixels.

## 3. Generate reference assets one image at a time

Default to one prompt per image. Never combine several states into one character sheet unless the user asks for a sheet.

Use a plain white or transparent background for character-state references.

For each character-state prompt:

- state that it is the **same character**, not a redesign
- repeat the invariant traits
- define the target rendering medium
- define the target information density
- forbid unintended age, costume, body-proportion, and accessory changes
- remove unrelated props, UI, text, and backgrounds

For the extreme low-resolution state, require nearest-neighbor enlargement, hard square pixels, no antialiasing, no blur, and very limited colors.

See `references/prompt-patterns.md` for reusable prompt patterns.

## 4. Generate environment references separately

Keep environments person-free unless the user specifically needs a composited keyframe.

Typical environment set:

- real-world room with visibly traceable device connections
- 2D desktop/computer world
- network cable or data-transfer tunnel
- retro low-resolution computer world

Design each environment to explain the transfer path visually. The viewer should understand where the character travels without relying on captions.

Avoid generic cyberpunk imagery unless requested. Prefer device-specific, readable visual logic: monitor, port, cable, second machine, older machine.

## 5. Build the reference map

Before writing the final video prompt, map every input explicitly.

Use a structure like:

```text
@Image 1 = live-action character master
@Image 2 = 2D character master
@Image 3 = high-detail pixel character
@Image 4 = low-resolution pixel character
@Image 5 = extreme low-resolution character
@Image 6 = real-world room
@Image 7 = 2D digital world
@Image 8 = network cable interior
@Image 9 = retro computer world
```

Then declare the role of each reference at the beginning of the video prompt. Do not leave the model to infer which image controls identity, style, or environment.

## 6. Compose the one-take video prompt

Default to Seedance 2.5 when the user requests a 30-second one-generation video.

Use this order:

1. format and duration
2. core concept
3. reference roles
4. character continuity rules
5. timestamped sequence
6. camera and editing direction
7. visual direction
8. audio direction
9. non-negotiable constraints

For 30 seconds, use 6-9 major beats. Do not over-cut every second.

A strong default timing is:

- 0-4s: real world and monitor entry
- 4-8s: transform into 2D
- 8-11s: traverse the digital environment
- 11-15s: network travel
- 15-18.5s: arrive as high-detail pixel art
- 18.5-22s: visible resolution loss
- 22-25.5s: extreme low-resolution world and reaction
- 25.5-28.5s: reverse restoration
- 28.5-30s: return to reality and visual punchline

Use motivated transitions: monitor surface, network port, cable exit, data burst, or display boundary.

## 7. Change camera language with representation

Make the camera itself communicate the representation change:

- live action: natural handheld or cinematic physical camera
- 2D: fluid tracking, pans, low angles, expressive close-ups
- network: fast FPV and strong forward depth
- high-detail pixel: flatter game-like three-quarter view
- low-resolution pixel: side-scrolling composition
- extreme low-resolution: nearly static old-game framing
- restoration: progressively regain smooth movement and camera freedom

Do not keep the same cinematic camera grammar across every state.

## 8. Mirror resolution changes in sound

Whenever practical, make the audio lose and regain fidelity with the image.

Suggested progression:

- real world: room tone and device noise
- 2D world: clean playful electronic sound
- network: fast stereo data pulses and broadband movement
- high-detail pixel: modern chiptune/electronic hybrid
- low-resolution: reduced polyphony and bandwidth
- extreme low-resolution: primitive short game-like tones
- restoration: rebuild sonic detail layer by layer

Use a distinct crisp `SNAP` or compression click for discrete resolution drops.

## 9. Continuity rules

Always enforce these unless the user overrides them:

- Keep exactly one protagonist unless more are requested.
- Preserve adult age across every state.
- Preserve hairstyle, clothing silhouette, palette, body proportions, and key accessory.
- Treat pixelization as information loss, not chibi conversion.
- Do not replace the character with a new design at any transition.
- Do not add random text, captions, logos, or UI labels unless required.
- Make each transformation readable with sound muted.
- Make each resolution stage visibly distinct from adjacent stages.
- Keep the transfer path spatially understandable.

## Output format

Return only the sections needed by the user. For a full production request, use:

### Concept
One short paragraph describing the transfer logic and visual hook.

### Character invariants
A compact list of identity traits that must survive all stages.

### Reference assets
Produce each asset as a separate labeled prompt: `IMAGE 01`, `IMAGE 02`, etc.

### Reference map
Map every created image to its `@Image N` role.

### Final video prompt
Provide one copy-paste-ready Seedance 2.5 prompt with explicit reference roles and timestamped beats.

### Continuity check
List only likely failure points specific to the current character or scene.

## Quality bar

Prefer a simple, legible transformation idea over excessive visual effects.

The viewer should understand the core concept within the first 5 seconds and understand the resolution-loss joke without reading text.

Keep the character cute or expressive through acting and composition, not by changing their age or proportions.

For a reusable public example and submission copy, read `references/renoise-submission.md`.
