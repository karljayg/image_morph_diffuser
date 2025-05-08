# image_morph_diffuser
turns any image into a 3D cloud of particles, then lets you form, expand, dissipate, or even morph between two images.

🚀 Summary
This tool turns any image into a 3D cloud of particles, then lets you form, expand, dissipate, or even morph between two images. It uses an off-screen HTML5 canvas to sample pixels, Three.js to render them as colored points, and Anime.js to animate transitions.

🛠 Tech Stack
HTML5 Canvas – down-samples the image to your chosen resolution, reads RGBA pixel data.

Three.js – WebGL renderer, buffer geometry for millions of points, OrbitControls for 3D navigation.

Anime.js – tweening library to interpolate positions, colors, and opacities during animations.

Vanilla JS – UI wiring, FileReader for uploads, DOM sliders/buttons.

⚙️ How It Works
Upload your primary (and optional secondary) image.

Down-sample it to at most ~300 000 pixels (or your slider-defined max) while preserving aspect ratio.

Sample every n<sup>th</sup> pixel (density slider) and skip transparent ones.

Clamp to 300 000 particles total for performance.

Build a THREE.Points cloud where each vertex’s position and color come from that pixel.

Animate between “states” (form, expand, dissipate, morph) by tweening each point’s 3D coordinates—and color if enabled.

👇 Usage
Primary Image

Click “Upload Primary Image” and pick a photo.

It auto-processes, fits the camera, and shows the Form Image state.

Secondary Image (optional)

Click “Upload Second Image” to prepare for morphing.

Once processed, the “Morph to Second Image” button unlocks.

Navigate the 3D cloud by dragging or zooming with your mouse.

Animate with the buttons:

Form Image – snaps back to the original pixel layout.

Expand Cloud – pushes particles outward along random vectors.

Dissipate Particles – pushes and fades them out.

Morph to Second Image – transitions each point into the second image’s layout/colors.

Morph Back to First Image – reverses that morph.

🔧 Controls & Settings
1. Image Uploads
Upload Primary Image: loads and processes your starting image.

Upload Second Image: loads a target for morphing.

2. Animation Buttons
Form Image: form the current base image.

Expand Cloud: push particles outwards.

Dissipate Particles: push + fade out for a vanishing effect.

Morph to Second Image: tween into the second-image layout (only enabled after you load it).

Morph Back to First Image: returns to the original layout (only enabled after a successful morph).

3. Particle Appearance
Particle Size (1–20): radius in world units. Smaller → more dot-like; larger → glossier blobs.

Particle Color (Tint): used when Use Image Colors is off.

Use Image Colors: checkbox to switch between tinted uniform color vs. the sampled pixel colors.

4. Resolution & Density
Image Detail (Max Pixels): caps the longer side of the down-sampled canvas when Particle Density > 1. Higher allows more detail but costs performance.

Particle Density (1–20): sample every n<sup>th</sup> pixel.

1 = every pixel → maximum fidelity.

>1 = sparser sampling → fewer particles for the same canvas size.

5. Animation Parameters
Expansion Factor (10–500): how far points fly out in the Expand Cloud state (and also used in Morph as a springy intermediate).

Dissipation Factor (100–2000): how far + fast they fly/fade in Dissipate Particles.

Animation Speed (500–5000 ms): global duration for any transition.

💡 Tips & Best Practices
Balance fidelity vs. performance:

If your GPU/CPU stutters, either lower Image Detail or bump Particle Density above 1.

Matching image sizes: for the smoothest morphs, pick two photos with similar aspect ratios.

Avoid huge canvases: most browsers clamp off-screen canvas to ~8 000–16 000 px per side.

Use density sparingly: sampling every pixel at 300 k points is great for detail, but taxing—try density = 2 for ~75 k points.

Experiment with speed: faster morphs (<1 s) look snappier; slower (>2 s) feel more organic.

OrbitControls: drag to rotate, scroll to zoom; hold right-click or two-finger drag to pan.
