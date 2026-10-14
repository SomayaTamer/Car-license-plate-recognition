# 🚘 Car License Plate Detection & Character Recognition

🔍 A computer vision project that explores automatic vehicle license plate detection, character segmentation, and text recognition using traditional image processing techniques, a custom K-Nearest Neighbors (KNN) classifier, and EasyOCR.

---

## 📌 About the Project

This project implements a step-by-step pipeline to locate potential license plates in vehicle images and extract their characters for recognition.

It combines **image processing algorithms implemented from scratch using NumPy** with existing computer vision and OCR libraries. It also explores two character recognition approaches: a custom KNN classifier and EasyOCR.

### ✨ Key Features

- 🖼️ **Image Preprocessing:** Grayscale conversion, Gaussian filtering, and median filtering.
- 📊 **Histogram Analysis:** Calculate and visualize pixel intensity distributions.
- 🔎 **Edge Detection:** Implement the Sobel operator to highlight image boundaries.
- ⚫ **Image Segmentation:** Apply thresholding, dilation, and erosion.
- 🧩 **Connected Components:** Identify connected regions and filter potential license plate candidates.
- 🚗 **Plate Detection:** Use region dimensions and aspect ratios to identify possible license plates.
- 🔠 **Character Segmentation:** Extract, normalize, and visualize individual characters.
- 🤖 **Custom KNN Classifier:** Recognize characters using pixel-based feature vectors and a KNN implementation from scratch.
- 📝 **OCR with EasyOCR:** Compare the custom approach with an existing OCR library.

---

## ⚙️ How It Works

The project follows a multi-stage computer vision pipeline:

```text
🚘 Vehicle Image
       |
       v
🖼️ Grayscale Conversion
       |
       v
🧹 Noise Reduction
   Gaussian Filter
       |
       v
🔎 Sobel Edge Detection
       |
       v
⚫ Binary Thresholding
       |
       v
🧩 Morphological Operations
   Dilation & Erosion
       |
       v
🔍 Connected Components
       |
       v
🚗 License Plate Candidates
       |
       v
✂️ Plate Cropping & Character Segmentation
       |
       v
🔠 Character Normalization
       |
       +----------------------+
       |                      |
       v                      v
🤖 Custom KNN             📝 EasyOCR
       |                      |
       v                      v
Character Predictions     OCR Text Results
```

---

## 🛠️ Technologies & Libraries

| Technology | Purpose |
|---|---|
| 🐍 Python | Main programming language |
| 🔢 NumPy | Numerical operations and custom image-processing algorithms |
| 🖼️ OpenCV | Image loading, resizing, and visualization support |
| 📊 Matplotlib | Display images, histograms, and intermediate results |
| 📋 Pandas | Data handling |
| 🤖 scikit-learn | Dataset shuffling and train-test splitting |
| 📥 KaggleHub | Download datasets |
| 📝 EasyOCR | Text recognition from detected plate regions |

---

## 📂 Datasets

### 1. 🚘 Indian Vehicle License Plate Dataset

Used to experiment with license plate detection and image preprocessing.

