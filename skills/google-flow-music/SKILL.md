# Best Practices for Google Flow Music

Flow Music is Google's AI music studio. It runs on Lyria 3 and Lyria 3 Pro. The same models power custom music in Google Vids, audio generation in the Gemini app, and the Lyria APIs on Vertex AI and Google AI Studio. The prompting principles below apply across all of those surfaces, with Flow-specific features called out where they matter.

The job of this skill is to help generate prompts that produce usable music on the first or second try, and to diagnose what to change when they don't.

## What Flow Music actually does

Before writing any prompt, know which capability fits the task.

- **Generate**: full track from a prompt. Up to three minutes on Lyria 3 Pro, thirty seconds on Lyria 3.
- **Chat with Producer**: conversational interface. Treat it like a session musician, not a search box. Multi-turn requests refine the same idea instead of re-rolling.
- **Replace**: swap out a specific section (verse, chorus, bridge) without regenerating the whole track. Use when 90% of the song is right.
- **Extend**: add length to an existing track. Use when the ending lands wrong or the song needs an outro.
- **Veo handoff**: send a generated track into Veo for a matched music video. Same model stack means tighter sync than mixing third-party tools.
- **YouTube Shorts export**: direct path from a Flow track into Shorts with no DMCA risk on the AI-generated audio.

If the user is using Lyria via API rather than Flow, the surface differs but the prompt language is identical. Note the limits: 30 seconds on Lyria 3, three minutes on Lyria 3 Pro.

## Prompt anatomy (not a template)

Every effective Flow Music prompt covers six things. The order does not matter. Treat this as a checklist for what the prompt contains, not a sentence skeleton to fill in.

- **Genre and era**: not just "rock" but "late-70s arena rock" or "early-2010s trap." Era anchors production style.
- **Mood**: emotional intent. "Defiant," "lovestruck," "uneasy," "triumphant." Avoid generic "upbeat" or "sad."
- **Instrumentation**: the three or four instruments that carry the track. Be specific: "Rhodes electric piano," not "keyboard."
- **Tempo and groove**: BPM range and feel. "Mid-tempo, 95 BPM, behind the beat" beats "medium speed."
- **Vocal direction**: gender, range, texture, language, delivery style. Or "instrumental" if no vocals.
- **Lyrics**: either a theme to write from, or exact lyrics in quotes for the model to perform.

A minimum viable prompt covers all six in two sentences. A maximum-control prompt fills out each axis with sensory detail.

**Minimum viable:**

> Mid-tempo dream pop, melancholic and washed-out, shoegaze guitars and reverbed snare, around 90 BPM, female alto vocal singing in English about driving home in the rain.

**Maximum control:**

> A late-80s dream pop track in the vein of the Cocteau Twins, melancholic and washed out with a sense of slow-motion drifting. Layered chorused electric guitars with heavy plate reverb, a Yamaha DX7 pad, and a gated reverb snare at 88 BPM. The bass sits low and round, the drums brush past you. Female alto vocal, breathy and reverbed, sung in English, syllables stretched. The lyric is a quiet narration of driving home in heavy rain after an argument, ending on the line "the road keeps going."

Both work. The first is fast. The second gets closer to a specific reference without naming an artist.

## Genre and era: the cheat codes

Era is the lever beginners miss. The same genre sounds different in different decades because production, instruments, and mix conventions change. Use these shorthand cues to anchor a period:

- **1950s**: mono mix, plate reverb on vocals, brushed kit, upright bass, tape saturation, "live in the room" feel.
- **1960s**: Hammond B3, fuzz guitar, vocal harmonies tight on the centre, four-piece arrangement.
- **1970s**: warm tape compression, wide stereo, Wurlitzer, Rhodes, strings doubling the melody, real drums.
- **1980s**: gated reverb on the snare, DX7 bell pads, programmed drums, synth bass, big chorus on guitar.
- **1990s**: grungy distortion or sample-based hip-hop, lo-fi tape hiss revival, four-track aesthetic.
- **2000s**: maximalist pop production, sidechain compression appearing, polished digital sheen.
- **2010s trap**: 808 slides, triplet hi-hat rolls, sparse arrangement, vocal triplet flow.
- **2020s hyperpop**: pitched-up vocals, distorted everything, aggressive sidechain, intentional clipping.

Pair a genre with an era for tighter results: "early 90s alternative rock" gets Pixies-adjacent, "mid 2010s alternative rock" gets The 1975-adjacent.

## Vocal direction

Lyria's vocal control is the area most prompts under-specify. Cover four axes when vocals matter:

