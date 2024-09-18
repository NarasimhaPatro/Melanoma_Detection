# Melanoma Detection - Convolutional Neural Network

Melanoma is a life-threatening form of skin cancer that accounts for 75% of skin cancer-related deaths. Early detection can greatly improve survival rates. This project aims to develop a solution that evaluates skin images and assists dermatologists by identifying potential melanoma cases, reducing the manual effort required for diagnosis.

The following multiclass classification model was developed using a custom Convolutional Neural Network (CNN) built with TensorFlow and Keras.

## Table of Contents
- [General Information](#general-information)
- [Process Followed](#process-followed)
- [Model Results](#model-results)
- [Technologies Used](#technologies-used)
- [Acknowledgements](#acknowledgements)
- [Contact](#contact)

## General Information

The dataset consists of **2,357 images** of malignant and benign skin conditions from the **International Skin Imaging Collaboration (ISIC)**. These images are categorized into various skin diseases. While most classes are evenly distributed, melanoma and moles are slightly more prevalent.

The dataset contains images of the following conditions:

- Actinic keratosis
- Basal cell carcinoma
- Dermatofibroma
- Melanoma
- Nevus
- Pigmented benign keratosis
- Seborrheic keratosis
- Squamous cell carcinoma
- Vascular lesion

## Process Followed

In this project, a CNN model was built with several variations and combinations. Improvements in accuracy are summarized below, and the final network structure is described.

### Neural Network Architecture:

- **Rescaling layer**: Normalizes pixel values to the `[0, 1]` range.
- **Convolutional layers**: 
  - Two layers with 32 filters (ReLU activation) followed by a max pooling layer.
  - Two layers with 64 filters (ReLU activation) followed by a max pooling layer.
  - Two layers with 128 filters (ReLU activation) followed by a max pooling layer.
- **Flatten layer**: Converts the output of the pooling layer into a single long vector.
- **Dense layer**: A fully connected layer with 512 neurons (ReLU activation) followed by a **softmax** layer for output classification with 9 neurons (one for each class).

The model uses the **adam** optimizer, **sparse_categorical_crossentropy** as the loss function, and **accuracy** as the evaluation metric.

### Model Variations
1. **Baseline Model**
   - CNN architecture without any augmentations or regularization.
   - Achieved basic performance but suffered from overfitting.
   
2. **Model with Data Augmentation**
   - Applied data augmentation techniques using Keras.
   - Used `RandomRotation`, `RandomZoom`, and `RandomTranslation`.
   
3. **Model with Augmentor Library**
   - External augmentation library (Augmentor) used to balance class imbalance.
   - Added regularization techniques and dropout layers to reduce overfitting.
   - Achieved more stable results across validation and test datasets.

A detailed explanation of the process, along with plots, observations, and conclusions, can be found in the Python notebook.

## Model Results

### Baseline Model Performance
- **Accuracy**: `85%` (Training), `47%` (Validation)
- **Loss**: `0.4162` (Training), `2.6695` (Validation)

### Model with Data Augmentation
- **Accuracy**: `47%` (Training), `46%` (Validation)
- **Loss**: `1.7991` (Training), `1.8813` (Validation)

### Model with Augmentor Library
- **Accuracy**: `85%` (Training), `76%` (Validation)
- **Loss**: `2.4290` (Training), `2.7418` (Validation)

#### Final Results Comparison:

| Model                   | Train Accuracy | Validation Accuracy | Train Loss | Validation Loss |
|-------------------------|----------------|---------------------|------------|-----------------|
| Baseline Model          | 85%            | 47%                 | 0.4162     | 2.6695          |
| Model with Augmentation | 47%            | 46%                 | 1.7991     | 1.8813          |
| Augmentor Library Model | 85%            | 76%                 | 2.4290     | 2.7418          |

## Technologies Used
- TensorFlow - 2.10.1
- Pandas - 2.1.1
- NumPy - 1.24.3
- Matplotlib - 3.8.0
- Seaborn - 0.13.2

> _Note: The versions of the libraries used in this project are specified above._

## Acknowledgements

- This project was part of the **Upgrad-IIITB ML & AI course**.
- The insights gained from the course played a crucial role in the completion of this project.

## Contact

Created by [Narasimha Patro](https://linkedin.com/in/narasimha-patro) | Email: [suraj.cse.28@gmail.com](mailto:suraj.cse.28@gmail.com)