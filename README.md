# GazeFail: Driver Gaze Failure Analysis

**When does AI-predicted visual attention fail to align with human driver gaze in complex driving scenes?**

This project presents a reproducible failure-case analysis pipeline for AI-based driver gaze prediction. Instead of reporting only average saliency scores, it evaluates AI-human gaze alignment across driving conditions and automatically identifies worst-case failures.

## Research question

> On which driving conditions and scene types do AI-predicted visual attention maps disagree most with human driver gaze?

## Method

The pipeline:

1. Loads or generates driving frames.
2. Creates human gaze heatmaps.
3. Produces AI attention heatmaps.
4. Computes AUC-Judd, shuffled AUC, NSS, CC, and SIM.
5. Assigns frames to normal, low-light, or blur conditions.
6. Computes condition-wise performance and robustness gaps.
7. Ranks frames by a composite failure score.
8. Generates visual failure galleries.

## Current status

The repository currently uses a controlled synthetic driving dataset to validate the complete evaluation pipeline.

The next extension is to use real DR(eye)VE or BDD-A frames, human gaze annotations, and predictions from a pretrained driver-attention model.

## Key outputs

- `results/metrics/condition_summary.csv`
- `results/metrics/robustness_gap.csv`
- `results/metrics/failure_case_summary.csv`
- `results/figures/condition_performance.png`
- `results/figures/failure_gallery.png`

## Future work

- Evaluate real DR(eye)VE and BDD-A data.
- Use SCOUT extended annotations for intersections, weather, and image-quality metadata.
- Compare multiple pretrained saliency and driver-attention models.
- Add dense-traffic and intersection conditions.
- Analyze center bias and vanishing-point bias.
