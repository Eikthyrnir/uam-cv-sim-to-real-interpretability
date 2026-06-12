# UAM CV Project: Synthetic-to-Real Interpretability for Object Detection

## Project overview

This repository contains the code notebooks for a Computer Vision project at Adam Mickiewicz University. The project investigates synthetic-to-real transfer in object detection using the DIMO dataset, which contains real and synthetic images of industrial metal objects.

The goal is to analyze how different object detection architectures behave when trained on real data, synthetic data and mixed training regimes. The analysis combines standard detection metrics with error decomposition and interpretability methods.

The project consists of two main experimental parts:

* **Part I:** real-only architecture baseline, where multiple object detection models are compared on real DIMO data.
* **Part II:** training-data regime comparison, where selected models are trained on different real/synthetic regimes and evaluated on the same real test set.

The final analysis uses:

* mAP and mAP@50:95;
* TIDE error decomposition;
* Activation-Box Ratio;
* CAM-style visualizations;
* attention maps;
* qualitative prediction and failure-case examples.

## Repository structure

The GitHub repository is intentionally lightweight. It contains the main code notebooks and exploratory notebooks. Large result files, full output notebooks, model checkpoints, datasets and PNG artifacts are stored externally in Google Drive.

Current repository structure:

```text
.
├── README.md
├── DIMO_detection_pipeline.ipynb
├── DIMO_detection_sandbox.ipynb
├── DIMO_sandbox.ipynb
├── Part 2 of DIMO_detection_pipeline.ipynb
└── Part 2.1 of DIMO_detection_pipeline.ipynb
```

### File description

* `DIMO_detection_pipeline.ipynb`
  Main pipeline notebook. Contains the core object detection pipeline and prediction visualizations across different data modes.

* `Part 2 of DIMO_detection_pipeline.ipynb`
  Notebook used for Part II experiments related to training-data regime comparison.

* `Part 2.1 of DIMO_detection_pipeline.ipynb`
  Additional Part II notebook used for qualitative prediction and CAM visualizations.

* `DIMO_detection_sandbox.ipynb`
  Exploratory notebook used during development on a smaller custom dataset/pipeline.

* `DIMO_sandbox.ipynb`
  Early exploratory notebook for training and visualization.

The full Part I results notebook is not included in GitHub because of file size limitations. It is available in the external Google Drive artifact folder.

## Data

The project uses the **DIMO dataset**: Dataset of Industrial Metal Objects.

DIMO is suitable for this project because it provides both real and synthetic images of industrial objects. This allows us to study the synthetic-to-real transfer problem under controlled conditions.

The experiments use the following training-data regimes:

* `real_only`: training only on real images;
* `sim_all`: training on all available synthetic images;
* `sim_weak_dr`: training on weakly randomized synthetic data;
* `sim_strong_dr`: training on strongly randomized synthetic data;
* `mixed`: training on a 50/50 mixture of real and synthetic data.

All models are evaluated on the same real test set.

## External artifacts

Large files are stored outside GitHub in the Google Drive artifact folder.

**Google Drive artifact folder:**
https://drive.google.com/drive/folders/1EKI4q7UQEtDs2j9fvrbT6Uw4jPJuD17M?usp=sharing 

The Drive folder contains:

* prepared DIMO subsets;
* full Part I results notebook;
* full Part I and Part II result figures;
* PNG plots used in the report;
* CAM and attention visualizations;
* qualitative prediction examples;
* qualitative error examples;
* model checkpoints;
* large experiment snapshots;
* additional artifacts that are too large for GitHub.

This separation is intentional. GitHub contains the code notebooks and project documentation, while Google Drive contains the heavy reproducibility artifacts.

## How to run

The notebooks were designed to be run in Google Colab or another Jupyter-compatible environment.

### 1. Clone the repository

```bash
git clone [TODO: paste repository URL]
cd [TODO: repository folder name]
```

### 2. Open the notebooks

Open the relevant notebook in Google Colab or Jupyter.

Recommended order:

1. `DIMO_detection_pipeline.ipynb`
2. `Part 2 of DIMO_detection_pipeline.ipynb`
3. `Part 2.1 of DIMO_detection_pipeline.ipynb`

