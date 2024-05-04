# Explainability with Saliency Maps

This project explores various techniques for visualizing and understanding the decision-making process of Convolutional Neural Networks (CNNs) using saliency maps. The main focus is on the Saliency Mapping technique, which highlights the regions of an image that contribute the most to the CNN's output prediction.

Saliency maps in deep learning were first witnessed in the paper titled Deep Inside Convolutional Networks: Visualising Image Classification Models and Saliency Maps: https://arxiv.org/abs/1312.6034. Our project is an implementation of the image-specific Class Saliency Visualisation method described in this paper.

## Motivation

Despite the excellent performance of CNNs in computer vision tasks, understanding why they perform well has been a challenge. Visualizing the parameters and extracted features of CNNs can provide useful insights into their internal workings. This project aims to improve the explainability and interpretability of CNNs through visualization techniques.

## Techniques

### Class-Based Image Generation

This technique helps visualize how a neural network "sees" a particular class by optimizing a random input image to maximize the logits (output values) corresponding to a specific class.

### Guided Backpropagation

This method visualizes the features extracted in the convolutional layers of the CNN. It performs a forward pass until the layer of interest and then backpropagates the gradients in a "guided" fashion, considering only positive gradients and corresponding positive input values.

### Saliency Mapping

Saliency mapping identifies the parts of an image that are most important for a CNN's decision. It generates a heatmap that highlights the regions of the image that contributed the most to the output. The technique involves the following steps:

1. Forward Pass: Calculate the prediction/output of the input image through the model, and extract the score for the target class.
2. Backward Pass: Compute the gradients of the target class score with respect to the input image pixels using backpropagation.
3. Absolute Values: Take the absolute value of each gradient.
4. Max pooling: Find the maximum value over the channels for each pixel to identify the most influential color.
5. Normalization: Normalize the saliency map.
6. Visualization: Visualize the saliency map to show the regions of the image that contribute the most.

## Fast Sign Gradient Attack (FSGA)

The FSGA algorithm is a computationally efficient and successful method for generating adversarial examples. It works by computing the gradient of the loss function with respect to the input image, taking the sign of the gradient, and adding a small perturbation in the direction of the sign of the gradient to the original input image.

## Results

The project presents saliency maps and adversarial examples generated using different CNN architectures (Custom CNN, ResNet18, ResNet50, and VGG16) for various classes like cats, dogs, bears, monkeys, and rabbits. The best result was obtained for ResNet50

ResNet-50

![Resnet_50_CAT](outputs/ResNet50/output1.png)
![Resnet_50_CAT](outputs/ResNet50/output2.png) 
![Resnet_50_CAT](outputs/ResNet50/output3.png)
![Resnet_50_CAT](outputs/ResNet50/output4.png) 
![Resnet_50_CAT](outputs/ResNet50/output5.png)


The ResNet50 architecture likely outperformed the custom CNN, ResNet18, and VGG16 in generating saliency maps due to its greater depth and complexity, the use of residual connections (which facilitate better gradient flow), and its training on the large, diverse, and fine-grained ImageNet dataset. The combination of these factors allowed ResNet50 to learn more robust and detailed features, leading to better identification and highlighting of relevant regions in the input images for saliency map generation.

