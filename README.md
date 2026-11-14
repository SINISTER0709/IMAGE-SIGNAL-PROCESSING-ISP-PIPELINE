# Image Signal Processing (ISP) Pipeline

A Python-based implementation of an **Image Signal Processing (ISP) Pipeline** that transforms RAW Bayer sensor data into visually enhanced RGB images.

This project explores the fundamental stages of digital camera image processing, including sensor data correction, noise reduction, demosaicing, color enhancement, and post-processing.

The pipeline is implemented using Python, NumPy, OpenCV, RawPy, and Matplotlib in a Jupyter Notebook.

## Project Overview

Digital camera sensors capture light intensity through a Color Filter Array (CFA), typically arranged in a Bayer pattern. The captured RAW data requires several processing stages before it can be displayed as a full-color image.

This project implements and experiments with these processing stages to understand how RAW sensor data is converted into an RGB image.

## ISP Pipeline Architecture

```text
RAW Bayer Image (.ARW)
        |
        v
Black Level Correction (BLC)
        |
        v
Defective Pixel Correction (DPC)
        |
        v
Bayer Noise Reduction (BNR)
        |
        v
Demosaicing
        |
        v
Auto White Balance (AWB)
        |
        v
Color Correction (CCM)
        |
        v
Gamma Correction
        |
        v
Sharpening and Saturation Enhancement
        |
        v
Final RGB Image
```

## Implemented Processing Stages

### 1. RAW Image Acquisition
- Loads Sony RAW `.ARW` images using RawPy.
- Extracts Bayer sensor data.
- Examines the camera's black level, white level, and Bayer pattern.

### 2. Black Level Correction (BLC)
- Subtracts the sensor's black-level offset.
- Normalizes the RAW pixel intensities.
- Clips negative intensity values.

### 3. Defective Pixel Correction (DPC)
- Identifies potentially defective pixels using a neighborhood-based threshold.
- Replaces detected outliers with neighboring median values.
- Visualizes corrected pixels using difference maps.

### 4. Bayer Noise Reduction (BNR)
- Applies bilateral filtering to individual Bayer color planes.
- Reduces noise while attempting to preserve image edges.

### 5. Demosaicing
- Reconstructs a full RGB image from Bayer data.
- Uses convolution-based interpolation for missing color information.

### 6. Auto White Balance (AWB)
Explores multiple white-balance techniques:
- Channel-mean-based white balance
- Bright-pixel-based illuminant estimation
- Block-based illuminant estimation

### 7. Color Correction
- Applies a 3×3 Color Correction Matrix (CCM).
- Experiments with color channel cross-talk correction.
- Implements an intensity-dependent adaptive color correction approach.

### 8. Gamma Correction
- Applies nonlinear gamma adjustment to the processed RGB image.
- Adjusts the resulting intensity range.

### 9. Image Enhancement
- Applies image sharpening using a convolution kernel.
- Performs a simple saturation/color-intensity enhancement.
- Generates final output images for visualization.

## Technologies Used

- **Python** — Primary programming language
- **NumPy** — Numerical computation and image array manipulation
- **OpenCV** — Image filtering and processing
- **RawPy** — RAW camera image reading
- **Matplotlib** — Image visualization
- **Jupyter Notebook** — Implementation and experimentation
- **Kaggle** — Notebook environment and dataset access

## Dataset

The project uses Sony RAW images from the **See-in-the-Dark (SID) dataset**.

The notebook references both short-exposure and long-exposure Sony `.ARW` images.

Dataset reference: [Learning to See in the Dark](https://github.com/cchen156/Learning-to-See-in-the-Dark)

The dataset is not included in this repository.

## Installation and Usage

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/image-signal-processing-pipeline.git
cd image-signal-processing-pipeline
```

### 2. Install the required dependencies

```bash
pip install numpy pandas matplotlib opencv-python rawpy imageio jupyter
```

### 3. Open the ISP Pipeline Notebook

```bash
jupyter notebook isp-pipeline-cv.ipynb
```

### 4. Configure the Dataset

Update the RAW image file paths inside `isp-pipeline-cv.ipynb` to match your dataset location.

### 5. Run the ISP Pipeline

Execute the notebook cells sequentially to visualize each image processing stage and generate the final enhanced RGB image.


The notebook generates intermediate visualizations including:

- RAW Bayer image
- Black-level-corrected image
- Defective pixel correction comparison
- Bayer noise reduction comparison
- Demosaiced RGB image
- White-balanced image
- Color-corrected image
- Gamma-corrected image
- Sharpened and enhanced image

The notebook also saves:

- `final_output.png`
- `final_output_enhanced.png`

## Current Scope and Limitations

- The implementation is primarily experimental and notebook-based.
- The Bayer channel indexing assumes an RGGB arrangement.
- Some correction parameters are manually selected for experimentation.
- The original dataset paths are specific to Kaggle.
- The pipeline has not been packaged or validated for arbitrary RAW camera formats.

## Future Improvements

- Support multiple Bayer patterns.
- Implement more advanced demosaicing algorithms.
- Add automatic parameter tuning.
- Improve color correction using calibrated camera matrices.
- Introduce quantitative image quality evaluation.
- Modularize the notebook into reusable Python functions.
- Compare processing results with reference RAW development tools.

## Project Objective

To gain practical experience in camera Image Signal Processing by implementing and visualizing the key stages involved in converting RAW sensor data into a visually enhanced RGB image.

## Author

**YOUR NAME**

GitHub: SINISTER0709 https://github.com/SINISTER0709
