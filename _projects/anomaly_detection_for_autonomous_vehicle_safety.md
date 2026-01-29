---
layout: project
title: "Anomaly Detection For Autonomous Vehicle Safety"
# description: "This work develops a real-time pipeline for anomaly detection for autonomous vehicle safety, leveraging the ‘world understanding’ in Large Language Models (LLMs) for edge-case reasoning."
description: "Research project on real-time anomaly detection pipeline for autonomous vehicles using Vision-Language Models (VLMs) and advanced model optimization techniques."
date: 2025-12-20
categories: [Anomaly Detection, Vision Language Models] #, Large Language Models, Machine Learning, Robotics, Computer Vision]
skills: [Anomaly Detection, Vision Language Models, Large Language Models, Machine Learning, Robotics, Computer Vision, PyTorch, Python]
featured_image: "/assets/images/projects/anomaly_det/output_20s_40s_4x_half.gif"
# github_url: ""
# demo_url: ""
interactive_plot: false

overview: "Autonomous Vehicles (AVs) often struggle with 'semantic anomaly' scenarios, such as mistaking a stop sign on a billboard for a real traffic signal, because these out-of-distribution scenes and context fall outside the narrow scope of traditional training data. We can leverage the much broader 'world understanding' in Vision Language Models (VLMs) and Large Language Models to reason about these edge cases and make more human-like decisions in AVs. However, VLMs are computationally expensive and not suitable for real-time applications out of the box.

<br> <br>

This project developed a real-time inference pipeline for anomaly detection using a VLM backbone. By combining quantization, prompt engineering, and the accelerated FP4 computation on the new Nvidia Blackwell architecture, we achieved  500ms end-to-end processing time, an 80% reduction in reasoning time. This significant improvement brings VLMs closer to real-time applications in AVs."

gallery:
  - type: "image"
    file: "/assets/images/projects/anomaly_det/output_20s_40s_4x.gif"
    description: "Example anomaly reasoning on the Harzard Perception Dataset (4x Speed)"
  - type: "video"
    file: "assets/images/projects/anomaly_det/output_1m30s_1m47s.webm"
    description: "Example anomaly reasoning on the Harzard Perception Dataset"
  - type: "video"
    file: "assets/images/projects/anomaly_det/stu_small_object_10s_15s.webm"
    description: "Example anomaly reasoning on the 'Spotting the Unexpected' dataset capturing small object anomalies"
---

<!-- ## Project Overview -->

<!-- Autonomous Vehicles often struggle with edge-case scenerios, when the vehicle encounters out-of-distribution objects (objects that were never seen during training). Self driving cars have been shown to be susceptible to fooling e.g., a stop sign on a billboard or pedestrian shirts, a traffic light on a truck, etc. This semantic Anomalies are challenging for traditional ML systems due to the limited domain of the training data. We can leverage the much broader 'world understanding' in Vision Language Models to reason about this edge-cases and make more human-like decisions in AVs. However, VLMs are computationally expensive and not suitable for real-time applications out of the box. -->

<!-- This project developed a real-time inference pipeline for anomaly detection using a VLM backbone. By combining quantization, prompt engineering, and the accelerated FP4 computation on the new Nvidia Blackwell architecture, we achieved  500ms end-to-end processing time, a significant improvement bringing VLMs closer for real-time applications in AVs. -->

# Methodology 

## Semantic Reasoning
To address the "semantic gap" where traditional AV pipelines fail to understand context (e.g., distinguishing a stop sign on a billboard from a real signal), we used the NVIDIA Cosmos-Reason1-7B Vision-Language Model (VLM). This model provides zero-shot reasoning capabilities, allowing the system to analyze complex, out-of-distribution scenes and classify them as "Normal" or "Anomaly".

## Datasets
STU Dataset
Harzard Perception Dataset
...video stream as a camera stream would be handled in the real vehicle.

## Temporal Reasoning
Unlike traditional systems that rely on static snapshots, our pipeline captures dynamic anomalies that unfold over time using a video-based approach. We implemented a sliding window technique with a window size of 50 frames and a step size of 20 frames. This allows the model to maintain temporal context, ensuring that motion-based irregularities and evolving hazards are detected effectively.

## Input and Generated Token Budgeting
To transition large VLMs from research to real-time application, we strictly budgeted computational resources.

Input Optimization: Video inputs are downsampled to 4 FPS and resolutions reduced (e.g., 384x242 or 250x250) to minimize the data load.

Token Budgeting: We restricted the maximum generated tokens to 5. By forcing the model to output concise binary classifications or brief justifications, we significantly reduced the inference latency typically associated with autoregressive text generation.

## Quantization
To further reduce memory footprint and accelerate inference, we applied 4-bit and 8-bit quantization techniques to the VLM backbone. This compression allowed the massive parameter set of the Cosmos-Reason1-7B model to run efficiently on edge-grade hardware without a catastrophic loss in reasoning accuracy, contributing directly to our <500ms inference time target.

## Hardware
The project leveraged a heterogeneous hardware stack to handle simulation, training, and inference:

Compute: We utilized Vast.ai for decentralized cloud computing to access high-performance GPUs.

GPUs: Initial testing was conducted on NVIDIA RTX 4080 units (1.5s latency), while final optimization and real-time validation (500ms latency) utilized the NVIDIA RTX 5090.

# Tools and Libraries
- **Simulation & Environment:** CARLA Simulator (Synthetic data generation, edge-case modeling)

- **AI Models:** NVIDIA Cosmos-Reason1-7B (VLM), Isolation Forest (Unsupervised Learning), Autoencoders

- **Algorithms:** Fully-Convolutional Data Description (FCDD), PatchCore

- **Optimization:** FlashAttention2 (Memory I/O acceleration), 4-bit/8-bit Quantization

- **Compute Platform:** Vast.ai (Decentralized Cloud Computing)

- **Hardware:** NVIDIA RTX 5090, RTX 4080