# thought-pull
Thought Pull — Telepathy gaze-controlled node demo (X357-AI)

# Thought Pull

**Move objects with your attention alone. No touch, no voice.**

Thought Pull is a gaze-controlled interface demo from **X357-AI**. Six nodes orbit a central ring. Fix your eyes on one and it's pulled inward, its ring brightening as the system locks onto your attention. When it reaches the centre, the core lights up and the phone pulses.

▶ **Live demo:** https://x357ai.github.io/thought-pull/thought_pull.html
(Best in Chrome on Android. Allow the camera when asked.)

---

## How to use it

1. Hold the phone upright at reading distance, with your face lit from the front.
2. Tap **Start** once. That's the only tap.
3. **Calibration (~20 s):** look at each dot as it appears. Four check dots then measure your tracking accuracy, shown as `±N px`.
4. **Play:** stare at the node with the **dashed ring** (the target). Keep your head still and move only your eyes. Pull it into the centre.

### Options
| Option | What it does |
|---|---|
| Marked target | Scores your hit rate against chance (1 in 6 ≈ 17%) |
| Squeeze to collapse | Experimental: a sharp squeeze, detected by the motion sensor, collapses the locked node instantly |
| Show gaze dot | Displays where the system thinks you're looking |
| Show camera | Small preview of the front camera |

---

## How it works

- **Eye tracking:** the front camera feeds Google's MediaPipe Face Landmarker, which finds 478 face points, including the centre of each iris.
- **Gaze features:** each iris's position between the eye corners, plus head orientation.
- **Calibration:** a 9-point ridge regression maps those features to screen coordinates, then a 4-point check measures the actual error.
- **Smoothing:** a One-Euro filter (Casiez, Roussel & Vogel, CHI 2012) steadies the cursor without lag.
- **Selection by direction:** phone-camera gaze is coarse, so instead of requiring a pinpoint hit, the app picks the node in the direction you're looking from the centre. The lock stays on while your eyes follow the node inward.

**Honest note:** the "mind-reading" feel comes entirely from camera-based eye tracking. The marked-target hit rate is the measurable test of control.

---

## Privacy
All processing happens on your phone. No video or images are uploaded or stored.

## Session log
Menu → **Copy log** exports a CSV of every calibration (accuracy in px) and trial (target, hit or miss, time to centre, method) for lab records.

---

## Credits
- **MediaPipe Face Landmarker**, Google (Apache 2.0): https://developers.google.com/mediapipe
- **One-Euro filter:** G. Casiez, N. Roussel, D. Vogel, "1€ Filter: A Simple Speed-based Low-pass Filter for Noisy Input in Interactive Systems," CHI 2012.

## Author
**Barry Lee Guevremont**, X357-AI LLC, Goldsboro, North Carolina
