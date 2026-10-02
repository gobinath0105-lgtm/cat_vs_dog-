# 🐱🐶 Cat vs Dog Image Classifier using CNN

A Deep Learning image classification project that uses a Convolutional Neural Network (CNN) to classify images as **Cat** or **Dog**.

## 📌 Project Overview

This project builds a CNN-based binary image classifier using the **Microsoft Cats vs Dogs dataset**.

The model was trained to recognize visual patterns from cat and dog images and predict the class of previously unseen images.

The project also includes:

* Image preprocessing
* Train/test splitting
* Data augmentation
* Dropout regularization
* Model evaluation
* Confusion matrix
* Classification report
* Prediction on new images
* Model saving and loading

## 📊 Dataset

The dataset contains **23,410 images**.

The classes are:

* `0` → Cat
* `1` → Dog

The dataset was split into:

* **Training:** 18,728 images
* **Testing:** 4,682 images

The split used:

```python
test_size=0.2
seed=42
```

## 🛠️ Technologies Used

* Python
* TensorFlow
* Keras
* NumPy
* Matplotlib
* Scikit-learn
* Hugging Face Datasets
* Jupyter Notebook

## 🔄 Image Preprocessing

Each image was:

1. Converted to RGB
2. Resized to `128 × 128`
3. Converted into a NumPy array
4. Normalized from `0–255` to `0–1`

Example:

```python
image = image.resize((128, 128))
image = np.array(image, dtype=np.float32)
image = image / 255.0
```

## 🧠 CNN Architecture

The final model uses:

```text
Input (128 × 128 × 3)
        ↓
Data Augmentation
        ↓
Conv2D (32 filters)
        ↓
MaxPooling
        ↓
Conv2D (64 filters)
        ↓
MaxPooling
        ↓
Flatten
        ↓
Dense (128 neurons)
        ↓
Dropout (0.5)
        ↓
Dense (1 neuron, Sigmoid)
```

### Data Augmentation

The model uses:

* Random horizontal flipping
* Random rotation
* Random zoom

This helps the model learn from slightly different versions of training images.

### Dropout

A dropout rate of `0.5` was used before the final classification layer to help reduce overfitting.

## ⚙️ Model Compilation

```python
model.compile(
    optimizer="adam",
    loss="binary_crossentropy",
    metrics=["accuracy"]
)
```

## 📈 Model Performance

The final model achieved:

**Test Accuracy: 79.07%**

### Confusion Matrix

```text
[[1833  502]
 [ 478 1869]]
```

Where:

```text
                Predicted
              Cat      Dog

Actual Cat   1833     502
Actual Dog    478    1869
```

### Classification Report

| Class        | Precision | Recall | F1-score |  Support |
| ------------ | --------: | -----: | -------: | -------: |
| Cat          |      0.79 |   0.79 |     0.79 |     2335 |
| Dog          |      0.79 |   0.80 |     0.79 |     2347 |
| **Accuracy** |           |        | **0.79** | **4682** |

## 🧪 Testing on New Images

After evaluating the test dataset, the model was also tested using new cat and dog images that were not part of the original test set.

The model successfully predicted the new images correctly.

Example prediction:

```text
Dog probability: 0.9935634
Prediction: Dog
```

## 💾 Saving the Model

The trained model was saved using:

```python
model.save("cat_dog_model.keras")
```

The saved model was then loaded again:

```python
loaded_model = tf.keras.models.load_model("cat_dog_model.keras")
```

The loaded model produced the same prediction on the test image, confirming that the saved model could be reused.

## 📁 Project Structure

```text
cat-dog-classifier/
│
├── cat_dog_classifier.ipynb
├── cat_dog_model.keras
├── README.md
├── requirements.txt
└── .gitignore
```

The original image dataset is **not included** in the repository because it is unnecessary for running the project notebook and would make the repository unnecessarily large.

## 🚀 How to Run

### 1. Clone the repository

```bash
git clone <your-repository-link>
```

### 2. Install dependencies

```bash
pip install tensorflow numpy matplotlib scikit-learn datasets pillow
```

### 3. Open the Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
cat_dog_classifier.ipynb
```

### 4. Run the notebook

Run the cells in order to:

* Load the dataset
* Preprocess images
* Create the CNN
* Train the model
* Evaluate the model
* Generate predictions

## 🎯 Key Learning Outcomes

Through this project, I practiced:

* CNN-based image classification
* Image preprocessing
* Normalization
* TensorFlow `tf.data`
* Data augmentation
* Dropout
* Binary classification
* Model evaluation
* Confusion matrix
* Precision, recall and F1-score
* Saving and loading Keras models
* Prediction on unseen images

## 👨‍💻 Author

**Gobinath**

B.Tech Artificial Intelligence & Data Science

---

⭐ If you find this project useful, feel free to explore the repository.
