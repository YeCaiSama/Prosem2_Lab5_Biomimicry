# Little Bird

A camera-controlled, Flappy Bird-inspired game using the local Teachable Machine image model in `tm-my-image-model/`.

## Run locally

1. Open this folder in VS Code and install the Live Server extension if needed.
2. Right-click `index.html` and choose **Open with Live Server** (or select **Go Live**).
3. Use the `http://localhost:...` address, then select **Start camera & play** and allow camera access.

The TensorFlow.js and Teachable Machine libraries load from jsDelivr, so an internet connection is required. The model files are included locally. Camera access is restricted by browsers to localhost or HTTPS.

## Interaction

- **Fly** at 78% confidence or higher triggers a wingbeat-like lift every 560 ms while the pose remains recognized.
- **Default** is no control; gravity makes the bird descend.
- Pass between leafy branches and collect golden seeds to score.

The interaction borrows from bird flight: wingbeats provide lift, while a bird that stops flapping glides and gradually descends.

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