- **Demographics and range**: male tenor, female alto, child soprano. Be explicit. "Singer" defaults to a generic delivery.
- **Texture**: breathy, raspy, smooth, nasal, gritty, airy, polished, untrained. Texture is what makes a voice feel like a voice.
- **Delivery**: legato, staccato, rapped, half-sung, spoken-word, sung-through, talk-rap. Specify what the voice is doing physically.
- **Language**: English, German, Spanish, French, Hindi, Japanese, Korean, Portuguese. More coming. Specify even when it's English.

Layering vocals is supported. State where backing vocals enter, what they do, and who sings them.

**Example with layered vocals:**

> Male baritone lead, gravelly and weathered, sung in English. A female alto enters in the choruses with a high harmony, breathy and one octave above the lead. In the bridge, a small gospel choir hums underneath the melody.

State changes over time when you want them. "The vocal starts confident and tight, then becomes softer and more uncertain in the second verse."

## Lyric craft for sung delivery

Lyrics for a model to sing are not the same as lyrics on a page. The model will follow phrasing more reliably when the words are written for melody.

- Match syllables to musical rhythm. Six-syllable lines sing differently than ten-syllable lines. If you want a fast vocal, write tighter lines. If you want stretched syllables, leave space.
- Put stressed words on strong beats. End lines on a vowel-heavy word when possible. "Stay" sings better than "stayed."
- Use rhyme to anchor melody. End rhyme on the second and fourth lines is the most predictable structure. ABAB and AABB both work. Internal rhyme is harder for the model and often gets flattened.
- Avoid clusters of consonants. "Strapped strict scripts" will mush. "Held the line slow" sings cleanly.
- Repeated lines pay off. Choruses repeat for a reason. If you want a hook, write one and mark it in the prompt as the chorus.

If you want the model to write the lyrics, give it a tight emotional brief instead of a vague theme. "Write a lyric about realising you've outgrown your hometown, in second person, no clichés" beats "song about home."

## Tempo, rhythm, and structure

State BPM as a range when exact is not critical: "85–95 BPM." State BPM exactly when matching to video. State feel separately: "swung," "straight," "behind the beat," "on top of the beat," "loose," "tight to a click."

For Lyria 3 Pro, you can dictate structure explicitly with timed segments. This is the single most powerful feature for video scoring or for songs that need specific transitions.

**Timed structure example:**

> [00:00] Sparse intro: solo upright piano playing a slow melodic motif in a minor key. [00:15] Brushed drums and upright bass enter. The piano keeps its motif but adds harmony underneath. [00:45] Female mezzo-soprano vocal enters, smooth and conversational, singing in English. [01:30] Chorus: full band lifts in volume. Strings enter for the first time. The vocal pushes up an octave. [02:15] Bridge: drums drop out. Only piano and a single sustained string note remain. Vocal becomes a whisper. [02:40] Final chorus returns at full volume. Builds to a held final note at [03:00].

Specifying timestamps does not just sequence sections. It anchors emotional pacing. Use it whenever the music needs to land at specific moments.

## Multimodal: prompting with images, PDFs, or video

Lyria accepts up to ten reference images or a PDF as part of the prompt. The model uses them to establish emotional baseline, palette, and pacing, not to literally describe what is in them.

How to use images well:

- Pick images that share an emotional tone, not images of bands or instruments.
- Two or three images are usually enough. Ten is for storyboards where the song needs to track scene by scene.
- State in the text prompt what role the images play: "Match the mood of the attached images" or "The lyric should reflect the story in the images."
- Genre still needs to be stated in text. Images do not communicate genre reliably.

**Example image-conditioned prompt:**

> A slow, hopeful folk ballad. Acoustic guitar, dobro, and a single low harmonica. Male baritone vocal in English, weathered and warm. The lyric and emotional arc should follow the story shown in the attached three images, ending on the feeling captured in the last one.

For video scoring, pair Flow Music with Veo. Generate video first, then write a Lyria 3 Pro prompt with explicit timestamps that match the scene transitions. Because both run on the same model stack, the sync tends to be closer than scoring with external tools.

## Working in Chat with Producer

The Chat interface is not a single-prompt box. Treat it like a producer in a studio. Three patterns work consistently:

- Establish before refining. Start with a wide-shot prompt that nails the genre and mood. Then refine.
- One change at a time. "Make the vocal raspier" is a clean ask. "Make the vocal raspier and slow the tempo and add strings" muddies which change did what.
- Reference the previous take. "Keep the rhythm section from the last version but replace the lead vocal with a female alto."

