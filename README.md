# frame_by_frame
**Stop motion animator**
https://evandevon.github.io/frame_by_frame/

- A browser-based stop motion animation tool built for classroom use.
- No installation required — open the page and start shooting.
- Must be served over HTTPS to work correctly. Open directly from the filesystem (file://) and camera switching and export features will not work. Use GitHub Pages or any web server.

**Features**

- Live camera preview with onion skinning (see the previous frame through your current shot)

- Capture frames from any connected webcam or USB camera

- Switch between cameras using the Cycle button or the camera dropdown

- Adjust resolution (SD / HD / FHD / Native)

- Flip and rotate the camera view

- Manual foucs or autofucs on supported webcams

- Draw on frames with a pen tool (adjustable colour and size)
  
- Add PNG overlays to frames (logos, props, titles)
  
- Copy overlays across frames
  
- Scrub, reorder, duplicate, and delete frames
  
- Playback at adjustable frame rates
  
- Export as WebM video, MP4, or image sequence (ZIP)
  
- Save and load projects as .fbf files
  
- Works on desktop and mobile browsers


**How to use
Getting started**

- Open the app in Chrome (recommended) or another modern browser served over HTTPS.
- Allow camera access when prompted.
- Position your subject in front of the camera.

**Capturing frames**

-Click Capture (or press Space) to take a shot.
-The frame appears in the filmstrip at the bottom.
-Adjust the FPS slider to control onion skin and playback speed.
-Toggle Onion to see a ghost of the previous frame over the live view — useful for planning movement between shots.

**Reviewing and editing frames**

-Click any frame in the filmstrip to review it.
-Use the Draw tool to sketch on a frame (ink is stored separately and won't affect the original photo).
-Use Add PNG to place a transparent PNG overlay onto a frame.
-Use Copy Overlay → Next or Copy Overlay → All to carry overlays across frames.

**Camera settings**

-Use the camera dropdown or the 🔄 Cycle button to switch between connected cameras.
-If the camera has focus control an 'autofocus' tickbox appears. If unticked, a focus slider appears.
-Use the resolution dropdown to change capture quality.
-Use Flip H, Flip V, and Rotate to adjust the camera orientation.

**Playback**

-Press Play to preview your animation in the filmstrip.
-Press Stop to return to the live view.

**Saving your work**

Click Save to download a .fbf project file. This saves all frames and drawings.
Click Load to reopen a saved project.

**Exporting**

**Click Export and choose a format:**

-WebM — good for sharing online
-MP4 — broad compatibility (falls back to WebM if H.264 is unsupported)
-Image Sequence — exports every frame as a JPEG inside a ZIP file, for use in other editing software




**Recommended setup**

-Browser: Chrome (desktop), served over HTTPS
-Camera: Any USB webcam. Sony cameras with Imaging Edge Webcam installed should also appear as a camera option.
-Deployment: GitHub Pages, or any static web host



**Known limitations**

-Projects can really blow out the ram needed to run, especially with inkings and png overlays. 
-GIF export is temporarily disabled.
-Camera cycling requires at least two cameras to be connected and recognised by the browser.
-On managed school devices, camera access may be restricted by IT policy.
