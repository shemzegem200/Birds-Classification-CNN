# Bird Species Classification - Deep Learning Assignment

## Overview
This project performs multi-class bird species classification using a deep learning approach. The dataset comprises 200 bird categories from the **Caltech-UCSD Birds-200-2011 dataset**, pre-processed into training and testing sets.

## Dataset
- **Source:** Caltech-UCSD Birds-200-2011
- **Total Images:** 11,788
- **Split:** 
  - Training: 8,841 images
  - Testing: 2,947 images
- **Classes:** 200 bird species
- **Image Dimensions:** ~500x500 pixels
- **Format:** JPG
- **Size:** ~1.1 GB

## Model Architecture
- **Input:** RGB images of size 256x256
- **Feature Extractor:** Custom deep residual neural network using BasicBlocks:
  - Each BasicBlock: Two 3×3 convolutional layers, BatchNorm, ReLU, and residual connections
  - Global average pooling followed by a fully connected classifier
- **Classifier:** Fully connected layers with SiLU activations and dropout
- **Output:** 200 class probabilities

## Activation Function
- **SiLU(x) = x ⋅ sigmoid(x)**
- Smooth, differentiable, reduces vanishing gradients, and improves feature richness.

## Training & Evaluation
- **Training Accuracy:** 86.88%
- **Test Accuracy:** 86%
- Smooth loss and accuracy curves demonstrate good generalization without overfitting.
- Final loss converges around 2.1 for both training and validation.

## Visualizations
- **First Layer Filters:** Grid showing diverse learned patterns (edges, textures, color gradients).
- **Feature Maps:** Visual representations of layer-wise activations.

## Experimentation with Filter Configurations
### Small Number of Filters
- Convolutional layers: 32 → 64 → 128 filters
- Faster training, fewer parameters
  
### Fewer Number of Filters
- Convolutional layers: 16 → 32 → 64 filters
- Adaptive Average Pooling ensures fixed output size
- Suitable for rapid prototyping

## Findings
- **Filter Depth Matters More:** More filters improved fine-grained feature representation.
- **Kernel Size Trade-off:** Larger kernels increased computation without consistent accuracy gains.
- **Best Configuration:** The model with more filters achieved the highest test accuracy and stability.

## Conclusion
The model effectively learns useful hierarchical features and generalizes well for bird species classification from images.
