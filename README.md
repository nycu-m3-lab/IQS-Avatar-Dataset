# Task-Oriented Quality Assessment for Intention Recognition in Distorted 3D Avatar Streaming

## 📌 Overview
This repository contains the official dataset and multimodal stimuli for our paper *Task-Oriented Quality Assessment for Intention Recognition in Distorted 3D Avatar Streaming*. We introduce a comprehensive behavioral dataset aimed at investigating how streaming-induced visual distortions affect human intention recognition in 3D avatars. 

This repository provides image fragments, video stimuli, and complete subjective behavioral judgment logs.

## Contents

```
R3DAI_Dataset/
├── stimuli/
│   ├── images/    10 actions × 13 conditions (PNG)
│   └── videos/    10 actions × 15 conditions (MP4, ~3-5s)
└── metadata/
    └── trial_responses.csv    2,688 trial-level responses
```

## 📊 Data Descriptions

### 1. Metadata Fields (`data/trial_responses.csv`)
The column fields in the behavioral dataset are defined below. Researchers can map these identifiers directly to the file paths in the `stimuli/` folder.

- `Subject_ID`: Anonymized participant identifier.
- `Content_ID`: Base avatar/action ID.
- `Distortion_ID`: Applied distortion type.
- `Q1_Response`: The forced-choice intention recognition response from the observer.
- `Q2_Confidence`: Self-reported user confidence level (0, 25, 50, 75, 100).
- `Q3_MOS`: Perceived visual quality score on a continuous 1–5 scale.

### 2. Stimuli Mapping
Depending on your benchmarking paradigm (IQA or VQA), you can map the rows in the CSV file to the physical files using the following conventions:

- **For Video-Based VQA Benchmarking:**
  $$\text{File Path} = \texttt{stimuli/videos/}\{\texttt{Content\_ID}\}/\{\texttt{Distortion\_ID}\}.\texttt{mp4}$$

- **For Image-Based IQA Benchmarking:**
  $$\text{File Path} = \texttt{stimuli/images/}\{\texttt{Content\_ID}\}/\{\texttt{Distortion\_ID}\}.\texttt{png}$$
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