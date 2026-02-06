Multi-Task Deep Learning for Segmentation, Localization, and Classification
================================================================

Overview
--------
This repository implements a multi-task deep learning framework for solving
multiple computer vision problems using the MNIST dataset. The project
demonstrates an end-to-end pipeline covering dataset creation, model design,
training from scratch, evaluation, and visualization.

By sharing representations across related tasks, the models jointly learn
foreground extraction, object localization, and semantic segmentation,
showcasing the effectiveness of multi-task learning in vision systems.


Tasks Implemented
-----------------

1) Dataset Creation
   - Foreground Segmentation Dataset
     * Binary foreground masks generated using Otsu’s thresholding
     * Class labels are not required

   - Classification with Circlization Dataset
     * Tight enclosing circular masks generated for each digit
     * Each sample includes an image, circular localization mask, and class label

   - Semantic Segmentation Dataset
     * Four digits randomly concatenated into a 2×2 grid
     * Pixel-wise labels for 10 digit classes + background
     * Over 250,000 unique images with no duplicates


2) Foreground Extraction
   - Model: U-Net (binary segmentation)
   - Metric: Intersection over Union (IoU)


3) Classification with Circlization
   - Model: Multi-task CNN with shared encoder
   - Jointly performs:
       * Digit classification
       * Circular mask prediction (localization)
   - Metrics:
       * Classification accuracy
       * IoU (set to zero if classification is incorrect)


4) Semantic Segmentation
   - Model: Multi-class U-Net (11 classes)
   - Metric: Dice Coefficient
   - Performance: 99.29% test Dice score


Model Design Highlights
-----------------------
- Shared feature encoders for efficient representation learning
- Task-specific decoder heads
- U-Net–based architectures for segmentation tasks
- Joint loss optimization for multi-task learning


Evaluation Metrics
------------------
- Intersection over Union (IoU)
- Dice Coefficient
- Classification-aware IoU for localization


Tech Stack
----------
- Python
- PyTorch
- OpenCV
- NumPy
- Matplotlib
- CUDA (optional GPU acceleration)


Results Summary
---------------
| Task                  | Metric   | Performance |
| --------------------- | -------- | ----------- |
| Foreground Extraction | IoU      | **99.63%**  |
| Classification        | Accuracy | **99.46%**  |
| Localization          | IoU      | **94.39%**  |
| Semantic Segmentation | Dice     | **99.29%**  |



Key Learning Outcomes
---------------------
- Large-scale dataset generation for vision tasks
- Training deep neural networks from scratch
- Multi-task learning for computer vision
- Custom metric implementation and evaluation
- Visualization and interpretation of model outputs
