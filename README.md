# Rainbow Sea Editor

A self-contained browser editor for Apeiron's luminous rainbow sea. Open `index.html` directly or publish it with GitHub Pages. No build tools, server, API keys, or network requests are required by the editor.

## Create a scene

Choose horizontal, vertical, or joining currents. Adjust flow width, speed, softness, color, and shear. Each tributary has its own speed. Ships sail through the junction with moving wakes and soft waterline masking.

Enable **Edit flow paths** to drag the control points. The shared endpoints of joining currents move together. Disable guides for an uncluttered preview; guides are never included in image exports.

Pause and scrub the timeline to find a frame. Scrubbing rebuilds the regenerative ocean from its initial state, so restoring the same scene settings, dimensions, and time reproduces the same frame in the same browser. Scenes run for up to ten minutes; restart to begin again. Rebuilding later moments can take a few seconds.

## Use your own ships

Under **Ships**, use **Choose image** separately for Ship 1 and Ship 2. PNG, WebP, and JPEG are supported; transparent PNG or WebP images blend best with the sea. Flip an image horizontally if its bow points left, and adjust **Waterline from top** to set how much of the hull is submerged. A larger percentage shows more of the ship. **Use galleon** restores the original artwork for that ship.

Images are processed in your browser, capped at 1024 pixels on the longest side, and stored with their transparency. Uploads can be up to 15 MB and 32 megapixels. Custom artwork is embedded in presets, JSON scene files, and standalone HTML exports; it is not uploaded to the repository or a server. If browser storage fills up, save the scene as a JSON file instead. Older scene files still load with the default galleons.

## Save and export

- **Export image** downloads a PNG at the selected resolution.
- **Save preset** stores settings and time in this browser on this device.
- **Save settings / Load settings** transfers a scene as a JSON file.
- **Download animation** creates a self-contained HTML animation with the current scene and embedded ship image.

Browser presets are specific to the website origin and device. Use JSON scene files for portable backups. Colors and antialiasing can vary slightly between browser implementations. This is a stylized visual approximation of currents and shear, not a physical fluid solver.

## GitHub Pages setup

For a public repository, go to **Settings → Pages**. Select **Deploy from a branch**, choose **main**, select **/(root)**, and save. GitHub will build the site from `index.html`; later commits to `main` update it automatically.

Expected project URL after Pages deployment:

https://BartelbyScribbler.github.io/Rainbow.Sea.editor/

This URL is only live after Pages is enabled and the deployment completes. Private repository Pages availability depends on the GitHub account plan. Making the repository public also makes its code and embedded ship image public.

## Implementation

The editor uses the Canvas 2D API, cubic Bezier current paths, time-driven surface motion, a fixed-step regenerative background, and local alpha masks for hull immersion. Scene files use a versioned JSON format with validated numeric bounds. Galleon artwork was generated with OpenAI's built-in image generation tool and is embedded as a transparent WebP image.

The rendering, editor UI, and embedded artwork are in `index.html`, which can be edited without a build step. No external libraries are loaded at runtime.

