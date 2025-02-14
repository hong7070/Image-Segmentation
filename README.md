Abstract
This project explores how different image compression methods affect the performance of deep learning models for medical image segmentation.
Specifically, the U-Net architecture is applied to the BraTS2020 dataset to segment brain tumors.
The compression techniques studied include wavelet decomposition (using Haar and db4), Discrete Cosine Transform (DCT), Karhunen-Loeve Transform (KLT), and downsampling.
Each method's impact on segmentation accuracy is evaluated.
The images are either spatially compressed to 64x64 resolution or compressed through data to 128x128 resolution.
Results show that while the highest F-score is achieved with original images, methods like KLT and wavelet decomposition still deliver comparable performance.
This suggests that compression can substantially reduce storage and computational demands without significantly affecting segmentation accuracy.

Introduction
Medical image segmentation plays a critical role in clinical diagnosis, treatment planning, and disease monitoring.
The emergence of deep learning, particularly with architectures like U-Net, has significantly enhanced segmentation accuracy.
However, the sheer volume of high-resolution images in medical datasets poses challenges for storage, transmission, and computational efficiency.
Compression techniques address these challenges by reducing image size while retaining crucial information.
Yet, simple methods like resizing or downsampling can lead to the loss of important features.
This project investigates how various compression methods: wavelet-based techniques (Haar and db4), Discrete Cosine Transform (DCT), and Karhunen-Loeve Transform (KLT) affect the U-Net model's performance in brain tumor segmentation.
The objective is to evaluate whether these techniques can lower computational demands without compromising segmentation accuracy.

Methodology
BraTS2020 dataset was used, which contains MRI brain scans and corresponding segmentation masks.
The images were preprocessed by cropping to 128x128 resolution and normalizing each modality by subtracting the mean and dividing by the standard deviation.
The dataset was split into 60% for training, 20% for validation, and 20% for testing.

Result
Compression Method    F-score
Original (128)        0.808
Downsample (64)       0.783
Wavelet (db4)         0.780
Wavelet (haar)        0.770
DCT (128)             0.785
KLT (128)             0.798

Discussion
The results indicate that the original images achieved the highest F-score on both the validation and test sets.
For data compression, KLT performed better than DCT, aligning with expectations since KLT preserves more variance through singular values.
DCT compression led to more noticeable blurring, reducing segmentation accuracy.
For spatial compression, downsampling outperformed wavelet methods (db4 and Haar).
This was unexpected, as wavelet transforms are typically designed to preserve important features.
The minor difference between db4 and Haar wavelets suggests that both methods retained similar levels of detail.
Despite these differences, the overall drop in performance due to compression was minimal.
The F-score for the original images (0.808) was only slightly higher than for KLT (0.798) and wavelet decomposition (0.780 and 0.770).
This suggests that compression can significantly reduce storage and computation requirements while maintaining acceptable performance for medical image segmentation tasks.
