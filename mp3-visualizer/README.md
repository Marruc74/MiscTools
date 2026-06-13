# MP3 → Visualizer Video

Drop in an audio file, pick a style, and record a music-visualizer video — all client-side in the browser. No install, no server, no build step.

## Run it

Open `index.html` in a modern browser (Chrome or Edge recommended for best recording support).

Or, since the repo is public, serve it straight from GitHub Pages once Pages is enabled for the repo.

## Usage

1. **Drop an audio file** onto the dashed box (or click to browse). MP3, WAV, OGG, and M4A all work.
2. Choose a **visualizer style**, **color theme**, and **resolution** (includes 16:9, 1:1 square, and 9:16 vertical for Reels/Shorts).
3. Press **▶ Preview** to see it live, or **● Record video** to capture.
4. When the track ends (or you press **■ Stop**), the video downloads automatically as a `.webm` with audio baked in.

## Visualizer styles

- **Frequency bars** — classic spectrum bars
- **Mirror bars** — bars mirrored around the center line
- **Radial spectrum** — bars radiating from a pulsing core
- **Waveform** — time-domain oscilloscope line
- **Pulse rings** — concentric rings that expand with the bass

## How it works

- The Web Audio API decodes the file and an `AnalyserNode` provides frequency/time-domain data each frame.
- The visualizer is drawn to a `<canvas>`.
- `canvas.captureStream()` (video) is mixed with a `MediaStreamAudioDestinationNode` (audio) into one `MediaStream`, which `MediaRecorder` writes to a `.webm`.

## Known tradeoffs

- **Real-time recording**: a 3-minute song takes ~3 minutes to capture and plays aloud during recording. Keep the tab focused — backgrounded tabs throttle the canvas. This is a browser limitation.
- **Output format is `.webm`** (VP9/VP8 + Opus). It plays in Chrome, Edge, Firefox, and VLC, and uploads fine to YouTube. True MP4 export would require ffmpeg or `ffmpeg.wasm`.
