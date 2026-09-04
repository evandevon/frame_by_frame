# frame_by_frame

Stop motion animator — https://evandevon.github.io/frame_by_frame/

A browser-based stop motion animation tool built for classroom use.

No installation required — open the page and start shooting. Must be served over HTTPS to work correctly. Opening directly from the filesystem (`file://`) will prevent camera switching, audio library access, and export features from working. Use GitHub Pages or any web server.

## Features

### Camera

- Live camera preview with adjustable onion skinning (back and forward frames, adjustable opacity)
- Capture frames from any connected webcam or USB camera
- Switch between cameras using the Cycle button or the camera dropdown
- Resolution selection: SD (640×480) / HD (1280×720) / Full HD (1920×1080) / 2K (2560×1440) / 4K (3840×2160) / Native
- Actual delivered resolution displayed in real time — amber if the camera negotiated a different resolution than requested
- Flip and rotate the camera view
- Manual focus or autofocus on supported webcams (via ImageCapture API)
- Exposure controls on supported cameras
- Denoise over multiple frames to reduce image noise

### Frames

- Capture with the on-screen button or the Space key or a user-selected hotkey
- Frames appear in the filmstrip at the bottom, with a coloured marker showing which background each one uses
- Scrub, reorder (long-press drag), duplicate, and delete frames
- Select multiple frames using checkboxes; bulk move, duplicate, or delete
- Keyboard navigation: ← → to step through frames, Home/End to jump, Del to delete
- Uploading or pasting an image in as a frame automatically caps it at 4K on the long edge — keeps a huge phone photo from making the whole project sluggish, while leaving anything already smaller untouched

### Reference layers

- Add posing-guide images or short image sequences over the live camera view, without affecting the actual captured photo
- Multiple reference layers at once, each colour-coded
- Move, resize, rotate, flip; toggle visibility
- Useful for lining up a pose against a previous shot, a storyboard sketch, or a real-world reference

### Inking

- Draw on frames with a pen tool (adjustable colour, opacity, and size)
- Ink is stored as a separate layer and does not alter the original photo
- Eraser tool
- Spray can tool with texture sampling — sample a region of the frame and spray its texture onto other areas; adjustable size, flow, softness, and mode (Dot or Even)
- Smudge tool — drags pixels along the ink layer; adjustable reach, blur, and soften
- **Time-Clone Pen** — paints pixels sampled from the same spot on the frame immediately before or after this one, rather than a fixed colour. Handy for painting out something that only shows up in one single frame, or blending motion between two frames. Adjustable size and edge softness; two optional toggles (off by default) let a stroke also pull in that neighbouring frame's own ink/paint or its own overlays, not just what the camera photographed
- Clear for the ink layer

### Overlays

- Add transparent PNG overlays to frames (logos, props, titles, characters)
- Upload an image file, paste one from the clipboard, or capture one live from the webcam — a small, movable, resizable picture-in-picture viewfinder sits right in the main preview (so it can be compared against whatever else is already on screen) and lands the resulting overlay at exactly the size and position it was left at
- Upload an animated GIF or video to spread it across frames as an overlay sequence — one overlay per frame, starting at the current frame; resizing or moving the sequence's first frame offers to sync that same size/position across the rest of the sequence in one step
- 8 resize handles (all four corners, all four edges) — freely squish/stretch by default in whatever direction is dragged
  - Hold **Shift** while dragging any handle to lock the aspect ratio instead
  - Hold **Ctrl** (or **Cmd**) while dragging any handle to crop instead of resize — trims which part of the source image is visible rather than stretching it
- Drag to reposition; rotate with the handle above the overlay
- Flip horizontally or vertically with dedicated buttons
- Bring forward / send backward to control overlay stacking order
- Opacity, brightness, and contrast sliders, plus a drop-shadow toggle, per overlay
- Overlay eraser: paint to erase or restore edges of an overlay (adjustable size and softness)
- Magic Background Erase: click a point on an overlay to flood-fill erase similar-coloured surrounding pixels
- Dotted bounding box shown when an overlay is active
- Copy a single overlay to the next frame or to all frames; copy all overlays on a frame to the next frame or to all frames
- Copy/paste an overlay via the system clipboard, or an in-app buffer as a fallback
- Cut-out tool: draw a freehand lasso or polygon selection on a frame, then cut it out as a moveable overlay
- Full touch support on every tool and handle above, not just mouse

