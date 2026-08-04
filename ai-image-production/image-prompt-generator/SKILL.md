---
name: image-prompt-generator
description: Turn a creative brief into clear, production-ready prompts for AI image generation. Use for concept art, editorial images, product shots, social posts, thumbnails, or visual assets when the user needs a prompt rather than an image.
---

# Image Prompt Generator

Create one strong, usable image prompt from the brief. Prioritize observable details and production choices over vague praise words.

## Discover the Brief

Identify the intended use, audience, aspect ratio, subject, mood, and any non-negotiable brand or text requirements. If a detail is missing but low-risk, choose a sensible default and state it briefly.

## Build the Prompt

Use this order:

```
[medium and visual approach] of [primary subject + action],
in [environment], [composition and camera],
[lighting], [palette and materials], [important details],
[output constraints]
```

- State the main subject before the setting.
- Use one coherent visual approach; do not combine incompatible styles.
- Make composition concrete: camera height, shot size, direction of movement, and placement in frame.
- Name a lighting setup and a palette with an intended effect.
- Specify aspect ratio, text-safe space, and exclusions when they matter.

## Production Defaults

- For editorial work: favour natural texture, believable light, and a specific moment of action.
- For product work: name the surface, lighting, camera angle, and whether the background is seamless or contextual.
- For educational visuals: keep the central concept legible at a glance and remove decorative clutter.
- For social assets: reserve the required copy area and protect a 10% safe margin.

## Output

Return:

1. A ready-to-paste prompt.
2. A short `Avoid:` line only when it prevents likely failure, such as extra text, watermarking, distorted hands, or clutter.
3. One optional variation only if it meaningfully changes composition or visual direction.

## Quality Check

Before finalizing, confirm the prompt has a single focal subject, a feasible scene, unambiguous framing, a deliberate light source, and no conflicting visual instructions.
