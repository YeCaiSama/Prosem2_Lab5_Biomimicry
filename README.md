# Little Bird

A camera-controlled, Flappy Bird-inspired game using the local Teachable Machine image model in `tm-my-image-model/`.

## Run locally

1. Open this folder in VS Code and install the Live Server extension if needed.
2. Right-click `index.html` and choose **Open with Live Server** (or select **Go Live**).
3. Use the `http://localhost:...` address, then select **Enable camera** and allow camera access.

The TensorFlow.js and Teachable Machine libraries load from jsDelivr, so an internet connection is required. The model files are included locally. Camera access is restricted by browsers to localhost or HTTPS.

## Interaction

- **Fly** provides repeated wingbeats and moves the bird forward while recognized; **Default** stops horizontal movement and lets the bird descend. Gestures are the only game controls.
- Land on the ground or a lower pipe to rest. The world stays fixed; the camera follows only when the bird moves past 38% of the screen width. It stops immediately when forward movement stops. Pipes are solid: a side collision holds your position while you fly into the opening. There is no death, teleport, or automatic restart.
- Pass a pipe to score. **Reset** starts a fresh map; enabling/disabling the camera preserves your game.
- The right panel displays the mirrored camera, both class probabilities, and the active control class. Recognition uses smoothing, a 62% entry threshold, a 42% hold threshold, and 220 ms of tolerance for brief dropouts. Stale predictions stop controlling the bird after 600 ms.
- The game uses a fixed physics step, a camera that follows the bird, and generous pipe gaps. On narrow screens the camera panel moves below the game.

The minimal grayscale pixel art is drawn directly on canvas. Wingbeats provide lift; gravity brings the bird back to a safe resting surface. Camera frames are processed in the browser.

## Quick check

Enable the camera and show Fly to take off and advance. Switch to Default while airborne: horizontal movement and the camera should stop while the bird lands. Show Fly again to continue. Keyboard, mouse, and touch do not move the bird. Fly into a pipe side, then climb into its opening; land on a lower pipe and take off again. The score only increases once per passed pipe. Check the Fly and Default bars with your actual poses, and use **Turn off camera** to release the camera.

## Publish to GitHub

Create a GitHub repository, then connect this folder to it and push the `main` branch:

```sh
git init
git add index.html README.md tm-my-image-model
git commit -m "Create camera-controlled Little Bird game"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

Replace the remote URL with the repository you create. The model weights are included in this project, so no hosted model URL is needed.
