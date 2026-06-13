# MP3 → Visualizer Video

Drop in an audio file, pick a style, and record a music-visualizer video — all client-side in the browser. No install, no server, no build step.

## Run it

Open `index.html` in a modern browser (Chrome or Edge recommended for best recording support).

Or, since the repo is public, serve it straight from GitHub Pages once Pages is enabled for the repo.

## Usage

1. **Drop an audio file** onto the dashed box (or click to browse). MP3, WAV, OGG, and M4A all work.
2. Choose a **visualizer style**, **color theme**, and **resolution** (includes 16:9, 1:1 square, and 9:16 vertical for Reels/Shorts).
3. *(Optional)* Add a **background image**. When set, the visualizer shrinks into a rounded panel composited over the photo, and you can choose its **position** — a bottom bar or any of the four corners.
4. Press **▶ Preview** to see it live, or **● Record video** to capture.
5. When the track ends (or you press **■ Stop**), the video downloads automatically as a `.webm` with audio baked in.

## Background image

Add any image as a full-frame background. The visualizer then renders into a smaller rounded, glowing panel placed over it (bottom bar, or bottom-left / bottom-right / top-left / top-right corner). The image is scaled to cover the whole frame, and the entire composite — photo + panel — is what gets recorded. Remove the image to return to the full-screen visualizer.

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

A **Glow / bloom** toggle adds shadow-based bloom to every style (prettier, but heavier — turn it off if recording stutters).

A **Shuffle styles every ~10s** toggle auto-switches to a random (different) style **and color theme** every 8–13 seconds, so a single recording cycles through the visualizers and palettes. Turning it on disables the manual style picker.

## How it works

- The Web Audio API decodes the file and an `AnalyserNode` provides frequency/time-domain data each frame.
- The visualizer is drawn to a `<canvas>`.
- `canvas.captureStream()` (video) is mixed with a `MediaStreamAudioDestinationNode` (audio) into one `MediaStream`, which `MediaRecorder` writes to a `.webm`.

## Known tradeoffs

- **Real-time recording**: a 3-minute song takes ~3 minutes to capture and plays aloud during recording. Keep the tab focused — backgrounded tabs throttle the canvas. This is a browser limitation.
- **Output format is `.webm`** (VP9/VP8 + Opus). It plays in Chrome, Edge, Firefox, and VLC, and uploads fine to YouTube. True MP4 export would require ffmpeg or `ffmpeg.wasm`.
