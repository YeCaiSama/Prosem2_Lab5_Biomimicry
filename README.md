# Little Bird

A gesture-controlled flying game built with Teachable Machine and TensorFlow.js for **Lab 5: Machine Learning + Biomimicry**.

Little Bird combines the pipe obstacles of Flappy Bird with a relaxed, no-death interaction. Its minimal grayscale pixel art takes inspiration from Chrome’s dinosaur game. Show the model your **Fly** gesture to move forward and gain lift; return to **Default** to stop moving forward and settle onto the ground or a pipe. Take your time—there is no game over.

## How to play

1. Open the website and click **Enable camera**.
2. Allow camera access and position yourself in the preview.
3. Show the gesture associated with the model’s **Fly** class to take off and move forward. Hold it for repeated wingbeats.
4. Return to **Default** to stop horizontal movement and let gravity bring the bird down.
5. Navigate through the pipe openings. Each fully passed pipe adds one point.

The ground and lower pipe tops are safe places to rest. Colliding with a pipe blocks movement without killing or resetting the bird. The map does not scroll automatically: the view follows the bird only after it moves far enough across the screen.

Gestures are the only movement controls. **Reset** starts a fresh map and clears the score. **Turn off camera** stops recognition without resetting your progress.

## Run locally

No build step or package installation is needed.

### With VS Code

1. Open this project folder in VS Code.
2. Install the **Live Server** extension if needed.
3. Right-click `index.html` and select **Open with Live Server**.
4. Open the localhost address shown by Live Server.

### With Python 3

From the project folder, run:

```sh
python3 -m http.server 8765 --bind 127.0.0.1
```

Then open [Little Bird locally](http://127.0.0.1:8765/).

Use a browser with webcam support and allow camera access. Serve the project through localhost or HTTPS rather than opening the HTML file directly. An internet connection is needed to load the TensorFlow.js and Teachable Machine libraries from jsDelivr; the trained model is included in this repository.

## Machine learning interaction

The included Teachable Machine image model recognizes two classes:

| Class | Game response |
| --- | --- |
| `Fly` | Repeated wingbeats and forward movement |
| `Default` | No forward movement; gravity brings the bird down |

The left panel contains the game. The right panel shows the mirrored webcam preview, both class confidence values, and the active control class. On smaller screens, the camera panel appears below the game.

To accommodate imperfect recognition, the game smooths Fly predictions, uses a 62% threshold to activate and a 42% threshold to sustain the gesture, and allows 220 ms of tolerance for brief recognition dropouts. Predictions older than 600 ms cannot control the bird. These settings are defined in `index.html`.

Camera frames are processed locally in the browser by the model. The application does not record or upload them.

## Biomimicry and feedback

The interaction borrows from bird flight: wingbeats provide lift, while gravity brings the bird down between wingbeats. A recognized Fly gesture becomes a virtual wingbeat. This is a simplified interaction inspired by flight rather than a physical simulation.

The feedback loop is:

```text
Player gesture → Webcam → Model prediction → Bird movement
      ↑                                           ↓
      └──── Player watches and adjusts gesture ────┘
```

The confidence bars help the player understand what the model sees. Safe landings allow the player to pause, adjust their position, and try again without losing progress.

## Project files

```text
index.html                         Page, pixel art, game logic, and model integration
tm-my-image-model/
  model.json                      Exported model architecture
  weights.bin                     Trained model weights
  metadata.json                   Class labels and model metadata
README.md                          Project description and setup
lab-5-machine-learning-and-biomimicry.md
                                   Assignment instructions
```

## Deployment

Deploy this folder as a static website. Keep `tm-my-image-model/` alongside `index.html` so the relative model paths continue to work. Enable HTTPS on the public site for camera access.

For the lab’s Dokploy workflow, select the **Static** build type and use the directory containing `index.html` as the site root.

## Troubleshooting

- **Camera blocked:** allow camera access in your browser’s site settings, then retry.
- **Camera unavailable:** connect a webcam and close other applications using it.
- **Model fails to load:** check your internet connection and confirm all three model files are present.
- **Gesture does not trigger reliably:** check the preview and confidence bars, improve lighting, and match the gesture used to train the Fly class. Recognition depends on the model’s training examples.
