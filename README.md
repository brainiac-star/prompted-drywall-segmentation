Prompted Segmentation for Drywall QA

This project fine-tunes a CLIPSeg model to perform text-conditioned image segmentation for two tasks:

Segment Crack (Cracks Dataset)

Segment Taping Area (Drywall-Join-Detect Dataset)

Given an image and a prompt such as "segment crack" or "segment taping area", the model outputs a binary mask highlighting only that region.

1. Datasets

Two datasets from Roboflow were used:

Cracks Dataset: 5164 train, 201 valid

Drywall Dataset: 820 train, 202 valid

Masks were generated from COCO annotations:

Cracks: polygon masks (or bbox+dilation when polygons missing)

Drywall: bounding-box masks

2. Method

The project uses CLIPSeg (CIDAS/clipseg-rd64-refined).

Steps:

Preprocess datasets and build binary masks

Combine images + masks + text prompts

Fine-tune CLIPSeg for 10 epochs

Evaluate mIoU, Dice, inference time

Generate prediction masks at original resolution

3. Results
Prompt	mIoU	Dice	Inference Time
segment crack	0.281	0.382	0.055 s
segment taping area	0.537	0.668	0.042 s

Model size: 578 MB

4. Visual Examples

The repository includes prediction samples showing:

Original image

Ground Truth mask

Predicted mask

Overlay
<img width="1145" height="426" alt="image" src="https://github.com/user-attachments/assets/18f863c0-dac4-499b-b635-992d151d53cc" />
<img width="1139" height="431" alt="image" src="https://github.com/user-attachments/assets/ec38fe26-4908-44e1-8ac2-a25a8714f728" />


5. Notebook

Full code is available in the Colab notebook:

👉 Colab Link:
https://colab.research.google.com/drive/1F9yOdxgS32W2vN6lkx20FECH1iV0g6aJ?usp=sharing

6. Report

A complete PDF report is included:

Methodology

Data preparation

Results

Visual examples

Failure cases
