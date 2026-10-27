# Handy Bird

A gesture-controlled flying game built with Teachable Machine and TensorFlow.js for **Lab 5: Machine Learning + Biomimicry**.

Handy Bird combines the pipe obstacles of Flappy Bird with a relaxed, no-death interaction. Show the model **Fly** gesture to move forward and gain lift; return to **Default** to stop moving forward and settle onto the ground or a pipe. Take your time—there is no game over.

## How to play

1. Open the website and click **Enable camera**.
2. Allow camera access and position yourself in the preview.
3. Show the gesture associated with the model’s **Fly** class to take off and move forward. Hold it for repeated wingbeats.
4. Return to **Default** to stop horizontal movement and let gravity bring the bird down.
5. Navigate through the pipe openings. Each fully passed pipe adds one point.

The ground and lower pipe tops are safe places to rest. Colliding with a pipe blocks movement without killing or resetting the bird. The map does not scroll automatically: the view follows the bird only after it moves far enough across the screen.

Gestures are the only movement controls. **Reset** starts a fresh map and clears the score. **Turn off camera** stops recognition without resetting your progress.

## Machine learning interaction

The included Teachable Machine image model recognizes two classes:

| Class | Game response |
| --- | --- |
| `Fly` | Repeated wingbeats and forward movement |
| `Default` | No forward movement; gravity brings the bird down |

The left panel contains the game. The right panel shows the mirrored webcam preview, both class confidence values, and the active control class. On smaller screens, the camera panel appears below the game.
