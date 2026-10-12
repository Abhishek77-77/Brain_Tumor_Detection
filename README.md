# Brain Tumor Classification Using MRI

An academic machine learning project that classifies brain MRI images into four categories using deep learning. The project compares a custom Convolutional Neural Network (CNN), Vision Transformer (ViT), and EfficientNetB0, and provides an interactive Gradio interface for image-based predictions.

> **Disclaimer:** This project is intended for academic and research purposes only. It is not a medical diagnostic tool.

## Problem Statement

Brain MRI images contain visual patterns that can help distinguish different tumor categories. This project explores deep learning models for classifying MRI images into:

- Glioma
- Meningioma
- No Tumor
- Pituitary

## Dataset

The project uses the [Brain Tumor MRI Dataset by Masoud Nickparvar on Kaggle](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset).

| Split | Images |
|---|---:|
| Training | 5,600 |
| Validation / development | 1,600 |
| **Total** | **7,200** |

Each of the four classes contains 1,400 training images and 400 images in the supplied testing folder.

Images are converted to RGB and resized to 224 × 224 pixels before being passed to the model.

## Models Compared

1. **Custom CNN** — a convolutional neural network built for four-class classification.
2. **Vision Transformer (ViT)** — a pretrained transformer-based image classification approach, evaluated with frozen and fine-tuned configurations.
3. **EfficientNetB0** — an ImageNet-pretrained convolutional backbone with a custom classification head.

EfficientNetB0 achieved the strongest result among the configurations tested.

## Results

### Model comparison

| Model | Best recorded accuracy |
|---|---:|
| Custom CNN | 69.31% |
| ViT — frozen backbone | 43.38% |
| ViT — fine-tuned | 59.75% |
| **EfficientNetB0** | **83.31%** |

### EfficientNetB0 classification metrics

| Class | Precision | Recall | F1-score |
|---|---:|---:|---:|
| Glioma | 0.91 | 0.61 | 0.74 |
| Meningioma | 0.71 | 0.78 | 0.74 |
| No Tumor | 0.86 | 0.99 | 0.92 |
| Pituitary | 0.88 | 0.95 | 0.91 |
| **Macro average** | **0.84** | **0.83** | **0.83** |
| **Weighted average** | **0.84** | **0.83** | **0.83** |

Overall accuracy on the 1,600-image development set: **83.31%**.

### Confusion matrix

Rows represent actual classes; columns represent predicted classes. Class order: Glioma, Meningioma, No Tumor, Pituitary.

| Actual \ Predicted | Glioma | Meningioma | No Tumor | Pituitary |
|---|---:|---:|---:|---:|
| Glioma | 246 | 107 | 32 | 15 |
| Meningioma | 20 | 311 | 30 | 39 |
| No Tumor | 1 | 3 | 396 | 0 |
| Pituitary | 2 | 18 | 0 | 380 |

The model performs particularly well on the No Tumor and Pituitary classes. Glioma recall is lower, indicating that further improvement is needed.

**Evaluation note:** The reported accuracy is measured on the dataset's supplied `Testing` folder, used here for development and model comparison. It should not be interpreted as independent external validation or clinical performance.

## Application

The project includes a Gradio interface intended to let users:

- Upload a brain MRI image.
- Obtain a predicted class.
- View the model's class-confidence scores.

Confidence scores represent the model's outputs, not the probability that a medical diagnosis is correct.

## Running the Project

1. Clone or download this repository.
2. Open the notebook in Google Colab.
3. Download the dataset from Kaggle and configure its path.
4. Install the required Python dependencies.
5. Run the notebook cells to train or evaluate the models.

The Gradio application requires the saved EfficientNetB0 model. Model loading instructions and the model's hosting location should be documented once the deployment files are finalized.

## Technologies

- Python
- TensorFlow / Keras
- EfficientNetB0
- Convolutional Neural Networks
- Vision Transformer
- NumPy and scikit-learn
- Gradio
- Google Colab

## Future Work

- Improve glioma classification and reduce confusion between tumor categories.
- Evaluate the model on a separate, previously unseen dataset.
- Explore fine-tuning and data augmentation strategies.
- Improve application usability and deployment.
- Add additional evaluation visualizations.

## Author

Computer Engineering undergraduate project focused on machine learning and healthcare image classification.