🔗 [View dataset on Kaggle](https://www.kaggle.com/datasets/saisirishan/indian-vehicle-dataset)

### 2. 🔠 Chars74K Digital English Font Dataset

Used to build the character image dataset for the custom KNN classification experiment.

🔗 [View dataset on Kaggle](https://www.kaggle.com/datasets/supreethrao/chars74kdigitalenglishfont)

📌 **Note:** The datasets are downloaded separately using KaggleHub and are not included in this repository.

---

## 🧠 Implementation Details

### 🖼️ 1. Image Processing from Scratch

Several fundamental image-processing operations are implemented manually using NumPy, including:

- RGB-to-grayscale conversion.
- Gaussian and median filtering.
- Histogram calculation.
- Sobel edge detection.
- Binary thresholding.
- Dilation and erosion.
- Connected-component detection.

These implementations provide practical experience with the underlying operations rather than relying entirely on ready-made functions.

### 🚗 2. License Plate Detection

Potential plate regions are identified by examining connected components and filtering them using geometric properties, including:

- Region width and height.
- Aspect ratio.
- Edge density and edge distribution for candidate scoring.

The selected candidate is cropped for further processing.

### ✂️ 3. Character Segmentation

After extracting a plate candidate, the pipeline:

1. Converts the plate to grayscale.
2. Applies binary thresholding.
3. Identifies connected character regions.
4. Filters regions using size and aspect ratio.
5. Sorts the detected regions from left to right.
6. Resizes the extracted characters to a consistent size.

### 🤖 4. Character Recognition with Custom KNN

The project uses the Chars74K dataset to create character feature vectors from normalized image pixels.

A KNN classifier is implemented from scratch using Euclidean distance to find the nearest training samples and predict each character.

The notebook also evaluates this classifier on a shuffled subset of 3,000 character images using an 80/20 train-test split.

### 📝 5. Recognition with EasyOCR

EasyOCR is applied to the cropped plate regions as an alternative recognition approach. The notebook displays OCR results alongside intermediate plate and character visualizations.

The two approaches are explored experimentally; the notebook does not establish a comprehensive, controlled comparison between their recognition accuracy.

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/car-license-plate-recognition.git
cd car-license-plate-recognition
```

Replace `YOUR-USERNAME` with your GitHub username.

### 2. Install the dependencies

It is recommended to use a virtual environment.

```bash
python -m venv .venv
```

**Windows:**

```bash
.venv\Scripts\activate
```

**macOS / Linux:**

```bash
source .venv/bin/activate
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

### 3. Download the datasets

The notebook uses KaggleHub to download the vehicle and character datasets. Configure Kaggle access if needed.

### 4. Run the notebook

Open `notebooks/car_plate_detection.ipynb` in Jupyter Notebook or Google Colab and run the cells in order.

📌 **Environment note:** The notebook contains a Google Colab-style path for extracting the Chars74K dataset. Update this path if you are running the notebook locally.

---

## 📁 Repository Structure

```text
car-license-plate-recognition/
│
├── 📄 README.md
├── 📄 requirements.txt
├── 📄 .gitignore
│
└── 📁 notebooks/
    └── 📓 car_plate_detection.ipynb
```

---

## ⚠️ Limitations

- Plate detection relies on handcrafted image-processing operations and fixed thresholds.
- Detection and segmentation may be affected by lighting, blur, viewing angles, and image quality.
- Character segmentation may fail when characters overlap, touch, or become disconnected.
- The notebook demonstrates the detection pipeline on a small sample of vehicle images.
- The KNN experiment uses a limited subset of the character dataset.
- Comprehensive detection and OCR accuracy metrics have not been established.

---

## 🔮 Future Improvements

- 🎯 Improve license plate localization under different lighting and viewing conditions.
- 📈 Evaluate detection and recognition on larger, separate test sets.
- 🧠 Explore deep-learning-based license plate detection.
- 🔠 Improve character segmentation and classification.
- 📊 Add quantitative evaluation metrics and compare recognition approaches under consistent conditions.
- 🖥️ Build a simple interface for uploading vehicle images and displaying detected plate text.

---

## 🙌 Acknowledgements

- 📂 Contributors to the [Indian Vehicle License Plate Dataset](https://www.kaggle.com/datasets/saisirishan/indian-vehicle-dataset).
- 🔤 Contributors to the [Chars74K Digital English Font Dataset](https://www.kaggle.com/datasets/supreethrao/chars74kdigitalenglishfont).
- 🛠️ Developers and contributors to NumPy, OpenCV, scikit-learn, Matplotlib, and EasyOCR.

---

📚 **Project Purpose:** Educational and experimental exploration of computer vision, image processing, segmentation, and optical character recognition.

⭐ If you find this project interesting, feel free to explore the notebook and its implementation!