The full Part I results notebook should be opened from the Google Drive artifact folder because it is too large for GitHub.

### 3. Mount Google Drive

If using Google Colab, mount Google Drive inside the notebook:

```python
from google.colab import drive
drive.mount('/content/drive')
```

Then update the paths in the notebook so they point to the external artifact folder.

### 4. Restore data and checkpoints

Use the prepared DIMO subset and model checkpoints from the Google Drive artifact folder.

Alternatively, if rebuilding the project from scratch, run the dataset preparation cells to construct the training regimes:

* `real_only`
* `sim_all`
* `sim_weak_dr`
* `sim_strong_dr`
* `mixed`

### 5. Run Part I

Part I is the real-only architecture baseline.

Because the full Part I output notebook is too large for GitHub, it is stored in the Google Drive artifact folder. Use that notebook or the stored artifacts to inspect the full Part I results.

Part I evaluates a broad set of object detection models on real-only DIMO data. The purpose is to analyze architecture-level differences before introducing synthetic-data regimes.

Main outputs include:

* mAP and mAP@50:95 per model;
* TIDE error decomposition;
* Activation-Box Ratio results;
* mAP vs ABR scatter plots;
* mAP vs model-size analysis;
* model-selection outputs for Part II.

### 6. Run Part II

Part II evaluates selected models across real and synthetic training-data regimes.

The selected models represent different detector families:

* Faster R-CNN MobileNetV3;
* YOLOv9s;
* YOLO26x;
* RT-DETR-L;
* YOLOS-small.

Main outputs include:

* regime-wise mAP results;
* regime-wise ABR results;
* TIDE error decomposition across regimes;
* prediction and CAM visualizations;
* qualitative failure-case examples.

### 7. Re-generate results

The evaluation and visualization cells can be re-run to regenerate:

* mAP tables;
* TIDE plots;
* ABR plots;
* mAP vs ABR scatter plots;
* CAM-style visualizations;
* attention-map examples;
* prediction examples with ground-truth and predicted bounding boxes.

Most generated figures are not stored directly in GitHub. They are available in the Google Drive artifact folder.

## Experiments

### Part I: Real-only architecture baseline

Part I focuses on architecture comparison. Multiple detection models are trained and evaluated using real DIMO data only.

The goal of this stage is to understand how different object detection architectures behave before testing synthetic-data transfer. This provides a baseline for model selection in Part II.

The analysis considers:

* detection performance;
* localization quality;
* dominant error types;
* activation concentration inside object boxes;
* differences between detector families.

### Part II: Training-data regime transfer

Part II focuses on synthetic-to-real transfer. A smaller set of representative models is trained under different data regimes and evaluated on the same real test set.

This allows us to compare how real data, synthetic data, weak domain randomization, strong domain randomization and mixed training affect:

* detection quality;
* localization errors;
* background errors;
* missed detections;
* activation concentration inside object boxes;
* qualitative prediction behavior.

## Results

Full results are available in the Google Drive artifact folder:

`[TODO: paste Google Drive link to CV_Project_DIMO]`

The result artifacts include:

* Part I architecture baseline outputs;
* Part II regime comparison outputs;
* mAP and mAP@50:95 tables;
* TIDE error decompositions;
* Activation-Box Ratio summaries;
* scatter plots;
* CAM-style visualizations;
* attention-map examples;
* prediction examples;
* qualitative failure cases.

Only lightweight code notebooks are stored in GitHub. Large PNG figures, full output notebooks, trained checkpoints and dataset snapshots are stored externally.

## Report

The final report describes the motivation, related work, dataset, experimental design, results, qualitative analysis, limitations and reproducibility instructions.

**Final report:**
`[TODO: paste PDF or Google Docs link]`

## Notes on reproducibility

This project relies on both GitHub and Google Drive:

* GitHub contains the code notebooks and project documentation.
* Google Drive contains large datasets, full result artifacts, output notebooks and model checkpoints.

To reproduce or inspect the full project, both the GitHub repository and the Google Drive artifact folder are needed.