### Masking

- Requires a background — grab one from the camera, upload one, paste one from the clipboard, or use Transparent mode
- **Background gallery**: keep multiple backgrounds in a project, not just one. Grabbing, uploading, or pasting a new one adds it to the gallery and makes it the default for newly captured frames; previously-used backgrounds stay available to preview, set as default, or apply to a selected range of frames — useful for multi-scene projects where the physical backdrop changes partway through
- Manual erase/restore brush with adjustable size and softness
- Rectangle, polygon, freehand erase tool — make a shape to erase or keep a region
- **Magic Foreground Erase**: click a spot on the frame's own photo and every connected, similarly-coloured pixel touching it gets erased from the mask automatically — the masking equivalent of an overlay's Magic Background Erase
- **Copy Mask / Paste Mask**: copy the current frame's mask and paste it onto another frame, for scenes where several frames share the same cutout
- Undo and redo for mask strokes, folded into the same undo system as everything else
- View mask mode — shows the raw black-and-white mask for inspection
- Reset mask for the current frame; Clear all masks across all frames
- Chroma keying with the following controls:
  - Key colour picker with RGB or HSV matching mode
  - Tolerance and Softness (feather)
  - Pedestal — lifts semi-transparent grey areas toward fully opaque
  - Choke — shrinks the matte edge inward to remove colour fringing
  - Spill suppression strength — reduces key-colour bleed on subject edges
  - Replace or Add-to mode — choose whether chroma key replaces the existing manual mask or multiplies with it
  - Apply to current frame (live preview on slider change) or Apply to all frames
- Difference keying with the following controls:
  - Using the camera to take a "clean plate" frame for comparison, or uploading one
  - Threshold, Softness, Choke, Clean, Contrast
  - Apply to current frame (live preview on slider change) or Apply to all frames

### Audio

- Multi-track audio timeline alongside the frame filmstrip, synced to the same clock as frame playback
- Record directly from the microphone, or upload audio files
- Trim, split, move, and adjust the volume of individual clips; waveform shown for every clip
- **Scrub-to-hear**: dragging the playhead across the timeline plays a short live snippet of whatever's under it, like scratching a record — makes it far faster to find exactly where a word or sound falls
- **A/B loop**: draggable in/out markers, defaulting to the whole timeline, with a highlighted range between them. Looping between those markers is the default playback behaviour, not a separate toggle — press Play and it loops until you stop it or narrow the range
- **Snap to frame**: a checkbox that snaps clip edges and the playhead to exact frame boundaries rather than landing between them
- Duplicate or delete the frame currently shown in the audio editor's own preview, without leaving the audio panel to do it
- Undo covers every audio action — recording, trimming, splitting, moving, volume, adding/removing tracks, muting — all folded into the same undo system as frames and overlays
- **Shared audio library**: a `🎵 Library` panel that auto-discovers a shared collection of sounds from an `audio-library/` folder in this repo — no manual list to maintain, folder names become categories automatically. Categories are collapsed by default and only fetch their sounds once expanded, each shown with a small waveform preview
- **My Uploads**: anything already brought into the current project (recorded or uploaded) is reusable from the same Library panel, with its own delete option
- Preview any sound before adding it — a separate player, independent of the project's own playback
- Mute individual tracks; the currently active track is clearly highlighted
- Whichever frame you last looked at in the audio editor's own preview is what's shown in the main window when you close the audio panel

### Journal & documentation tools

- **Contact sheet**: a printable summary for design/production journals — composited frames, overlay gallery, background gallery, audio timeline snapshot, and full session history, opened as a print-ready page
- **Session log**: automatically tracks captures, reshoots, deletions, overlay/reference-layer additions, audio actions, and exports as they happen, surfaced in the contact sheet
- **Save as Tutorial**: package the current project as a shareable tutorial — title, description, optional video link, a looping preview GIF, and attachment files (worksheets, reference sheets) — bundled into the `.smz` itself, so anyone who opens the file sees the tutorial popup automatically, however they received it

### Playback

- Play/Stop with adjustable FPS; pausing stays on the frame you were viewing rather than jumping to the live camera
- First/Last/Previous/Next frame buttons and keyboard equivalents
- Play just the currently selected frames

### Export

