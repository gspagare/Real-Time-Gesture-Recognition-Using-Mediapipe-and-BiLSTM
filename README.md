# Real-Time Gesture Recognition Using Mediapipe and LSTM

## Description

This project implements a real-time gesture recognition system that uses the Mediapipe library for detecting and extracting keypoints and a Bidirectional LSTM neural network for classifying gestures. The system is designed to work with live video input from a webcam, making it suitable for various applications such as sign language recognition, human-computer interaction, and more. The entire implementation is provided in a Jupyter Notebook.

## Table of Contents
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Model Architecture](#model-architecture)

## Features
- Real-time video capture and processing.
- Keypoint detection for face, pose, and hands using Mediapipe.
- Motion detection to improve prediction accuracy.
- Gesture classification using a Bidirectional LSTM neural network.
- Visualization of detected landmarks and predicted gestures.

## Installation

1. **Clone the repository**:
    ```bash
    git clone https://github.com/yourusername/real-time-gesture-recognition.git
    cd real-time-gesture-recognition
    ```

2. **Create and activate a virtual environment**:
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. **Install the required dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

4. **Download Mediapipe models and setup the environment**:
    - Ensure you have the necessary Mediapipe models and configurations in place.

## Usage

1. **Run the Jupyter Notebook**:
    ```bash
    jupyter notebook gesture_recognition.ipynb
    ```

2. **Follow the instructions within the notebook** to perform live gesture recognition.

## Model Architecture

The neural network used in this project is a Bidirectional LSTM with the following architecture:

```plaintext
Input Shape: (30, 1668)
    ┌───────────────────────────┐
    │    Input Layer            │
    │  Shape: (30, 1668)        │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ BiLSTM Layer 1            │
    │  Units: 128               │
    │  Activation: sigmoid      │
    │  Return sequences: True   │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ Dropout Layer 1           │
    │  Rate: 0.1                │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ BiLSTM Layer 2            │
    │  Units: 64                │
    │  Activation: sigmoid      │
    │  Return sequences: True   │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ Dropout Layer 2           │
    │  Rate: 0.1                │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ BiLSTM Layer 3            │
    │  Units: 32                │
    │  Activation: sigmoid      │
    │  Return sequences: False  │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ Dense Layer 1             │
    │  Units: 128               │
    │  Activation: sigmoid      │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ Dropout Layer 3           │
    │  Rate: 0.1                │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ Dense Layer 2             │
    │  Units: 64                │
    │  Activation: sigmoid      │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ Dropout Layer 4           │
    │  Rate: 0.1                │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │ Dense Layer 3             │
    │  Units: 10                │
    │  Activation: softmax      │
    └───────────────────────────┘
                │
                ▼
    ┌───────────────────────────┐
    │    Output Layer           │
    │  Shape: (10,)             │
    └───────────────────────────┘
