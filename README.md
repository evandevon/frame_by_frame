# frame_by_frame
**Stop motion animator**
https://evandevon.github.io/frame_by_frame/

- A browser-based stop motion animation tool built for classroom use.
- No installation required — open the page and start shooting.
- Must be served over HTTPS to work correctly. Opening directly from the filesystem (file://) will prevent camera switching and export features from working. Use GitHub Pages or any web server.

---

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

### Frames
- Capture with the on-screen button or the Space key or user selected hotkeys
- Frames appear in the filmstrip at the bottom
- Scrub, reorder (long-press drag), duplicate, and delete frames
- Select multiple frames using checkboxes; bulk move, duplicate, or delete
- Keyboard navigation: ← → to step through frames, Home/End to jump, Del to delete

### Inking
- Draw on frames with a pen tool (adjustable colour, opacity, and size)
- Ink is stored as a separate layer and does not alter the original photo
- Eraser tool
- Spray can tool with texture sampling — sample a region of the frame and spray its texture onto other areas; adjustable size, flow, softness, and mode (Dot or Even)
- Smudge tool — drags pixels along the ink layer; adjustable reach, blur, and soften
- Undo (up to 10 steps) and Clear for the ink layer
- Ctrl+Z routes to the relevant undo (ink or mask) depending on the active tool

### Overlays
- Add transparent PNG overlays to frames (logos, props, titles, characters)
- Drag to reposition; corner handle to resize proportionally; midpoint handles to resize width or height independently
- Rotate with the handle above the overlay
- Flip horizontally or vertically with dedicated buttons
- Bring forward / send backward to control overlay stacking order
- Overlay eraser: paint to erase or restore edges of an overlay (adjustable size and softness)
- Dotted bounding box shown when an overlay is active
- Copy a single overlay to the next frame or to all frames
- Copy all overlays on a frame to the next frame or to all frames
- Paste overlay from a buffer
- Cut-out tool: draw a freehand lasso or polygon selection on a frame, then cut it out as a moveable overlay

### Masking
- Requires a clean plate (background image grabbed from the camera or uploaded)
- Manual erase/restore brush with adjustable size and softness
- Rectangle erase tool — drag to erase a rectangular region; Invert toggle erases everything outside the rectangle instead
- Undo and redo for mask strokes
- View mask mode — shows the raw black-and-white mask for inspection
- Reset mask for the current frame; Clear all masks across all frames
- Chroma key with the following controls:
  - Key colour picker with RGB or HSV matching mode
  - Tolerance and Softness (feather)
  - Pedestal — lifts semi-transparent grey areas toward fully opaque
  - Choke — shrinks the matte edge inward to remove colour fringing
  - Spill suppression strength — reduces key-colour bleed on subject edges
  - Replace or Add-to mode — choose whether chroma key replaces the existing manual mask or multiplies with it
  - Apply to current frame (live preview on slider change) or Apply to all frames

### Playback
- Play/Stop with adjustable FPS
- First/Last/Previous/Next frame buttons and keyboard equivalents

### Export
- MP4 (H.264 via MediaRecorder; falls back to WebM if H.264 is unsupported)
- Image sequence — every frame exported as a JPEG inside a ZIP file
- Configurable export FPS
- Option to export selected frames only
- Option to burn frame numbers into the export
- Deflicker option
- Bitrate scales automatically with FPS to maintain consistent per-frame quality
- GIF export — temporarily disabled

### Save / Load
- Save and load projects as .smz files (a ZIP containing all frames, ink layers, masks, and overlay assets)
- Project name stamped into the filename with date and time

### Other
- Brightness and contrast adjustment per frame (non-destructive)
- Memory usage display with per-category breakdown
- Works on desktop and mobile browsers

---

## How to use

### Getting started
1. Open the app in Chrome (recommended) or another modern browser, served over HTTPS.
2. Allow camera access when prompted.
3. Position your subject in front of the camera.

### Capturing frames
- Click **Capture** (or press **Space**) to take a shot.
- The frame appears in the filmstrip at the bottom.
- Use the **FPS** control to set onion skin and playback speed.
- Use **Onion skinning** (back and forward) to see ghost frames over the preview — useful for planning movement between shots.

### Reviewing and editing frames
- Click any frame in the filmstrip to review it.
- Open the **Inking** panel to draw on a frame, spray texture, or smudge.
- Open the **Overlay** panel to add PNG props or characters, adjust their position, size, rotation, and flip, or erase their edges.
- Open the **Masking** panel to remove the background using manual brush work, rectangle erase, or chroma key.

### Camera settings
- Use the camera dropdown or the 🔄 Cycle button to switch between connected cameras.
- If the camera supports focus control, an **Autofocus** tickbox appears. Unticking it reveals a manual focus slider.
- Use the **Resolution** dropdown to change capture quality. The **Actual** display shows what the camera delivered — amber means the camera negotiated a different resolution than requested (common when another tab is using the camera, or the requested resolution is unsupported).
- Use **Flip H**, **Flip V**, and **Rotate** to adjust the camera orientation.

### Playback
- Press **Play** to preview your animation.
- Press **Stop** to return to the live view.

### Saving your work
- Click **Save** to download a `.smz` project file (just a renamed .zip) containing all frames, ink, masks, and overlays.
- Click **Load** to reopen a saved project.

### Exporting
Click **Export** and choose a format:
- **MP4** — broad compatibility (falls back to WebM if H.264 is unsupported in the browser)
- **Image Sequence** — every frame as a JPEG inside a ZIP file, for use in other editing software
- **GIF** — not yet implemented

---

## Known limitations
- GIF export is temporarily disabled.
- Camera cycling requires at least two cameras connected and recognised by the browser.
- If the Actual resolution is stuck at a lower value, check whether another tab or application is using the same camera — the browser shares the existing stream and cannot renegotiate a higher resolution while it is in use.
- On managed school devices, camera access may be restricted by IT policy.
- The app must be served over HTTPS; file:// will not allow camera access or export to work correctly.

---

## Future features
- Audio tracks for music and sound effects
- Asset library of reusable overlays
- Text overlay tool
- Video import
