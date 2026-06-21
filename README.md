# Task-Oriented Quality Assessment for Intention Recognition in Distorted 3D Avatar Streaming

## 📌 Overview
This repository contains the official dataset and multimodal stimuli for our paper *Task-Oriented Quality Assessment for Intention Recognition in Distorted 3D Avatar Streaming*. We introduce a comprehensive behavioral dataset aimed at investigating how streaming-induced visual distortions affect human intention recognition in 3D avatars. 

This repository provides image fragments, video stimuli, and complete subjective behavioral judgment logs.

## Contents

```
IQS-Avatar-Dataset/
├── stimuli/
│   ├── images/    10 actions × 13 conditions (PNG)
│   └── videos/    10 actions × 15 conditions (MP4, ~3-5s)
└── metadata/
    ├── iqs_ground_truth.csv    135 fragment-level aggregated scores
    └── trial_responses.csv    2,688 trial-level responses
```

## 📊 Data Descriptions

### 1. Metadata 
#### `iqs_ground_truth.csv`
Fragment-level aggregated scores. These are the benchmark targets used for metric correlation analysis.

- `Content_ID`: Base avatar/action ID (E1–E10).
- `Distortion_ID`: Applied distortion type.
- `ground_truth`: Correct intention label for the action.
- `mean_IQS`: Average Intent Quality Score across observers.
- `accuracy`: Proportion of correct intention recognitions.
- `mean_confidence`: Average observer confidence.
- `mean_MOS`: Average subjective visual quality rating.
- `n_responses`: Number of observer responses aggregated for this fragment.

#### `trial_responses.csv`
Trial-level behavioral responses. Researchers can map identifiers directly to file paths in the `stimuli/` folder.

- `Subject_ID`: Anonymized participant identifier.
- `Content_ID`: Base avatar/action ID (same as above).
- `Distortion_ID`: Applied distortion type (same as above).
- `Q1_Response`: The forced-choice intention recognition response from the observer.
- `Q2_Confidence`: Self-reported confidence level (0, 25, 50, 75, 100).
- `Q3_MOS`: Perceived visual quality score on a continuous 1–5 scale.

### 2. Stimuli Mapping
Depending on your benchmarking paradigm (IQA or VQA), you can map the rows in the CSV file to the physical files using the following conventions:

- **For Video-Based VQA Benchmarking:**
  `stimuli/videos/{Content_ID}/{Distortion_ID}.mp4`

- **For Image-Based IQA Benchmarking:**
  `stimuli/images/{Content_ID}/{Distortion_ID}.png`
  *(Note: Image-based evaluation excludes temporal conditions such as LFR_10 and LFR_15)*

## Intent Quality Score (IQS)

```
IQS = acc × (conf / 100) − (1 − acc) × (conf / 100) × 0.5
```

- `acc`: 1 if Q1_Response matches ground truth, 0 otherwise
- `conf`: Q2_Confidence value
- Range: [−0.5, +1.0]

## 📄 License
This dataset is licensed under the Creative Commons Attribution 4.0 International (CC BY 4.0) License.