# RCAN-LowLight-SuperResolution
Joint low-light image denoising and 4× super-resolution using Residual Channel Attention Networks (RCAN). Enhances degraded images by reducing noise and recovering fine details for high-quality restoration.

## Overview

This project focuses on enhancing low-light images and performing 4× super-resolution using a deep learning model based on the Residual Channel Attention Network (RCAN). The model restores spatial detail and improves brightness and clarity in poorly lit conditions.

## Objectives

- Enhance and upscale low-light images efficiently.
- Restore visual details and color fidelity.
- Leverage RCAN architecture with channel attention and pixel shuffle.
- Evaluate with PSNR and SSIM.

## Features

- Custom RCAN architecture with Residual Channel Attention Blocks (RCAB).
- Channel-wise attention mechanism for adaptive enhancement.
- Lightweight upsampling using PixelShuffle.
- End-to-end training and evaluation on low-light image datasets.
- Visual tracking of loss and performance metrics.


Ensure the number of files in each folder matches for pairing.

## Model Architecture

### RCAB (Residual Channel Attention Block)

- 2 Convolutional Layers followed by ReLU
- Channel Attention via Global Average Pooling
- Residual Connection with Attention Scaling

### RCAN Model

- Input: 3-channel RGB image
- Head: 3x3 convolution
- Body: Stack of 10 RCAB blocks
- Upsample: PixelShuffle for 4x scaling
- Tail: Final image reconstruction (RGB output)

## Training Details

The model is trained using the L1 loss function with the Adam optimizer. Training is conducted for 10 epochs using a batch size of 4 for training and 1 for validation. Evaluation metrics include PSNR and SSIM. Input images and ground truths are normalized and transformed using PyTorch's `ToTensor()`.

### Epoch-wise Performance

| Epoch | Avg Train Loss | Validation PSNR (dB) | Validation SSIM |
|-------|----------------|----------------------|-----------------|
| 1     | 0.0213         | 36.45                | 0.9318          |
| 2     | 0.0127         | 37.19                | 0.9395          |
| 3     | 0.0117         | 37.53                | 0.9447          |
| 4     | 0.0111         | 37.93                | 0.9469          |
| 5     | 0.0109         | 37.90                | 0.9484          |
| 6     | 0.0107         | 38.08                | 0.9491          |
| 7     | 0.0106         | 38.20                | 0.9498          |
| 8     | 0.0104         | 38.32                | 0.9504          |
| 9     | 0.0104         | 37.98                | 0.9505          |
| 10    | 0.0103         | 38.11                | 0.9513          |

### Summary

- **Best PSNR**: 38.32 dB (Epoch 8)
- **Best SSIM**: 0.9513 (Epoch 10)
- The model showed consistent improvement in both PSNR and SSIM across epochs.
- Validation performance stabilized after ~Epoch 6, indicating convergence.
