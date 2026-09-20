# Prompt Patterns

## 1. Same-character conversion pattern

Use this pattern for every representation state:

```text
Use the supplied character as the identity reference.
Reconstruct the exact same adult character in [TARGET MEDIUM].
This is not a redesign and not a different person.
Preserve: [FACE], [AGE], [HAIR], [KEY MARKER], [CLOTHING], [PALETTE], [BODY PROPORTIONS].
Change only the rendering medium and information density.
[STATE-SPECIFIC TECHNICAL RULES].
Plain white or transparent background. One character. Full body. Front view.
No text, UI, props, extra characters, costume redesign, age change, or body-proportion change.
```

## 2. High-detail pixel state

```text
Render the same character as high-quality modern pixel art representing approximately 64-96 pixels of character information.
Use clear square pixels, limited but expressive shading, readable facial features, and a preserved silhouette.
No antialiasing, no blur, no vector-smooth edges.
Do not create a chibi version.
```

## 3. Low-resolution pixel state

```text
Reduce the same character to approximately 32x48 pixels of character information.
Simplify hair into larger blocks, remove most fabric folds and secondary shading, reduce facial features to the minimum readable arrangement, and keep the strongest identity marker visible in only a few pixels.
Use a smaller palette and hard stepped contours.
```

## 4. Extreme low-resolution state

```text
Reduce the same character to approximately 16x24 pixels of character information.
Preserve identity primarily through silhouette and four or fewer dominant color groups.
Eyes and mouth may be one or two pixels each.
Use nearest-neighbor enlargement, hard square pixels, no antialiasing, no blur, and no smooth lines.
The result must look genuinely low-resolution, not like a pixel filter placed over a high-resolution drawing.
```

## 5. Environment pattern

```text
Person-free environment designed for video compositing and spatial continuity.
Show a clearly understandable path from [SOURCE DEVICE/SPACE] to [DESTINATION DEVICE/SPACE].
Keep important entrances, exits, ports, cables, and travel directions visually legible.
Avoid decorative complexity that obscures the route.
No readable text and no people.
```

## 6. Seedance 2.5 reference-role block

```text
Use @Image 1 strictly as the live-action identity of the protagonist.
Use @Image 2 as the exact 2D version of the same protagonist.
Use @Image 3, @Image 4, and @Image 5 as progressively lower-resolution representations of exactly the same character.
Use @Image 6 for the real-world environment.
Use @Image 7 for the 2D digital environment.
Use @Image 8 for the transfer/network environment.
Use @Image 9 for the extreme low-resolution destination environment.

The protagonist must remain recognizably the same adult person throughout every visual transformation. Only rendering medium and information density may change.
```

## 7. Resolution-transition wording

Prefer discrete wording for visible degradation:

```text
Do not morph smoothly.
Reduce the character in clearly visible discrete steps.
SNAP: remove secondary shading.
SNAP: collapse hair and clothing detail into larger blocks.
SNAP: reduce facial information and palette.
The character remains the same person at every step.
```

Avoid vague wording such as "becomes pixelated" when stage distinction matters.
