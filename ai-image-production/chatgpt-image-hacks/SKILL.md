---
name: chatgpt-image-hacks
description: Production hacks, power-user tricks, and prompting patterns for ChatGPT image generation (gpt-image-2). Use when a user wants better ChatGPT image results, says "image hack," "ChatGPT image tip," "fix my image output," or asks for advanced help with text rendering, photorealism, product shots, character consistency, edits, style anchors, composition, or output optimization. Use chatgpt-image-2-prompting for basic prompt structure; use this skill for advanced hacks only.
---

# ChatGPT Image Hacks

Use precise production language to strengthen prompts while preserving the user's intent. Add only details that solve the stated problem; avoid adjective-heavy prose.

## Prompt Architecture

- Use short labelled lines or numbered lists for scenes with four or more elements: `HEADLINE`, `SUBJECT`, `BACKGROUND`, then `CONSTRAINTS`.
- Put the foreground and primary subject before the background. Group all non-negotiable constraints at the end.
- Use one precise descriptor instead of stacked praise words. For a grounded quality lift, use `Render as if photographed on a film set with professional lighting.`

## Text and Typography

- Quote every required string and label its role: headline, subhead, callout, caption, or legal text.
- State `no extra words`, `no duplicate text`, and `no lorem ipsum` when text must be exact.
- Specify case and treatment: `ALL CAPS`, `single line`, `hand-lettered`, `printed`, `neon sign`, `embossed`, `stamped`, or `vector-clean text`.
- For small type use `legible at 2K, not decorative`; name the required language and script.

## Lighting, Color, and Photorealism

- Use hex or PANTONE values for brand-critical color, for example `brand red: #E63946`.
- Choose a lighting setup: Rembrandt, butterfly, split, or Kino Flo. Use cues such as `warm key, cool fill`, `practical lighting only`, or `no HDR look`.
- State time, weather, and purpose: `1:47 pm, overcast December light`; `flat lighting for product`; or `dramatic lighting for editorial`.
- For a real-photo feel, selectively add camera, lens, aperture, slight edge distortion, ISO grain, no retouching or skin smoothing, and controlled motion blur.
- Prefer `editorial photography, not advertising` or `documentary photography` to reduce stock-photo polish.

## Style and Composition

- Use one dominant style anchor: a specific era, art movement, publication, photographer, or director's visual language. Do not stack incompatible anchors.
- Make composition measurable: `subject in left third, action directed right, negative space right third`; `Dutch angle, 12 degrees clockwise`; or `camera at knee height`.
- Choose standard shot vocabulary: wide establishing, medium, close-up, extreme close-up, or over-the-shoulder.
- Reserve text space explicitly: `leave 20% blank in the upper-right for text overlay`. State `bleed to edge` or `centered with white border`.

## Product and Character Details

- Use commercial terms where relevant: hero shot, lifestyle shot, flat lay, packshot, ghost mannequin, or white infinity cove.
- State surface, lens, shadows, and output need; for example `macro lens, f/8, focus-stacked result, no chromatic aberration` or `transparent background`.
- List product-label text exactly and specify hierarchy.
- For people, anchor apparent age, expression micro-detail, hands, footwear, clothing, camera relationship, and activity. Use `caught mid-movement` for a natural action.
- For character consistency, list all fixed features once at the top, then describe only what changes.

## Editing Existing Images

Use this exact structure:

```
Change: [the one exact element to alter]
Preserve: [face, pose, lighting, layout, text, geometry, and other locked features]
Constraints: [no new objects, no color drift, no extra text, no watermark]
```

- Quote both old and replacement text for typography edits.
- For multi-image edits, label inputs by role: `Image 1: base scene. Image 2: jacket reference.`
- Use bounded changes such as `zoom out 20%` or `change only the jacket color to [X]`.

## Output Controls

- Always state aspect ratio: `16:9`, `portrait 4:5`, or `21:9 letterbox`.
- Request `10% safe zones on all sides` when cropping or text placement matters.
- Use low quality for iteration and high quality only for final assets.
- For print, request `high resolution, optimized for print at 300 dpi`.
- Avoid contradictory instructions such as `photorealistic 3D render` and oversized targets beyond 2560×1440 when consistency matters.

## Quick Formulas

New image:

```
[Scene / environment] → [Subject + action] → [Key details] →
[Lighting] → [One style anchor] → [Camera] → [Constraints]
```

Edit:

```
Change: [X only]
Preserve: [everything else, listed]
Constraints: [no drift, no extra text, no watermark]
```

Before returning a prompt, remove generic superlatives, resolve conflicting styles, specify visible hands, feet, and important background objects, and ensure literal text and locked elements are explicit.
