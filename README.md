# Deep-Learning
Convolution, padding, and stride  CNN architectures  Representation learning and transfer learning  Convolution implemented from scratch with NumPy  Transfer learning with a pretrained ResNet18 using frozen layers and fine-tuning
Student Name: Jilkapally Praneeth Teja
Course: CS5720 Neural Network and Deep Learning
Semester: Fall 2026

Part II - Programming

Question 1 - Implement Convolution from Scratch

Objective

The purpose of this task is to implement a 2-D convolution/filtering operation using NumPy without using a built-in convolution function.

Input

The program uses the following 5 x 5 input matrix:

1 1 1 0 0
0 1 1 1 0
0 0 1 1 1
0 0 1 1 0
0 1 1 0 0

The 3 x 3 filter is:

1 0 1
0 1 0
1 0 1

The program uses:

Stride = 1
Padding = 0

What the program does

The code:

stores the input and filter using NumPy arrays

slides the filter over the input matrix

computes the dot product at every valid location

creates the output feature map

prints the output feature map

prints the output shape

Output

The output feature map is:

[[4 3 4]
 [2 4 3]
 [2 3 4]]

Output shape:

(3, 3)

Question: What happens if the stride changes from 1 to 2?

With stride 1, the filter moves one position at a time. When the stride is changed to 2, the filter moves two positions at a time. Because the filter makes fewer valid movements across the input, fewer output values are calculated. Therefore, the output feature map becomes smaller.

Question 2 - Transfer Learning: Freeze vs. Fine-Tune

Objective

This task compares two transfer-learning approaches using a pretrained CNN.

The implementation uses:

Pretrained Model: ResNet18
Dataset: CIFAR-10
Classes: Cat and Dog

The original CIFAR-10 labels are converted as follows:

Cat = 0
Dog = 1

Images are resized to 224 x 224 so they can be used with the pretrained ResNet18 model.

Experiment A - Feature Extraction

For Experiment A:

Load the pretrained ResNet18.

Freeze the pretrained convolutional/base layers.

Replace the original classification layer with a 2-class classifier.

Train only the new classifier.

The purpose of this experiment is to use the pretrained network as a fixed feature extractor.

Trainable Parameters

Only the final classifier is trainable.

The ResNet18 final layer has 512 input features and 2 output classes:

512 x 2 + 2 = 1026

Therefore, the expected number of trainable parameters is:

1026

Experiment B - Fine-Tuning

For Experiment B:

Start with the pretrained ResNet18.

Freeze the earlier layers.

Unfreeze the final convolutional block (layer4).

Keep the new final classifier trainable.

Train the unfrozen layers and classifier.

This allows the higher-level pretrained features to adapt to the cat-versus-dog dataset.

Required Comparison

Both experiments use the same number of epochs.

The program records:

trainable parameters

training time

test accuracy

training loss

Results :
FINAL COMPARISON
============================================================

Experiment A: Frozen Feature Extractor
Trainable Parameters: 1026
Training Time: 178.98 seconds
Test Accuracy: 76.75%

Experiment B: Fine-Tuning
Trainable Parameters: 8394754
Training Time: 243.93 seconds
Test Accuracy: 85.75%

============================================================
ASSIGNMENT RESULTS
============================================================
Method                           Parameters   Time (sec)     Accuracy
----------------------------------------------------------------------
Frozen Feature Extractor               1026       178.98       76.75%
Fine-Tuned Network                  8394754       243.93       85.75%

Loss plot saved as: transfer_learning_loss.png
