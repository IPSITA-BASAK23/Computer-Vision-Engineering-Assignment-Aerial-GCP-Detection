# Computer-Vision-Engineering-Assignment-Aerial-GCP-Detection


## 1. Background

In aerial surveying and photogrammetry, **Ground Control Points (GCPs)** are physical markers placed on the ground before a drone flight. These markers are manually surveyed with high-precision GPS equipment and act as anchor points to tie the drone imagery to exact geographical coordinates.

Identifying the exact pixel coordinates of the center of these markers in aerial images is a critical step in the 3D reconstruction pipeline. Your task is to automate this process.

## 2. Problem Statement

Given an aerial image crop containing a GCP marker, your solution must produce two outputs:

1. The precise $(x, y)$ pixel coordinates of the **center** of the GCP marker.
2. The **shape** of the marker, classified as one of: `Cross`, `Square`, or `L-Shaped`.

You are free to approach this however you see fit. We care about the quality of your results and the clarity of your reasoning, not a specific architecture or technique.

## 3. The Dataset

**Download the dataset here:** [Google Drive](https://drive.google.com/drive/folders/1RDNiAO1EynKrRDomcVNXQW1-ct5zzvE5?usp=sharing)

You have been provided with two directories: a `train_dataset` and a `test_dataset`.

The dataset consists of high-resolution images (2048x1365). The images are organized in a nested directory structure mimicking our production environment: `project_name/survey_name/gcp_id/image.JPG`.

**Important Note:** This dataset reflects real-world production conditions. It is not a perfectly sanitized academic dataset. You should conduct thorough Exploratory Data Analysis (EDA) before designing your approach.

### Label Format

In the `train_dataset` directory, you will find a `curated_gcp_marks.json` file containing the ground-truth annotations. It maps the relative image path to its labels:

```json
{
    "project1/survey1/2/DJI_0431.JPG": {
        "mark": {
            "x": 1024.5,
            "y": 850.2
        },
        "verified_shape": "L-Shaped"
    }
}

```

The `test_dataset` contains only the raw images. You do not have access to the ground truth for this set.

## 4. Deliverables

Please submit a repository (or a zipped folder) containing the following:

1. **The Codebase:** All code, scripts, or Jupyter notebooks used for EDA, data loading, model training, and inference.
2. **Model Weights:** Instructions on how to download your best model weights (e.g., via a Google Drive or AWS S3 link).
3. **A `predictions.json` File:** You must run your final trained model on the unlabelled `test_dataset` and generate a JSON file formatted *exactly* like the training labels.
4. **README / Write-up:** A concise document outlining:
    * Your approach and why you chose it.
    * Your training strategy (data augmentations, loss functions, handling of dataset characteristics).
    * Any challenges you encountered with the dataset and how you mitigated them.
    * Instructions on how to run your inference script to reproduce your `predictions.json`.



## 5. Evaluation Criteria

We will evaluate your model by comparing your submitted `predictions.json` against our hidden test set ground truth. You are not restricted to any specific architecture or technique.

You will be graded on:

* **Localization Accuracy:** How close your predicted $(x, y)$ coordinates are to the actual marker centers, measured across multiple pixel-distance thresholds.
* **Classification Accuracy:** How well your shape predictions match the ground truth across all three classes.
* **Engineering Quality:** We look for clean, modular, and reproducible code. Practical, robust solutions are valued higher than overly complex architectures that are difficult to deploy.
* **Data Handling:** Your ability to identify and appropriately handle the unique constraints and distributions of the provided data.

---

