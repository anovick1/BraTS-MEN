# BraTS-Meningioma-RT: Meningioma Radiotherapy Segmentation

Using the 2023 data for task 3 of the [BraTS-Lighthouse 2025 Challenge](https://www.synapse.org/Synapse:syn64153130/wiki/631057)

## What’s the problem?

Meningiomas are tumors that arise from the meninges (the tissue that surrounds the brain). Many are benign, but they can still cause harm by pressing on nearby brain structures. When radiation therapy is used, doctors must precisely outline the **Gross Tumor Volume (GTV)** in 3D on MRI. That outline is the target that gets radiation.

## Why is this hard?

* **Time & variability:** Manual outlining is slow (30–60+ minutes per case) and can vary between clinicians.
* **Subtle appearance:** Tumors can look different across patients and scans; edema and post-contrast enhancement can confuse the eye.
* **3D complexity:** The tumor spans many slices in multiple MRI sequences.

## What I'm’re building

I am training training a computer vision model that **automatically segments the tumor (GTV)** from a set of MRI scans acquired for radiotherapy planning. The input is four MRI sequences of the same patient (T1 native, T1 with contrast, T2-weighted, and T2-FLAIR). The output is a **3D mask**: a per-voxel decision of “tumor” vs “not tumor.”

## Why it’s useful

* **Saves time:** Dramatically reduces contouring effort for radiation oncologists.
* **Consistency:** Produces stable outlines that can be reviewed/edited instead of drawn from scratch.
* **Access & equity:** Smaller centers with fewer specialists can start from a strong automated baseline.
* **Research & trials:** Standardized, reproducible GTVs help compare treatments and outcomes.

## What “good” looks like

The model's predictions closely overlap expert annotations (measured by **Dice score**). Clinically, a strong model means: less time spent drawing, fewer missed regions, and fewer unnecessary expansions into healthy brain.
