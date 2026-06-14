# MP3 → Visualizer Video

Drop in an audio file, pick a style, and record a music-visualizer video — all client-side in the browser. No install, no server, no build step.

## Run it

Open `index.html` in a modern browser (Chrome or Edge recommended for best recording support).

Or, since the repo is public, serve it straight from GitHub Pages once Pages is enabled for the repo.

## Usage

1. **Drop an audio file** onto the dashed box (or click to browse). MP3, WAV, OGG, and M4A all work.
2. Choose a **visualizer style**, **color theme**, **resolution** (includes 16:9, 1:1 square, and 9:16 vertical for Reels/Shorts), and **video format** (**WebM** by default, or **MP4** for universal playback — MP4 recording needs Chrome or Edge).
   - *(Optional)* **Clip to a section** — set a **Start** and **End** to render and record only part of the track (great for shorts). Accepts `0:30` or plain seconds `30`; leave blank for the whole track. Trimmed clips download with the range in the filename (e.g. `song_30-60s.webm`). When an **End** is set, the volume fades to 0 over the last 2 seconds for a clean outro.
3. *(Optional)* Add one or more **background images** and set the **second** each appears. Each image has a **pan** slider to shift it horizontally — useful for fitting a widescreen image into a 9:16 frame without being stuck on the center crop — or an **auto →** toggle that slowly sweeps the image left-to-right across the whole time it's on screen, revealing all of it. When any are set, the visualizer shrinks into a rounded panel composited over the photo, and you can choose its **position** — a bottom bar or any of the four corners.
4. *(Optional)* Type a **song title** — it's auto-filled from the filename and drawn over the video. Pick its **position** (top/bottom, left/center), an **animation**, and a **size** — or hide it. The animation previews live on the idle canvas, so you can tune it before recording.
5. Press **▶ Preview** to see it live, or **● Record video** to capture.
6. When the track ends (or you press **■ Stop**), the video downloads automatically (`.webm` or `.mp4`, per your choice) with audio baked in.

## Song title

The title field is pre-filled from the audio filename (editable). It's rendered on top of the finished frame with a soft shadow so it stays readable over both the visualizer and any background photo. Position options: top-left (default), top-center, bottom-left, bottom-center, or hidden.

**Animation** (changes over the course of the video):

- **None** — a clean static label
- **Gradient shift** — filled with the current color theme's gradient, slowly cycling between the two colors
- **Pulsing glow** — white text whose colored bloom throbs with the bass (respects the Glow / bloom toggle)
- **Typewriter** — types the title out character by character at the start, with a blinking caret
- **Wavy letters** — letters bob along a travelling sine wave
- **Shimmer sweep** — a bright highlight repeatedly sweeps across the text
- **Beat bounce** — the whole title scales and lifts on each beat

**Size** — small / medium / large.

While nothing is playing, an animated title keeps animating on the idle canvas (driven by a gentle simulated beat) so you can preview the effect; during playback and recording the beat-reactive animations follow the actual audio. The typewriter only "types" during real playback — while idle it shows the full title.

## Background images (timed slideshow)

Add one or more images as a full-frame background. Each row in the list has an **"at … s"** field — the second at which that image becomes active — plus two ways to control horizontal framing of a too-wide image:

- a **pan** slider that fixes the image's horizontal position (left ↔ right, centered by default), and
- an **auto →** checkbox that automatically pans the image from its **left edge to its right edge** over the entire time it's on screen, so the whole image is revealed. The speed adapts to the available time: the sweep runs from the image's start time until the **next image's** start time (or, for the last image, the **end of the clip/track**). Turning **auto →** on disables that row's manual pan slider.

Pan/auto-pan only have a visible effect when the image is wider than the frame can show (e.g. a 16:9 photo in a 9:16 canvas); otherwise there's no horizontal slack to move within. As playback passes each time, the background **crossfades** (1.2 s) from the previous image to the next, so a sequence of images plays as a synced slideshow behind the music. When any image uses **auto →**, the idle canvas loops the timeline so you can preview the motion (and slideshow) before recording.

