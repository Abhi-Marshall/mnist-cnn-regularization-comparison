# MNIST CNN Regularization Comparison

This project performs handwritten digit classification using the MNIST dataset with Convolutional Neural Networks (CNNs), demonstrating and comparing key regularization strategies: **L2 regularization**, **data augmentation**, **dropout**, and their combination. Performance metrics for all approaches are saved in CSV/Excel form.

---

## Dataset

- **MNIST:** 70,000 grayscale images (28x28 pixels) of digits (0-9).
- 60,000 images for training, 10,000 for testing.
- Data is preprocessed and split (70:30) into train and validation sets.

---

## Project Structure

- `notebooks/` : Jupyter notebooks for each experiment
- `models/` : Saved model weights (optional)
- `outputs/` : CSV/Excel files with results
- `README.md` : Project documentation

---

## Model and Regularization Approaches

### 1. **Base CNN Model**
- Two convolution layers with ReLU activation and Average Pooling
- Dense layer with ReLU activation
- Output softmax layer (10 classes)
- Adam optimizer, sparse categorical cross-entropy loss

### 2. **L2 Regularization**
- Adds L2 penalties to convolution and dense layer weights to reduce overfitting.

### 3. **Data Augmentation**
- Uses Keras `ImageDataGenerator` with:
  - random rotation, zoom, width/height shifts
- Feeds novel, augmented batches in each epoch, improving model robustness.

### 4. **Dropout**
- Adds dropout layer after dense layer, randomly zeroing out neurons during training.

### 5. **Combined Regularization**
- Applies **L2 regularization**, **data augmentation**, and **dropout** together for maximal regularization.

---

## How the Algorithm Works

1. **Data Loading and Preprocessing**
   - Loads MNIST dataset, normalizes images, adds channel dimension.
   - Splits training data into train and validation using scikit-learn.

2. **Model Creation**
   - Modular function architecture: each model (`L2`, `Augmentation`, `Dropout`, `Combined`) has its own builder function.
   - Swappable regularization settings.

3. **Training**
   - Trains each model for 5 epochs, using relevant regularization (see above).
   - For augmented models, trains using a Keras data generator.

4. **Evaluation**
   - Evaluates each model on train, validation, and test sets.
   - Records accuracy, loss, and misclassified sample counts.

5. **Results Export**
   - Saves all metrics for all approaches in a summary CSV and Excel file.
   - Metrics are ready for direct comparison, visualization, or reporting.

---
