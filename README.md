# Jailbreaking-Deep-Models
adversarial attack experiments on ImageNet classifiers using ResNet-34 &amp; DenseNet-121. Jupyter notebooks &amp; scripts cover preprocessing, baseline evaluation, single-step FGSM and multi-step PGD L∞ attacks, 32×32 patch perturbations, transferability analysis, setup, metrics, example visualizations, and reproducible experiments.

Adversarial Attack Experiments

Implementation of five adversarial attack tasks as specified in the course TA PDF citeturn3file0:

1. Baseline Evaluation

Dataset: 501-image subset from 100 ImageNet classes (TestDataSet/TestDataSet), labels mapped using labels_list.json.

Preprocessing: ImageNet normalization (mean=[0.485,0.456,0.406], std=[0.229,0.224,0.225]).

Model: torchvision.models.resnet34(weights="IMAGENET1K_V1") on MPS/CPU.

Results: Top-1 = 75.85%, Top-5 = 94.01%.

2. FGSM Attack (Task 2)

Method: Fast Gradient Sign Method, ε = 0.02 in normalized space.

Verification: L∞ distance ≤ 0.02 in raw pixels.

Results: Top-1 = 3.19%, Top-5 = 20.76%.

Visualization: 5 random (original, adversarial, perturbation) triplets.

3. PGD Attack (Task 3)

Method: Multi-step Projected Gradient Descent, ε = 0.02, 10 steps, α = ε/4, random init inside ε-ball.

Results: Top-1 = 0.00%, Top-5 = 3.79%.

Visualization: 3 representative examples.

4. Patch Attack (Task 4)

Method: 32×32 random mask PGD, ε = 0.3, 10 steps, updates confined to patch.

Results: Top-1 = 42.51%, Top-5 = 78.64%.

Visualization: Overlay of patch location on selected images.

5. Transferability Study (Task 5)

Model: torchvision.models.densenet121(weights="IMAGENET1K_V1").

Datasets: Original, FGSM, PGD, Patch adversarial sets.

DenseNet-121 Results: Top-1 Original=75.25%, FGSM=44.31%, PGD=59.48%, Patch=71.06%.

Analysis: Transfer strength varies; multi-step attacks generalize more than FGSM; patch attacks transfer least.

Reference: Full list of ImageNet-1K models in PyTorch Vision Model Zoo: https://pytorch.org/vision/main/models.html

All experiments are reproducible via the provided Jupyter notebooks and Python scripts.
