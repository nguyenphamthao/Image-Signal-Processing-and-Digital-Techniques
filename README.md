# Digital Image Signal Processing and FFT-Based Filtering

This project demonstrates fundamental concepts of **Digital Signal Processing (DSP)** and their application to **digital image processing**.
The project focuses on the relationship between **1D signal processing** and **2D image processing**, using techniques such as **DFT**, **FFT**, **low-pass filtering**, **high-pass filtering**, and objective image quality evaluation.

The system was implemented using **Python**, **OpenCV**, and **NumPy** to process images, apply spatial-domain and frequency-domain filtering, and evaluate the results using **PSNR** and **SSIM** metrics.

---

## 1. Project Overview

Digital Signal Processing plays an important role in analyzing, transforming, filtering, and reconstructing signals.
In this project, the main objective is to apply DSP concepts to image data, where an image is treated as a two-dimensional discrete signal.

The project demonstrates how theoretical DSP concepts such as:

* Discrete Fourier Transform (DFT)
* Fast Fourier Transform (FFT)
* Frequency-domain analysis
* Low-pass filtering
* High-pass filtering
* Image sampling and quantization
* Image quality measurement

can be applied to real image processing tasks.

---

## 2. Main Objectives

The main objectives of this project are:

* Understand the basic theory of **DFT** and **FFT**.
* Analyze how frequency-domain processing can be applied to images.
* Compare spatial-domain filtering and frequency-domain filtering.
* Implement image filtering techniques using Python.
* Evaluate processed images using quantitative metrics.
* Demonstrate the relationship between **1D DSP** and **2D image processing**.

---

## 3. Theoretical Background

### 3.1 Discrete Fourier Transform

The **Discrete Fourier Transform (DFT)** is used to transform a discrete signal from the time or spatial domain into the frequency domain.

For image processing, a grayscale image can be considered as a 2D signal.
The 2D DFT allows the image to be analyzed based on its spatial frequency components.

Low-frequency components usually represent smooth regions and general brightness information, while high-frequency components represent edges, details, and noise.

---

### 3.2 Fast Fourier Transform

The **Fast Fourier Transform (FFT)** is an efficient algorithm used to compute the DFT with much lower computational complexity.

Instead of calculating DFT directly with complexity:

```text
O(N^2)
```

FFT reduces the complexity to:

```text
O(N log N)
```

This makes FFT very useful for image filtering and frequency-domain processing, especially when working with large images.

---

### 3.3 Radix-2 and Radix-4 FFT

This project also discusses FFT structures such as:

* **Radix-2 FFT**
* **Radix-4 FFT**
* Butterfly computation structure
* Divide-and-conquer approach
* Bit-reversal ordering
* Reduction of computational complexity

These concepts help explain why FFT is much faster than direct DFT computation.

---

## 4. Image Processing Techniques

The project applies several image processing techniques, including:

### Low-Pass Filtering

Low-pass filtering allows low-frequency components to pass and reduces high-frequency components.

It is commonly used for:

* Image smoothing
* Noise reduction
* Blurring
* Removing fine details

### High-Pass Filtering

High-pass filtering allows high-frequency components to pass and suppresses low-frequency components.

It is commonly used for:

* Edge detection
* Image sharpening
* Detail enhancement
* Highlighting rapid intensity changes

### FFT-Based Filtering

FFT-based filtering transforms an image into the frequency domain, applies a filter mask, and then reconstructs the image using inverse FFT.

General workflow:

```text
Input Image
   |
   v
Convert to Grayscale
   |
   v
Apply FFT
   |
   v
Shift Frequency Spectrum
   |
   v
Apply Frequency-Domain Filter
   |
   v
Apply Inverse FFT
   |
   v
Reconstructed Image
```

---

## 5. Technologies Used

* Python
* OpenCV
* NumPy
* Matplotlib
* Digital Signal Processing
* DFT / FFT
* Image Filtering
* PSNR
* SSIM

---

## 6. Project Workflow

The image processing workflow includes:

1. Load input images.
2. Convert images to grayscale if necessary.
3. Apply spatial-domain filtering.
4. Apply FFT-based frequency-domain filtering.
5. Reconstruct filtered images.
6. Compare original and processed images.
7. Evaluate results using PSNR and SSIM.
8. Analyze the effect of different filtering methods.

---

## 7. Evaluation Metrics

### PSNR

**PSNR (Peak Signal-to-Noise Ratio)** is used to measure the difference between the original image and the processed image.

A higher PSNR value usually indicates better image reconstruction quality.

### SSIM

**SSIM (Structural Similarity Index Measure)** evaluates the structural similarity between the original image and the processed image.

SSIM values are usually between 0 and 1.

* SSIM close to 1 means the processed image is very similar to the original image.
* Lower SSIM means more structural distortion.

---

## 8. Experimental Results

The project tested multiple images using different filtering techniques.

The main comparison includes:

* Original image
* Low-pass filtered image
* High-pass filtered image
* FFT low-pass filtered image
* FFT high-pass filtered image

For each processed image, quality was evaluated using:

* PSNR
* SSIM
* Visual comparison

Example result for one test image:

| Filtering Method |     PSNR |   SSIM |
| ---------------- | -------: | -----: |
| Low-pass Filter  | 26.80 dB | 0.8460 |
| High-pass Filter | 18.45 dB | 0.5754 |

From the results, low-pass filtering generally preserves the main visual structure better, while high-pass filtering emphasizes edges and details but may reduce overall image similarity.

---

## 9. Discussion

The project shows that DSP principles can be effectively extended from 1D signals to 2D images.

Important observations:

* Low-pass filters smooth images and reduce high-frequency noise.
* High-pass filters enhance edges and image details.
* FFT allows filtering to be performed efficiently in the frequency domain.
* PSNR and SSIM provide useful quantitative evaluation of image quality.
* The choice of filter parameters strongly affects the final image quality.
* Sampling density, quantization bits, window length, and filter design all influence the processing results.

---

## 10. Repository Structure

```text
.
├── src/
│   └── image_processing_code.py
├── images/
│   └── input_test_images
├── results/
│   └── filtered_images_and_outputs
├── documents/
│   └── project_report.pdf
└── README.md
```

You can adjust the folder names depending on the actual structure of the repository.

---

## 11. Key Features

* Demonstrates DFT and FFT theory through image processing.
* Applies low-pass and high-pass filtering.
* Implements FFT-based image filtering.
* Uses OpenCV and NumPy for image manipulation.
* Evaluates image quality using PSNR and SSIM.
* Compares spatial-domain and frequency-domain processing.
* Shows the relationship between 1D DSP and 2D image processing.

---

## 12. Future Development

Possible future improvements include:

* Add more image datasets for testing.
* Implement additional filters such as Gaussian, Butterworth, and Ideal filters.
* Add a graphical user interface for selecting images and filter parameters.
* Compare processing time between spatial-domain convolution and FFT-based filtering.
* Extend the project to color image processing.
* Apply the techniques to real-time video processing.
* Add noise models and denoising algorithms.
* Improve visualization of frequency spectra.

---

## 13. Author

**Pham Thao Nguyen**
Electronics and Telecommunications Engineering
Ho Chi Minh City University of Technology – VNU-HCM
