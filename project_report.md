# Investigating Failure Cases of AI-Based Driver Gaze Prediction in Complex Driving Scenes

## 1. Introduction

Driver gaze prediction is important for driver-monitoring and assistance systems. However, average performance metrics can hide serious failures in visually difficult or safety-critical scenes.

This project investigates when AI-predicted visual attention fails to align with human driver gaze. We compare AI attention maps with human gaze maps and analyze performance across driving conditions.

## 2. Research question

How does AI-human gaze alignment change across normal driving, low-light conditions, and blurred images?

## 3. Method

We build a controlled synthetic evaluation pipeline containing normal, low-light, and blurred driving frames.

For each frame, we generate:

- A human gaze heatmap.
- An AI attention heatmap.
- Image-quality measurements: brightness, sharpness, and contrast.

We compute five alignment metrics:

- AUC-Judd
- Shuffled AUC
- NSS
- CC
- SIM

We also compute a composite failure score:

\[
failure\_score = 1 - mean(CC, SIM, AUC	ext{-}Judd, Shuffled\ AUC)
\]

Higher failure scores indicate poorer alignment between AI attention and human gaze.

## 4. Results

The condition-wise results are stored in `results/metrics/condition_summary.csv`.

The expected pattern is:

1. Normal frames achieve the strongest AI-human gaze alignment.
2. Low-light frames show reduced alignment because visual evidence becomes weaker.
3. Blurred frames show reduced alignment because fine-grained scene structure is lost.
4. The robustness-gap analysis quantifies the performance drop relative to normal driving.

## 5. Failure-case analysis

Frames are ranked using the composite failure score. For each condition, we automatically select the worst-aligned and best-aligned cases.

The failure gallery compares:

- The driving frame.
- The human gaze heatmap.
- The AI attention heatmap.

This allows qualitative inspection of systematic errors, such as excessive center bias, overly broad attention, or failure to focus on the same road region as the driver.

## 6. Limitations

The current experiments use synthetic frames and simulated AI attention maps. Therefore, the results validate the evaluation methodology rather than establish conclusions about a specific deployed driver-gaze model.

The next stage should use real driving datasets, human gaze annotations, and pretrained model predictions.

## 7. Future work

- Evaluate DR(eye)VE and BDD-A.
- Use SCOUT extended annotations for intersections, weather, time of day, and image-quality metadata.
- Compare multiple pretrained saliency and driver-attention models.
- Add dense-traffic and intersection conditions.
- Analyze center bias and vanishing-point bias.
- Extend to object-level gaze prediction.

## 8. Conclusion

This project provides a reproducible failure-oriented evaluation framework for AI-based driver gaze prediction. It demonstrates a complete pipeline for measuring AI-human gaze alignment, detecting condition-specific degradation, and visualizing failure cases.
