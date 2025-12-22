# Automated Oral Cavity Image Classification and Analysis
### DH 307 R&amp;D Project, IIT Bombay
#### Guide: [Prof. Nirmal Punjabi](https://www.kcdh.iitb.ac.in/people/faculty/kcdh-faculty), IIT Bombay
---
This project implements a full deep learning pipeline for **oral cavity image classification** using the **Piyarathne et al. Oral Cavity dataset**. The goal is to classify images into **Healthy**, **OCA**, and **OPMD** categories using modern CNN and Transformer-based architectures.

## **Overview**

* Built a complete pipeline for **data preprocessing** and **image classification**.
* Used segmentation annotations to extract **tight oral cavity crops**, improving model focus and reducing background noise.
* Trained and fine-tuned multiple backbone architectures:

  * **ResNet18, ResNet50**
  * **DenseNet121**
  * **EfficientNet-B0, EfficientNet-B3**
  * **ViT-b-16**
  * **ConvNeXt-Tiny**


## **Methodology**

### **1. Preprocessing & ROI Extraction**

* Used provided segmentation polygons to extract the **oral cavity region** using mask-based cropping.
* Cropped regions were then resized to a fixed target size(224x224) for model input.

### **2. Model Training**

* Fine-tuned multiple architectures using PyTorch.
* Techniques used:

  * **Weighted Cross-Entropy Loss** (handles class imbalance)
  * **AdamW optimizer**
  * **CosineAnnealingLR Scheduler**
  * **Learning rate tuning** (1e-4 found optimal)
  * **Early stopping** based on validation accuracy
  * **Evaluation on separate validation & test splits**


## **Results**

### **Best Model: "_ConvNeXt-Tiny_"**

  * **Validation Accuracy:** 74.3%
  * **Test Accuracy:** 69.8%
  * **Macro Avg F1 Score:** 0.68

* **Class-wise F1 Scores:**

    * **Healthy:** 0.74
    * **OCA:** 0.62
    * **OPMD:** 0.67

### **Model Comparison Summary**

| Model           | Val Acc (%) | Test Acc (%) |
| --------------- | ----------- | ------------ |
| ResNet18        | 68.4        | 66.7         |
| ResNet50        | 67.9        | 65.3         |
| DenseNet121     | 66.2        | 68.0         |
| EfficientNet-B0 | 70.9        | 66.7         |
| EfficientNet-B3 | 68.4        | 63.1         |
| ViT-b-16        | 67.9        | 68.0         |
| ConvNeXt        | **74.3**    | **69.8**     |




#### **Dataset**

N.S. Piyarathne, S.N. Liyanage, R.M.S.G.K. Rasnayaka, P.V.K.S. Hettiarachchi, G.A.I. Devindi, F.B.A.H. Francis, D.M.D.R. Dissanayake, R.A.N.S. Ranasinghe, M.B.D. Pavithya, I.B. Nawinne, R.G. Ragel, R.D. Jayasinghe, “A comprehensive dataset of annotated oral cavity images for diagnosis of oral cancer and oral potentially malignant disorders,” Oral Oncology, vol. 156, p. 106946, 2024. (https://doi.org/10.1016/j.oraloncology.2024.106946)





