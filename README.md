# Medical Image Segmentation with Compressed Inputs

## Abstract
This project explores how different image compression methods affect the performance of deep learning models for medical image segmentation. Specifically, the U-Net architecture is applied to the BraTS2020 dataset to segment brain tumors. 

The compression techniques studied include:
- **Wavelet decomposition** (Haar and db4)
- **Discrete Cosine Transform (DCT)**
- **Karhunen-Loeve Transform (KLT)**
- **Downsampling**

Each method's impact on segmentation accuracy is evaluated. The images are either:
- **Spatially compressed** to a resolution of 64x64
- **Data compressed** to a resolution of 128x128

Results show that while the highest F-score is achieved with original images, methods like KLT and wavelet decomposition still deliver comparable performance. This suggests that compression can substantially reduce storage and computational demands without significantly affecting segmentation accuracy.

## Introduction
Medical image segmentation plays a critical role in clinical diagnosis, treatment planning, and disease monitoring. The emergence of deep learning, particularly with architectures like U-Net, has significantly enhanced segmentation accuracy. However, the sheer volume of high-resolution images in medical datasets poses challenges for storage, transmission, and computational efficiency.

Compression techniques address these challenges by reducing image size while retaining crucial information. However, simple methods like resizing or downsampling can lead to the loss of important features. This project investigates how various compression methods (wavelet-based techniques, DCT, and KLT) affect the U-Net model's performance in brain tumor segmentation. The objective is to evaluate whether these techniques can lower computational demands without compromising segmentation accuracy.

## Methodology
### Dataset
- **BraTS2020 dataset**: Contains MRI brain scans and corresponding segmentation masks.
- **Preprocessing**:
  - Cropped images to 128x128 resolution.
  - Normalized each modality by subtracting the mean and dividing by the standard deviation.
- **Data Splitting**:
  - 60% Training
  - 20% Validation
  - 20% Testing

### Compression Techniques
1. **Downsampling**: Reducing image resolution to 64x64.
2. **Wavelet Transform**: Using Haar and db4 wavelets.
3. **Discrete Cosine Transform (DCT)**: Retaining significant frequency components.
4. **Karhunen-Loeve Transform (KLT)**: Using eigenvalue decomposition for optimal variance retention.

## Results
| Compression Method | F-score |
|--------------------|---------|
| Original (128)     | 0.808   |
| Downsample (64)    | 0.783   |
| Wavelet (db4)      | 0.780   |
| Wavelet (haar)     | 0.770   |
| DCT (128)          | 0.785   |
| KLT (128)          | 0.798   |

## Discussion
The results indicate that the **original images achieved the highest F-score** on both the validation and test sets.

### Key Observations
- **Data Compression**:
  - KLT performed better than DCT, aligning with expectations since KLT preserves more variance through singular values.
  - DCT compression led to more noticeable blurring, reducing segmentation accuracy.
- **Spatial Compression**:
  - Downsampling outperformed wavelet methods (db4 and Haar), which was unexpected since wavelet transforms are typically designed to preserve important features.
  - The minor difference between db4 and Haar wavelets suggests that both methods retained similar levels of detail.

### Key Takeaways
- The **F-score for the original images (0.808) was only slightly higher than for KLT (0.798) and wavelet decomposition (0.780 and 0.770)**.
- **Compression can significantly reduce storage and computation requirements while maintaining acceptable performance** for medical image segmentation tasks.

## Conclusion
This study demonstrates that **compression techniques like KLT and wavelet transforms can effectively reduce image size while maintaining segmentation accuracy**. These findings suggest that **medical image segmentation models can be optimized for computational efficiency without significant performance loss**, making them more feasible for real-world applications.
