# Multi-Resolution Character Transfer

## Overview

Multi-Resolution Character Transfer is a reusable visual workflow for transforming one character through multiple digital representations while preserving the character's identity.

A character can begin as live action, enter a display, become a 2D animation character, travel through a digital network, and progressively lose visual information as they move to lower-capability devices:

**Live Action -> 2D Animation -> High-Detail Pixel Art -> Low-Resolution Pixel Art -> Extreme Low-Resolution Sprite**

The workflow can then reverse the same states and restore the character to the original live-action form.

The important idea is that the character is not redesigned at each stage. Only the **representation medium and information density** change.

## Intended use

Use this workflow for:

- character transformation videos
- digital-world travel sequences
- monitor / device transition videos
- network or data-transfer visual storytelling
- retro-computing themed videos
- one-take AI video demonstrations
- reusable character-consistency tests across visual media

## Inputs

Minimum input:

- one character image or clear character description

Recommended input:

- target duration
- aspect ratio
- desired transfer path or device sequence
- preferred video model
- optional final punchline or ending

## Outputs

The workflow produces:

1. a character identity invariant list
2. a live-action or primary character master prompt
3. a 2D character reference prompt
4. a high-detail pixel-art reference prompt
5. a low-resolution pixel-art reference prompt
6. an extreme low-resolution sprite prompt
7. separate environment prompts
8. a reference-image assignment map
9. a timestamped one-take video prompt
10. continuity and failure-prevention rules

## Default resolution ladder

### Stage A - Live Action
Use the highest-information identity reference.

### Stage B - 2D Animation
Preserve the same face, age, hairstyle, accessory, clothing, palette, and body proportions. Change only rendering medium.

### Stage C - High-Detail Pixel Art
Represent approximately 64-96 pixels of character information with clean square pixels and enough detail to preserve facial identity.

### Stage D - Low-Resolution Pixel Art
Reduce to approximately 32x48 pixels. Remove secondary shading, clothing folds, and minor facial details.

### Stage E - Extreme Low Resolution
Reduce to approximately 16x24 pixels. Preserve identity mainly through silhouette and dominant color groups.

## Core technique

Choose a small set of character invariants before generating any transformed states.

Good invariants include:

- hair silhouette and color
- one strong accessory or marker
- dominant clothing colors
- body proportions
- face shape
- age impression

Repeat these invariants in every state prompt.

For pixel-art states, do not ask only for a "pixel-art style." Explicitly reduce information density at each step. A convincing transformation should lose detail in stages rather than apply a uniform pixel texture.

## Video construction

For a 30-second Seedance 2.5 sequence, a reliable structure is:

- 0-4s: real world and display entry
- 4-8s: live action to 2D transformation
- 8-11s: travel through the digital environment
- 11-15s: network transfer
- 15-18.5s: high-detail pixel arrival
- 18.5-22s: visible compression / resolution loss
- 22-25.5s: extreme low-resolution world and character reaction
- 25.5-28.5s: reverse restoration
- 28.5-30s: return to reality and visual punchline

Change camera language together with rendering medium: cinematic handheld in reality, fluid animation camera in 2D, FPV inside the network, flatter game framing in pixel worlds, and nearly static framing at the lowest resolution.

Sound can follow the same progression by reducing bandwidth and polyphony as image resolution decreases, then restoring fidelity during the return journey.

## Example concept

A live-action woman jumps into her desktop monitor and becomes a 2D animation character. She runs through the computer, enters a network port, and travels through a physicalized data cable. She reaches another machine as high-detail pixel art. Continued transfer reduces her first to a 32x48 sprite and then to an approximately 16x24 sprite in an old computer world. She notices how little detail remains, panics, runs backward through the network, restores every visual state, and returns to reality. One small accessory remains pixelated as the final joke.

## Reusability

Replace the example character with any adult character or original design. The method does not depend on one fixed face, costume, or art style. The reusable component is the transformation ladder, identity-invariant method, reference mapping, and timed video structure.

## Quality checklist

Before generation, verify that:

- all states depict the same character
- age and body proportions stay stable
- one strong identity marker survives all stages
- each resolution stage has meaningfully less information than the previous one
- pixel art uses hard square pixels instead of a filter-like texture
- character and background references are generated separately
- the travel path is spatially understandable
- every reference image has one explicit role in the final video prompt
- the final transformation remains understandable without captions
