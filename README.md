# Image Classification for Emotion Recognition

This project demonstrates how to build an image classification model for emotion recognition using TensorFlow and Keras. The model is trained on a dataset of facial expressions and can be converted to different formats for deployment. The notebook includes steps for data preparation, model training, evaluation, and inference.

## Table of Contents
1. [Overview](#overview)
2. [Dataset](#dataset)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Model Conversion](#model-conversion)
6. [Inference](#inference)
7. [Results](#results)
8. [License](#license)

## Overview
The project aims to classify facial expressions into six emotion categories:
- Angry
- Happy
- Neutral
- Sad
- Surprise
- Ahegao

The model is built using a pre-trained MobileNetV2 as the base and fine-tuned for emotion recognition. It includes data augmentation, training, evaluation, and conversion to formats like TensorFlow Lite and TensorFlow.js for deployment.

## Dataset
The dataset used for this project is the [Emotion Recognition Dataset](https://www.kaggle.com/datasets/sujaykapadnis/emotion-recognition-dataset). It contains images of facial expressions categorized into different emotion classes.

## Installation
1. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

2. Download the dataset:
   The dataset is downloaded using the `kagglehub` library in the notebook.

## Usage
1. Open the notebook `ImageClassification.ipynb` in your preferred IDE (e.g., PyCharm or Jupyter Notebook).
2. Follow the steps in the notebook:
   - Data preparation
   - Data augmentation
   - Model training
   - Evaluation and visualization
   - Model conversion
   - Inference

3. Run the cells sequentially to train the model and test its performance.

## Model Conversion
The trained model is converted into the following formats for deployment:
- **TensorFlow Lite**: Saved in the `tflite_model` directory.
- **TensorFlow.js**: Saved in the `tfjs_model` directory.
- **SavedModel**: Saved in the `saved_model` directory.

### Conversion Commands
- TensorFlow Lite:
  ```python
  converter_tf_lite = tf.lite.TFLiteConverter.from_keras_model(model)
  tflite_model = converter_tf_lite.convert()
  with open('tflite_model/model.tflite', 'wb') as f:
      f.write(tflite_model)
  ```
- TensorFlow.js:
  ```bash
  tensorflowjs_converter --input_format=keras model.h5 tfjs_model
  ```

## Inference
The notebook includes a sample inference pipeline using the TensorFlow Lite model. To test the model:
1. Provide the path to a test image.
2. Run the `predict_image_tflite` function to get the predicted class and probabilities.

Example:
```python
test_image_path = 'data/final_dataset/test/Angry/sample_image.png'
predicted_class, predictions = predict_image_tflite(test_image_path)
print(f"Predicted class: {predicted_class}")
```

## Results
The model achieved high accuracy on the test set. Below is an example of the output for a test image:
- **Predicted Class**: Angry
- **Predicted Probabilities**:
  ```
  Ahegao: 0.0000
  Angry: 0.9998
  Happy: 0.0000
  Neutral: 0.0001
  Sad: 0.0000
  Surprise: 0.0001
  ```