When any images are present, the visualizer renders into a smaller rounded, glowing panel placed over them (bottom bar, or bottom-left / bottom-right / top-left / top-right corner). Images are scaled to cover the whole frame, and the entire composite — photo + panel — is what gets recorded. Editing a time re-sorts the list automatically; the **✕** button removes an image. With no images, the visualizer fills the frame as before.

## Visualizer styles

- **Neon bars** — glowing spectrum bars with a fading reflection
- **Mirror bars** — bars mirrored around the center line
- **Spectrum mountains** — smooth filled spectrum with a glowing crest and reflection
- **Radial spectrum** — symmetric bars radiating from a slowly rotating, pulsing core
- **Liquid blob** — a smooth bass-reactive blob that warps with the frequencies
- **Aurora ribbons** — layered glowing waveforms with motion trails
- **Galaxy burst** — a particle system that erupts on the beat, with trails
- **Bloom rings** — concentric glowing rings that expand with the bass
- **LED meter** — discrete equalizer blocks with falling peak-hold caps
- **Kaleidoscope** — radial spectrum mirrored into 8 rotating wedges, with trails
- **DNA helix** — two glowing strands with rungs, twisting and pulsing with the beat
- **Spiral** — dots on a rotating spiral, sized by frequency, with trails
### Fantasy ✨

A set of magic-themed styles, grouped separately in the style picker:

- **Enchanted** — a glowing arcane rune-circle (counter-rotating rings with frequency-reactive ticks and a bright core orb), rising magical motes that drift and flicker, and star sparkles that twinkle on the highs
- **Fairy dust** — a swirling, twinkling cloud of glowing motes orbiting a soft core, with star sparkles mixed in
- **Crystal orb** — a slowly rotating faceted gem whose facets stretch with the spectrum, lit by inner facet lines and a bright glint
- **Phoenix flames** — a rising plume of fiery motes (white-hot at the base, cooling toward the tips) that flares with the beat over a glowing ember
- **Aurora veil** — hanging shimmering curtains of light that sway with the spectrum, under a sky of twinkling stars
- **Summoning circle** — a rotating arcane ring of radial spectrum ticks with a counter-spinning pentagram and a pulsing core
- **Enchanted bars** — a fantasy take on *Neon bars*: gem-tipped, white-hot glowing columns with a soft reflection and rising sparkle motes
- **Enchanted mirror** — a fantasy take on *Mirror bars*: glowing spires mirrored across a shimmering surface line, with twinkles
- **Mystic peaks** — a fantasy take on *Spectrum mountains*: a glowing ridge under a glowing moon, with fireflies drifting above it
- **Arcane bloom** — a fantasy take on *Radial spectrum*: the spectrum drawn as a rotating two-layer flower/mandala of petals around a glowing core

A **Glow / bloom** toggle adds shadow-based bloom to every style (prettier, but heavier — turn it off if recording stutters).

A **Shuffle styles every ~10s** toggle auto-switches to a random (different) style **and color theme** every 8–13 seconds, so a single recording cycles through the visualizers and palettes. Turning it on disables the manual style picker and reveals a **Randomize from** selector — choose **All styles**, **Fantasy only ✨**, or **Non-fantasy only** to control which pool the shuffle draws from.

## How it works

- The Web Audio API decodes the file and an `AnalyserNode` provides frequency/time-domain data each frame.
- The visualizer is drawn to a `<canvas>`.
- `canvas.captureStream()` (video) is mixed with a `MediaStreamAudioDestinationNode` (audio) into one `MediaStream`, which `MediaRecorder` writes to a `.webm`.

## Known tradeoffs

- **Real-time recording**: a 3-minute song takes ~3 minutes to capture and plays aloud during recording. Keep the tab focused — backgrounded tabs throttle the canvas. This is a browser limitation.
- **Output format**: choose **WebM** (VP9/VP8 + Opus — plays in Chrome, Edge, Firefox, and VLC, and uploads fine to YouTube) or **MP4** (H.264 + AAC — plays natively everywhere, including Safari/iOS and most editors). MP4 is recorded directly by `MediaRecorder`, which only **Chrome and Edge** support; in other browsers the MP4 option automatically falls back to WebM and tells you so. (No `ffmpeg.wasm` transcode step is involved.)
