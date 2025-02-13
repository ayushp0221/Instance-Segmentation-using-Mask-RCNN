# Instance-Segmentation-using-Mask-RCNN

## Project Overview

This project implements **Mask R-CNN** for **instance segmentation**, specifically detecting and segmenting objects like **trash cans** and **poles** in a campus environment. The model builds on **Faster R-CNN** by adding a mask prediction branch, enabling **pixel-level segmentation**.

## Dataset

- **Total Images:** 200 (Trash cans & Poles)  
- **Annotation Tool:** Roboflow  
- **Format:** COCO JSON  

### Splits:
- **Training:** 80% (160 images)  
- **Validation:** 10% (20 images)  
- **Test:** 10% (20 images)  
- **Augmentation:** Random horizontal flipping  
- **Normalization:** ImageNet mean & standard deviation  

## Model Architecture

- **Backbone:** ResNet-50 + Feature Pyramid Network (FPN)  
- **Region Proposal Network (RPN):** Proposes candidate object regions  
- **RoI Align:** Ensures pixel-level precision  

### Heads:
- **Box Classification:** Object class prediction  
- **Box Regression:** Bounding box refinement  
- **Mask Prediction:** Pixel-wise segmentation  

## Custom Modifications

- **Transfer Learning:** Pretrained on COCO dataset  
- **Class Customization:** Trained for **2 classes** (Trash Can, Pole)  
- **Adjustments:**  
  - `FastRCNNPredictor` → Adjusted for **3 categories** (Background, Trash Can, Pole)  
  - `MaskRCNNPredictor` → Configured for custom classes  

## Training Details

### Loss Functions:
- **Classification Loss:** Cross-entropy  
- **Bounding Box Loss:** Smooth L1  
- **Mask Loss:** Binary cross-entropy  

### Hyperparameters:
- **Learning Rate:** 0.0001  
- **Batch Size:** 8  
- **Epochs:** 20  
- **Optimizer:** Adam  
- **Scheduler:** StepLR (step size = 5, gamma = 0.1)  

## Evaluation Metrics

- **IoU (Intersection over Union):** Measures segmentation quality  
- **mAP (Mean Average Precision):** Assesses model performance  
- **Accuracy:** Measures correct class predictions  

## Results

| **Metric**  | **Before Training** | **After Training** |
|------------|-----------------|----------------|
| **Mean IoU** | 0.05            | **0.61**      |
| **mAP**      | 0.02            | **0.021**     |
| **Accuracy** | 0.10            | **0.86**      |

## Visualization

- **Pre-training:** Poor object detection  
- **Post-training:** Significant improvement in segmentation  

## Conclusion

This project successfully implements **Mask R-CNN** for instance segmentation in a custom dataset.
- The **IoU and mAP curves** suggest effective learning.  
- **Accuracy plateaued around 85%**, indicating reliable object classification.  
 
