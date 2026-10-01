# Targeted Adversarial PGD Attack on MobileNetV2 using Keras & OpenCV

This repository contains a pure implementation of a **Targeted PGD (Projected Gradient Descent)** adversarial attack on a deep convolutional neural network (MobileNetV2 pre-trained on ImageNet). 

The goal of this project is to demonstrate the vulnerability of computer vision models to subtle, human-imperceptible pixel perturbations.
## How It Works
Unlike standard model training where weights are updated to minimize loss, this script freezes the model weights and iteratively updates the **input image pixels** to minimize the loss toward a specific, incorrect target class. 
* **Source Class:** Tabby Cat (ID: 281)
* **Target Class:** Lemon (ID: 951)
* **Method:** Iterative PGD with `alpha=0.002` and `epsilon=0.02` constraints to ensure the noise remains invisible to the human eye.

## Visual Results
Inside the iterative loop, the model's confidence shifts dramatically within 30 steps:
* **Step 1:** Model sees a **Cat** (100% confidence).
* **Step 20:** Model sees a **Lemon** (88.63% confidence), while visually the image remains an identical cat.

<img width="456" height="224" alt="image" src="https://github.com/user-attachments/assets/f42ac2b2-f4e1-4045-be93-98cf53e4fbe4" />






## Core Tech Stack
* **Framework:** TensorFlow / Keras (utilizing `tf.GradientTape` for manual backpropagation to pixel inputs)
* **Image Processing:** OpenCV (`cv2`) for precise BGR/RGB conversions and metadata-safe PNG exporting.
* **Visualization:** Matplotlib

## Key Takeaways for AI Safety
This experiment serves as a Proof of Concept (PoC) for auditing ML models. Understanding these mathematical flaws allows engineers to build defenses, such as **Adversarial Training**, to make production-ready systems safe against manipulation.
