
# BraTS-Meningioma-RT: Meningioma Radiotherapy Segmentation

This project tackles **Task 3 (Meningioma Radiotherapy Segmentation)** from the [BraTS-Lighthouse 2025 Challenge](https://www.synapse.org/Synapse:syn64153130/wiki/631057), using the 2023 dataset.

---

## Problem

**Meningiomas** are tumors that arise from the meninges (the membranes surrounding the brain). Most are benign, but they can still cause serious issues by pressing on nearby structures.

In radiotherapy, doctors must precisely outline the **Gross Tumor Volume (GTV)** in 3D MRI scans. This contour defines the radiation target.

**Challenges:**

* **Time & variability:** Manual contouring takes 30–60 minutes per patient and varies across clinicians.
* **Subtle appearance:** Tumors can look very different across patients and sequences; contrast enhancement and edema add complexity.
* **3D complexity:** Tumors span multiple slices, across four MRI sequences, requiring careful review.

---

## Goal

Build a computer vision model that **automatically segments the tumor (GTV)** on MRI scans for radiotherapy planning.

**Input:** Four MRI sequences per patient:

* T1 native (T1n)
* T1 post-contrast (T1c)
* T2-weighted (T2w)
* T2-FLAIR (T2f)

**Output:** A **3D binary mask** where each voxel is labeled “tumor” or “not tumor.”

---

## Why this matters

* ⏱ **Efficiency:** Reduces time spent on manual contouring.
* 📈 **Consistency:** Produces stable, reproducible contours that clinicians can edit instead of starting from scratch.
* 🌍 **Access & equity:** Smaller centers with fewer specialists can benefit from strong automated baselines.
* 🔬 **Research:** Standardized GTVs make it easier to compare treatments and clinical trial outcomes.

---

## What “good” looks like

* **Quantitative:** High overlap between predictions and expert annotations, measured by **Dice Similarity Coefficient (DSC)**.
* **Clinical impact:** Fewer missed regions, less unnecessary radiation to healthy tissue, and faster planning workflows.

---

## Approach

* Framework: [MONAI](https://monai.io/) + PyTorch
* Model: 3D U-Net (baseline)
* Training setup:

  * Inputs cropped to 96³ or 128³ ROIs
  * Dice + Cross Entropy loss
  * Sliding-window inference for full-volume prediction
  * Checkpointing best model based on validation Dice
* Hardware: Colab Pro (L4/T4/A100 GPU)

---

## Results (TBD)



