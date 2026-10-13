# GazeFail: Driver Gaze Failure Analysis

**When does AI-predicted visual attention fail to align with human driver gaze in complex driving scenes?**

This project presents a reproducible failure-case analysis pipeline for AI-based driver gaze prediction. Instead of reporting only average saliency scores, it evaluates alignment between AI attention and human gaze across driving conditions and automatically identifies worst-case failures.

## Research question

> On which driving conditions and scene types do AI-predicted visual attention maps disagree most with human driver gaze?

## Method

The pipeline:

1. Loads or generates driving frames.
2. Creates human gaze heatmaps.
3. Produces AI attention heatmaps.
4. Computes saliency-alignment metrics:
   - AUC-Judd
   - Shuffled AUC
   - Normalized Scanpath Saliency (NSS)
   - Correlation Coefficient (CC)
   - Similarity (SIM)
5. Assigns frames to failure conditions:
   - Normal
   - Low light / night
   - Blur
6. Computes condition-wise performance and robustness gaps.
7. Ranks frames by a composite failure score.
8. Generates visual failure galleries comparing human gaze and AI attention.

## Current status

The repository currently uses a controlled synthetic driving dataset to validate the full evaluation pipeline.

The next extension is to replace synthetic frames and AI maps with:
- Real frames from DR(eye)VE or BDD-A
- Human gaze ground truth
- Predictions from a pretrained driver-attention or saliency model

## Results

See:

- `results/metrics/condition_summary.csv`
- `results/metrics/robustness_gap.csv`
- `results/metrics/failure_analysis_with_scores.csv`
- `results/metrics/failure_case_summary.csv`
- `results/figures/condition_performance.png`
- `results/figures/failure_gallery.png`

## Repository structure

```text
.
├── driver_gaze_failure_analysis.ipynb
├── README.md
├── requirements.txt
├── data/
├── results/
│   ├── metrics/
│   ├── figures/
│   └── failure_cases/
└── report/
```

## Future work

- Evaluate real DR(eye)VE and BDD-A frames.
- Use SCOUT extended annotations for intersection, weather, and quality metadata.
- Compare multiple pretrained saliency and driver-attention models.
- Add dense-traffic and intersection conditions.
- Analyze center bias and vanishing-point bias.
- Extend the analysis to object-level gaze prediction.

## Intended contribution

This project provides a failure-oriented evaluation framework for driver-gaze prediction. Its goal is not only to measure average alignment, but to identify the conditions under which AI attention becomes unreliable.