Use Replace when one section is wrong and the rest is right. Use Extend when the song needs more length or a different ending. Use full regenerate sparingly. You lose all the choices the model made.

## Troubleshooting

Most failed prompts fail in predictable ways. The fix usually lives in one or two words.

| Symptom | Likely cause | Fix |
|---|---|---|
| Wrong genre | Era unspecified; genre name ambiguous | Add an era ("early 90s alternative") and a reference production style |
| Tempo too fast or slow | "Upbeat" or "slow" is vague | State BPM or BPM range explicitly |
| Vocals you didn't want | Theme described but no "instrumental" tag | Add "instrumental, no vocals" |
| Vocal delivery wrong | Demographics or texture missing | Add range, gender, texture, language |
| Lyrics mush or skip words | Bad consonant clusters, lines too long | Rewrite lyric with vowel endings and tighter syllable counts |
| Track feels generic | Prompt is a list of adjectives with no specific reference points | Add an era, an instrument by exact name, a mood beyond "happy" or "sad" |
| Structure ignored | Asked for verse-chorus-bridge in vague terms | Use timestamps with Lyria 3 Pro |
| Iteration loop stalled | Re-rolling instead of replacing | Use Replace on the broken section, keep the rest |
| Mix sounds modern when you wanted vintage | No era anchor; no production style cue | Add era and one or two period-specific production terms (plate reverb, gated snare, tape saturation) |

## Anti-patterns

The five most common prompt failures, with what they should be instead.

- **Pile of adjectives.** "Beautiful, emotional, powerful, deep, moving song about love." Replace with two specific adjectives and one concrete reference: "A tender mid-tempo love song in the production style of late-70s Fleetwood Mac."
- **Stacking too many genres.** "Country trap dream pop ambient." Pick one primary genre and at most one secondary inflection: "Country with subtle ambient pad textures underneath."
- **Naming a specific artist as the target.** Lyria avoids mimicking existing artists by design. The output will be inconsistent and often disappointing. Describe the era, instrumentation, and production style instead.
- **Generic mood words.** "Happy," "sad," "upbeat," "chill." All four describe nothing specific. Use "celebratory," "wistful," "defiant," "drowsy."
- **Treating the model like a search box.** One-shot prompts plateau fast. Switch to Chat and refine in passes.

## Quick-start: six prompts that work

Use these as starting points and modify.

1. **Indie folk, intimate:** A quiet acoustic folk ballad, fingerpicked nylon guitar and a single upright bass, recorded close-mic'd with room sound. 78 BPM. Female alto vocal in English, soft and confiding, singing about waiting for someone who isn't coming.
2. **Trap instrumental:** A modern Atlanta trap instrumental, 808 sub bass with slides, triplet hi-hat rolls, sparse synth lead. 140 BPM half-time feel. Instrumental, no vocals. Dark and patient.
3. **Cinematic orchestral, tense:** A tense orchestral cue building from silence. Tremolo strings, low brass swells, a single timpani heartbeat. Builds across 90 seconds to a sudden silence. Instrumental.
4. **Amapiano, joyful:** An amapiano track at 112 BPM. Log drum bassline, soft piano chords, shaker, vocal chops layered. Male vocal in English with light call-and-response from a female alto. Lyric about a celebration that runs all night.
5. **80s synthpop:** An 80s synthpop track in the style of mid-decade production. DX7 bells, gated reverb snare, Linn drum kit, synth bass. 118 BPM. Male tenor vocal in English, polished and slightly nasal. Lyric about driving alone at night through a neon city.
6. **Bilingual R&B duet:** A modern R&B duet at 82 BPM. Warm electric piano, finger snaps, soft kick. Male baritone vocal in English answered by a female soprano in Portuguese. Lyric about the gap between two people in two cities.

## Pairing Flow Music with other tools

- **Flow Music + Veo**: write video first, then score with Lyria 3 Pro using explicit timestamps that match scene transitions. Same model stack means tighter sync.
- **Flow Music + Gemini**: when stuck on how to describe a sound, ask Gemini to turn a creative brief into a fully-specified prompt. Gemini can also write singable lyrics if you give it a syllable target per line.
- **Flow Music + Nano Banana**: generate a storyboard or vibe-board first, then feed those images into Lyria as conditioning.
- **Flow Music + YouTube Shorts**: direct export means a creator can score short-form video end-to-end without leaving the Google stack.

## Trust and safety

All Lyria outputs include SynthID watermarking and support C2PA cryptographically signed metadata. The model is designed to avoid mimicking specific existing artists. Prompts that try to name and copy an artist will either fail or produce something unusable. Describe the era, the instrumentation, and the production style instead.
