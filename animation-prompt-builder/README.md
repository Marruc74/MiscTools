# AI Animation Prompt Builder

Fill out one reusable template and get a paste-ready story prompt in any of the **20 prompt structures** from the *100 AI Animation Story Prompts* pack — plus the **Master Generator**. Pick a structure, fill the fields, copy, paste into Claude / ChatGPT / Gemini. Entirely client-side, no build step.

## Run it

Open `index.html` in any modern browser. (Or serve it via GitHub Pages once Pages is enabled for the repo.)

## How it works

The pack's 100 prompts are really one set of building blocks — **locked characters, a story goal, a dialogue map, scene-by-scene text-to-image + image-to-video prompts, and a closing moral** — wrapped in 20 different *structures* (Classic Numbered, Section Headers, Screenplay, XML, JSON, Pixar Story Spine, Three-Act, and so on). This tool keeps the building blocks in a form and swaps the wrapper.

1. **Story** — title, genre, moral theme, and an optional one- or two-line story goal (leave it blank to let the AI invent the premise).
2. **Locked characters** — add 2–4 characters. Each row is a name plus its *visual lock* (the `"3D cartoon girl, 122cm, auburn hair…"` string). These get rendered as `LOCKED [Name]` and the standard "expand each into a 3–4 paragraph character sheet" instruction is added automatically.
3. **Format** — choose one of the 21 structures (a one-line explainer shows what each is good for), and tune scene count, dialogue-line count, runtime, aspect ratio, audience, and style anchor.
4. **Copy / Download** — the assembled prompt updates live on the right. Copy it to the clipboard or download it as a `.txt`.

Click **Load example** to populate the form with the pack's "The Secret of Ember Falls" cast and see a complete prompt, then edit from there. Or hit **🎲 Surprise me** to generate a fresh, coherent story every time — a themed title, moral, story goal, a random structure, and 2–3 locked characters with full visual locks that match the chosen genre. Keep clicking until something sparks, then fine-tune.

### Randomize one section at a time

If most of the story is right but one piece isn't, re-roll just that piece — the rest stays put. There's a small **🎲** next to **Title**, **Moral theme**, and **Story goal**, and one on each **character** row. The per-character dice keeps that character's kind (a person stays a person, a companion stays a companion) and a person's gender, and fits the current genre — so you can keep spinning a single cast member until they click while everyone else stays locked.

Characters span any age: the main character is usually a child or teen, with a small chance of an adult or elderly lead, and supporting cast can be any age. Age drives height, the description ("boy" → "young woman" → "elderly man"), hair, and naming.

## Structures included

Master Generator (one-line idea), then: Classic Numbered · Section Headers · Screenplay · Role-Play · Constraint-First · Chain-of-Thought · JSON-Style · Storyboard Panels · XML Tags (Claude-optimized) · Few-Shot Examples · Question-Driven · Bullet Minimalist · Cinematic Brief · Pixar Story Spine · Three-Act · Reverse Engineering · Multi-Turn Chained · Character POV Locked · Visual-First · Director's Commentary.

## Notes

- Your draft is saved in `localStorage`, so a refresh keeps your work. **Clear** resets the story fields.
- The Master Generator ignores the character rows on purpose — it asks the AI to invent the cast from your one-line idea.
- Output is plain text; nothing leaves your browser.
