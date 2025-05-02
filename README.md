
# Image Enhancement Project Report

## Table of Contents
1. [Introduction](#introduction)
2. [Objectives](#objectives)
3. [Methodology](#methodology)
    - [Component Extraction](#component-extraction)
    - [Blurry Image Enhancement](#blurry-image-enhancement)
    - [Noise Removal](#noise-removal)
    - [Visual Enhancement](#visual-enhancement)
4. [Techniques Applied](#techniques-applied)
    - [Morphological Operations](#morphological-operations)
    - [High-Pass Filtering](#high-pass-filtering)
    - [Noise Removal Techniques](#noise-removal-techniques)
    - [Histogram Equalization](#histogram-equalization)
5. [Results](#results)
6. [Discussion](#discussion)
7. [Conclusion](#conclusion)
8. [Future Work](#future-work)

---

## Introduction

The image enhancement project focuses on applying a variety of techniques to improve the quality of images that suffer from issues like blurriness, noise, and poor contrast. By utilizing filters, morphological operations, and denoising methods, this project aims to enhance images in terms of sharpness, clarity, and overall visual quality. The project utilizes Python and OpenCV to process the images.

---

## Objectives

The main objectives of the project are:
1. To extract specific components (e.g., circles, structures) from images.
2. To enhance blurry images, particularly by sharpening and filtering.
3. To remove noise from images using various noise reduction techniques.
4. To enhance the overall visual quality of challenging images.

---

## Methodology

### Component Extraction

The first objective is to extract components like circles from the given images. For this, morphological operations and Hough Circle Transforms are used. These techniques help detect and isolate specific structures like circles from noisy or cluttered backgrounds.

### Blurry Image Enhancement

Images such as the ones of a building and a dog suffer from blurriness. To improve their sharpness, high-pass filtering and sharpening techniques are applied. The high-pass filter emphasizes edges in the images, making them appear clearer.

### Noise Removal

Some images, such as the noisy text or rocket images, contain noise that hampers clarity. To address this, various noise removal techniques are employed, including:
- **Gaussian Blur**: A method that smooths out noise while maintaining important features in the image.
- **Median Filtering**: Helps in removing salt-and-pepper noise.
- **Non-Local Means Denoising**: A more advanced method that preserves image details while reducing noise.

### Visual Enhancement

Images with poor contrast, such as the nameplate or newspaper images, can benefit from histogram equalization and sharpening. Histogram equalization improves the contrast of the images, making the details clearer, while sharpening enhances the visual quality.

---

## Techniques Applied

### Morphological Operations

Morphological operations are used to extract components from images. In this project, circles in the image are detected using the Hough Circle Transform method.

**Example Code for Circle Extraction:**
```python
detected_circles = cv2.HoughCircles(blurred, cv2.HOUGH_GRADIENT, dp=1.2, minDist=40, param1=50, param2=30, minRadius=10, maxRadius=40)
````

### High-Pass Filtering

To enhance blurry images, high-pass filters are used. These filters help sharpen the edges of the image by subtracting low-frequency components and retaining high-frequency details.

**Example Code for High-Pass Filtering:**

```python
high_pass_kernel = np.array([[-1, -1, -1], [-1, 8, -1], [-1, -1, -1]])
filtered_building = cv2.filter2D(gray_building, -1, high_pass_kernel)
```

### Noise Removal Techniques

Different noise removal techniques are used for various images:

* **Gaussian Blur**: Applied to smooth out image noise without sacrificing too much detail.
* **Median Filtering**: Used to remove salt-and-pepper noise.
* **Non-Local Means Denoising**: This technique is effective for removing noise while maintaining the quality of the image.

**Example Code for Gaussian Blur:**

```python
gaussian_text = cv2.GaussianBlur(text_img_rgb, (5, 5), 0)
```

### Histogram Equalization

For images with poor contrast, histogram equalization is used to improve visibility. It redistributes the intensity levels of the image, ensuring that the dark areas become more distinguishable.

**Example Code for Histogram Equalization:**

```python
img_nameplate_eq = cv2.equalizeHist(img_nameplate)
```

---

## Results

The following results were obtained from applying the techniques to the original images:

### 1. Circles Image

* **Before Enhancement**: Circles were partially visible due to the cluttered background.
* **After Enhancement**: Morphological operations successfully extracted the circles, making them more defined.

### 2. Building Image (Blurry)

* **Before Enhancement**: The building image was blurry, making the structure unclear.
* **After Enhancement**: High-pass filtering sharpened the edges, making the building structure clearer.

### 3. Dog Image (Blurry)

* **Before Enhancement**: The image of the dog was unclear due to blur.
* **After Enhancement**: The dog image was sharpened, making the details more visible.

### 4. Noisy Text Image

* **Before Enhancement**: The image contained salt-and-pepper noise.
* **After Enhancement**: Median filtering and non-local means denoising significantly reduced the noise, enhancing the text's readability.

### 5. Noisy Rocket Image

* **Before Enhancement**: The rocket image had significant noise.
* **After Enhancement**: Gaussian blur and non-local means denoising helped smooth out the noise while preserving key details.

### 6. Noisy Wind Chart

* **Before Enhancement**: The wind chart was cluttered with noise, affecting its visibility.
* **After Enhancement**: Gaussian blur and noise reduction techniques cleaned up the chart, improving the contrast and clarity of the data.

### 7. Newspaper Image (Noisy)

* **Before Enhancement**: The newspaper image was noisy, making text difficult to read.
* **After Enhancement**: Non-local means denoising and sharpening made the text clearer and more readable.

### 8. Nameplate Image (Noisy)

* **Before Enhancement**: The image of the nameplate had significant noise.
* **After Enhancement**: Histogram equalization and sharpening enhanced the contrast and text visibility.

---

## Discussion

The techniques applied showed promising results in improving image quality. Morphological operations helped isolate specific components (like circles), and high-pass filtering successfully sharpened blurry images. Noise removal methods, particularly non-local means denoising, proved to be highly effective in maintaining the quality of the image while reducing noise.

However, there were limitations. For example, in highly noisy images (like the rocket or text), some fine details were still lost after denoising. The performance of sharpening and high-pass filtering varied depending on the image content.

---

## Conclusion

In conclusion, the project successfully demonstrated various image enhancement techniques, including morphological operations, high-pass filtering, noise removal, and histogram equalization. These techniques were applied to improve images with different issues, such as blurriness, noise, and poor contrast. 

The results showed clear improvements in the visual quality of most of the images. For example, the building and rocket images saw significant improvements in sharpness and clarity, while the noisy wind chart and nameplate images had their contrast and readability enhanced. 

However, the techniques applied did not fully resolve issues in the dog and text images. While some improvement was observed, these images did not reach the desired clarity due to their inherent challenges, such as severe blurriness or complex noise patterns.

Overall, the methods proved effective for most images, though further optimization, especially for highly complex or noisy images, is necessary.


---

## Future Work

1. **Advanced Denoising**: Further explore advanced denoising algorithms such as deep learning-based approaches.
2. **Edge Detection**: Apply edge detection techniques like Canny edge detection to enhance image features.

