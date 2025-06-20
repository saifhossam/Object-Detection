# Hard Hat Detection using Computer Vision

This project focuses on **enhancing occupational safety** by automating the detection of **Personal Protective Equipment (PPE)**, specifically hard hats, using computer vision techniques. It addresses the challenges of manual safety monitoring on construction and industrial sites.

---

**Motivation**

* **Enhance Worker Safety**: Construction sites pose high risks of head injuries.
* **Reduce Human Error**: Manual PPE monitoring is inconsistent and error-prone.
* **Automated Compliance Monitoring**: Real-time safety enforcement through vision-based systems.

---

**Dataset: Hard Hat Detection**

* **5000 real-world annotated images** from construction/industrial sites.
* Each image includes bounding boxes for: `head`, `helmet`, `person`.
* **Balanced**, **open-source**, and licensed for academic/industrial use.
* [Dataset URL: Hard Hat Detection](#)

---

**System Pipeline Overview**

---

**1. Preprocessing**

* **Resizing**: 416×416 (standard for object detection)
* **Normalization**: Scale pixel values to \[0,1]
* **Noise Reduction**: Used **MedianBlur** (better edge preservation than Gaussian)
* **Contrast Enhancement**: Applied **CLAHE** for adaptive histogram equalization
* **Color Conversion**: RGB, HSV transformations
* **Thresholding**: Binary image creation
* **Sharpening**: Custom 3×3 mask
* **Morphological Operations**: Erosion, Dilation, Opening, Closing, Gradient

---

**2. Segmentation**

* **Binary & Otsu Thresholding**: Pixel-based segmentation
* **Canny Edge Detection**: Highlights object boundaries
* **Contours**: Detects object shapes
* **K-means Clustering**: Segments images into K regions

---

**3. Annotation Parsing (XML)**

* Extracted: `filename`, `image size`, and object labels with bounding boxes.

---

**4. Visualization**

* Drew bounding boxes with color-coded labels (`head`, `helmet`, `person`).

---

**5. Feature Extraction**

* **3D Color Histograms** using OpenCV
* ROI resized to 64×64 → flattened feature vector
* Tried:

  * **HOG**: Good for grayscale + ML (not used)
  * **SIFT**: Better with CNN (not used here)

---

**6. Classification**

* **Random Forest / KNN**: Effective with structured features (color histograms)
* **CNN**: Learns features directly from raw images

---

**Final Output**

* Labeled images with bounding boxes
* Classified objects: Head | Helmet | Person
* Model suitable for integration with real-time surveillance systems

---

**License**

This project uses an open-source dataset and is licensed under MIT for educational and non-commercial use.

---