- MP4 (H.264 via MediaRecorder; falls back to WebM if H.264 is unsupported)
- Animated GIF (capped at 480px wide to keep file size reasonable)
- Image sequence — every frame exported as a JPEG inside a ZIP file
- Configurable export FPS
- Option to export selected frames only
- Option to burn frame numbers into the export
- Deflicker option
- Bitrate scales automatically with FPS to maintain consistent per-frame quality

### Save / Load

- Save and load projects as `.smz` files (a ZIP containing all frames, ink layers, masks, backgrounds, overlay assets, reference layers, and audio)
- Project name stamped into the filename with date and time
- Project automatically saves a backup to IndexedDB and offers to recover it on reload after an unexpected close
- A single, unified undo/redo system covers frames, ink, masks, overlays, reference layers, backgrounds, and audio together

### Other

- Brightness and contrast adjustment per frame (non-destructive) — see also the per-overlay version under Overlays
- Memory usage display with per-category breakdown
- Works on desktop and mobile browsers, with full touch support throughout

## How to use

### Getting started

1. Open the app in Chrome (recommended) or another modern browser, served over HTTPS.
2. Allow camera access when prompted.
3. Position your subject in front of the camera.

### Capturing frames

- Click Capture (or press Space) to take a shot.
- The frame appears in the filmstrip at the bottom.
- Use the FPS control to set onion skin and playback speed.
- Use onion skinning (back and forward) to see ghost frames over the preview — useful for planning movement between shots.

### Reviewing and editing frames

- Click any frame in the filmstrip to review it.
- Open the Inking panel to draw on a frame, spray texture, smudge, or paint in pixels from the frame before or after it with the Time-Clone Pen.
- Open the Overlay panel to add PNG props or characters — upload a file, paste one, or capture one live from the webcam — adjust their position, size, rotation, flip, brightness, or contrast, or erase their edges.
- Open the Masking panel to remove the background using manual brush work, rectangle erase, Magic Foreground Erase, or chroma key, and to manage the background gallery.
- Open the Audio panel to record, upload, or pull sounds from the shared library onto the timeline — scrub the ruler to hear exactly where a sound falls, and use the loop markers to repeat a section while you line things up.

### Camera settings

- Use the camera dropdown or the 🔄 Cycle button to switch between connected cameras.
- If the camera supports focus control, an Autofocus tickbox appears. Unticking it reveals a manual focus slider.
- Use the Resolution dropdown to change capture quality. The Actual display shows what the camera delivered — amber means the camera negotiated a different resolution than requested (common when another tab is using the camera, or the requested resolution is unsupported).
- Use Flip H, Flip V, and Rotate to adjust the camera orientation.

### Playback

- Press Play to preview your animation.
- Press Stop to return to the live view.
- Press the yellow Play button to only play the currently selected frames.

### Saving your work

- Click Save to download a `.smz` project file (just a renamed `.zip`) containing everything in the project.
- Click Load to reopen a saved project.
- Use Save as Tutorial instead of a regular save to package the project with a title, description, video link, and attachments for sharing.

### Exporting

Click Export and choose a format:

- **MP4** — broad compatibility (falls back to WebM if H.264 is unsupported in the browser)
- **GIF** — animated, capped at 480px wide
- **Image Sequence** — every frame as a JPEG inside a ZIP file, for use in other editing software

## Known limitations

- Camera cycling requires at least two cameras connected and recognised by the browser.
- If the Actual resolution is stuck at a lower value, check whether another tab or application is using the same camera — the browser shares the existing stream and cannot renegotiate a higher resolution while it is in use.
- On managed school devices, camera access may be restricted by IT policy.
- The app must be served over HTTPS; `file://` will not allow camera access, the audio library, or export to work correctly.
- The shared audio library requires an internet connection and being hosted on GitHub Pages (or a manually configured equivalent) — it fails gracefully and stays out of the way if unavailable, but sounds already in a project keep working offline regardless.

## Future features

- Ink/overlay layer ordering control — right now ink always sits on top of overlays; a per-overlay "bring above ink" toggle is the leading idea, possibly alongside a simpler whole-project swap for the common case
- Asset library of reusable overlays (beyond the current per-project copy/paste)
- Text overlay tool
- Flipbook PDF export
- Framing guide overlays (rule of thirds, grid, perspective)
