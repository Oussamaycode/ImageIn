# 🌍 Intel Image Classification using CNNs

A Computer Vision project using Deep Learning and TensorFlow/Keras to classify natural and urban environments into six categories. The model takes an image as input and predicts its corresponding class along with a confidence score.

The model was trained using GPU computing resources provided by **[Vast.ai](https://vast.ai/)**.

## 📌 Project Overview

The objective of this project is to develop an image classification system capable of automatically identifying the environment represented in an image.

The project explores Convolutional Neural Networks (CNNs), image preprocessing, data augmentation, model training, evaluation, and prediction using TensorFlow/Keras.

### 🎯 Objectives

- Classify images into six environment categories.
- Explore and preprocess the Intel Image Classification dataset.
- Build and train a CNN using TensorFlow/Keras.
- Apply data augmentation to improve generalization.
- Evaluate model performance using classification metrics.
- Analyze misclassified images and common prediction errors.
- Experiment with different model configurations.
- Save the final model and use it to predict new images.

## 🗂️ Dataset

**Dataset:** Intel Image Classification

The dataset contains approximately 17,000 images distributed across six classes.

| Class | Description |
|---|---|
| `buildings` | Buildings and constructed environments |
| `forest` | Forests and wooded areas |
| `glacier` | Glaciers and icy landscapes |
| `mountain` | Mountainous landscapes |
| `sea` | Seas and ocean environments |
| `street` | Streets and urban roads |

The dataset was provided through Discord as part of the project.

## 🛠️ Technologies

- **Python** — Main programming language
- **TensorFlow / Keras** — CNN construction and training
- **NumPy** — Numerical operations
- **Pandas** — Data analysis
- **Scikit-learn** — Evaluation metrics and dataset splitting
- **Matplotlib / Seaborn** — Visualizations and confusion matrix
- **Pillow (PIL)** — Image loading and processing
- **tf.data** — Efficient image pipeline and batch loading
- **Vast.ai** — Cloud GPU computing for model training
- **Git / GitHub** — Version control and project management

## 🧠 Methodology

The project follows an eight-step workflow.

### 1. Data Exploration

- Inspect the dataset structure and image formats.
- Identify the six target classes.
- Count images per class and analyze class distribution.
- Visualize sample images.
- Check image dimensions and identify problematic files.
- Split the data into training, validation, and test sets.

### 2. Preprocessing and Data Augmentation

Images are resized to a consistent input dimension and normalized before being passed to the model.

The image pipeline uses batching and efficient loading to support training.

Data augmentation is applied **only to the training set**, using transformations such as:

- Random rotation
- Horizontal flipping
- Zoom
- Translation
- Slight contrast variation

These transformations help expose the model to more visual variations and reduce overfitting.

### 3. CNN Architecture

The model uses Convolutional Neural Network layers implemented with TensorFlow/Keras.

The architecture can include:

- `Conv2D` for extracting visual features
- `ReLU` for introducing non-linearity
- `MaxPooling2D` for reducing spatial dimensions
- `Flatten` or `GlobalAveragePooling2D` for feature aggregation
- `Dense` layers for classification
- `Dropout` for regularization

The final classification layer produces scores for the six environment categories.

### 4. Model Training

The model is compiled and trained using:

- **Optimizer:** Adam
- **Loss function:** Categorical or sparse categorical cross-entropy, depending on the label format
- **Evaluation metric:** Accuracy
- **Callbacks:** EarlyStopping and, optionally, ReduceLROnPlateau

Training is performed using GPU resources on **Vast.ai**.

Training and validation accuracy and loss are plotted to monitor convergence and identify potential overfitting or underfitting.

### 5. Model Evaluation

The final model is evaluated on a separate test set that is not used for training or model selection.

Evaluation metrics include:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix

Misclassified images are also visualized to identify common errors and understand which classes are more difficult to distinguish.

### 6. Model Improvement

Multiple configurations are compared by changing parameters such as:

- Number of convolutional layers and filters
- Dropout rate
- Learning rate
- Batch size
- Data augmentation settings
- Number of training epochs

The final configuration is selected based on validation performance and generalization to unseen test images.

### 7. Prediction on New Images

The trained model is saved and can be loaded to classify new images.

The prediction pipeline:

1. Loads an image from a file.
2. Applies the same resizing and preprocessing used during training.
3. Runs the image through the trained model.
4. Identifies the predicted class.
5. Returns the predicted class and its probability.

### 8. Final Analysis

The final results are analyzed to determine:

- Which configuration performs best.
- Which classes are most difficult to classify.
- Which classes are frequently confused.
- Whether overfitting occurred.
- How data augmentation affected performance.
- What improvements could be explored in future work.

## ☁️ Training Infrastructure

Model training was performed on **[Vast.ai](https://vast.ai/)**, a platform that provides access to cloud GPU computing resources.

Using a cloud GPU allows computationally intensive deep learning experiments to run without relying exclusively on local hardware.

## 📊 Results

The final model is evaluated using the test dataset.

| Metric | Result |
|---|---|
| Test accuracy | To be added |
| Weighted precision | To be added |
| Weighted recall | To be added |
| Weighted F1-score | To be added |
| Best configuration | To be added |

*Replace these placeholders with the actual results obtained during evaluation.*

Training and validation curves, the confusion matrix, and examples of misclassified images can be included here.

## 🚀 Installation

### Prerequisites

- Python 3.10 or a compatible Python version supported by the installed TensorFlow release
- pip
- Git

### 1. Clone the repository

```bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_PROJECT_DIRECTORY>
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```powershell
.venv\Scripts\activate
```

On Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

If a `requirements.txt` file is available:

```bash
pip install -r requirements.txt
```

Otherwise, install the main dependencies:

```bash
pip install tensorflow numpy pandas scikit-learn matplotlib seaborn pillow
```

For GPU training, use a TensorFlow and CUDA configuration compatible with the selected Vast.ai instance.

## 📁 Project Structure

The following is a suggested structure; adapt it to match the actual repository.

```text
intel-image-classification/
│
├── data/
│   ├── train/
│   ├── validation/
│   └── test/
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_preprocessing_augmentation.ipynb
│   ├── 03_cnn_training.ipynb
│   ├── 04_evaluation.ipynb
│   └── 05_model_comparison.ipynb
│
├── models/
│   └── best_model.keras
│
├── results/
│   ├── training_curves.png
│   ├── confusion_matrix.png
│   └── misclassified_images.png
│
├── src/
│   └── predict.py
│
├── requirements.txt
├── .gitignore
└── README.md
```

## 🔮 Example Prediction

Example of the expected output when predicting a new image:

```text
Predicted class: mountain
Probability: 94.25%
```

*This is an illustrative example, not a measured result from the trained model.*

## ⚠️ Limitations

- Performance depends on the quality and diversity of the training dataset.
- Visually similar environments may be confused, such as mountains and glaciers or buildings and streets.
- Images containing multiple environments may be difficult to classify into a single category.
- Predictions can be unreliable for images that differ significantly from the training data.
- The predicted probability represents the model's confidence score and is not necessarily a calibrated probability of correctness.

## 🔧 Future Improvements

- Experiment with transfer learning using pretrained architectures such as MobileNetV2, EfficientNet, or ResNet.
- Tune hyperparameters systematically.
- Improve generalization with carefully selected augmentation strategies.
- Analyze class-specific errors and potential class imbalance.
- Evaluate inference speed and model size.
- Develop a simple web interface for uploading images and displaying predictions.
- Investigate probability calibration and robustness on out-of-distribution images.

## 👨‍💻 Author

Developed as a Computer Vision and Deep Learning project focused on image classification using TensorFlow/Keras and cloud GPU training with Vast.ai.

## 📄 License

Specify the license applicable to this project and verify the dataset's redistribution terms before publishing the dataset or derived assets.
