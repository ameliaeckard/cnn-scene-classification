# Image Classification Experiments

This project explores several approaches to improving image classification performance, beginning with a simple baseline model and progressing to transfer learning with a pretrained ResNet18.

The goal was to evaluate how changes to the input representation, data augmentation, and model architecture affected validation performance.

## Experiments

| Experiment | What changed? | Why did I try it? | Validation Accuracy | What did I learn? |
|---|---|---|---:|---|
| Baseline | Starter TNet | Establish a baseline and verify the training pipeline | 49.79% | The baseline provided a useful reference point, but classification performance was limited. |
| Experiment 1 | Training images ×4: original, horizontal flip, vertical flip, and horizontal + vertical flip | Test whether increased spatial variation would reduce overfitting | 47.08% | Four-way flip augmentation did not improve generalization. Vertical flips may also introduce unrealistic scene orientations. |
| Experiment 2 | RGB images instead of grayscale | Determine whether color provides useful information for classification | 51.88% | Color provided useful information and slightly improved performance, but the model still showed limited generalization. |
| Final Model | ImageNet-pretrained ResNet18 with RGB input and transfer learning | Use pretrained visual features and a stronger architecture rather than learning all image features from scratch | **89.79%** | Transfer learning produced the largest improvement. Pretrained visual representations generalized substantially better than the Starter TNet. |

## Final Model

The final approach uses a pretrained ResNet18 model with RGB images.

Instead of training an entire convolutional neural network from scratch, the model begins with visual features learned from ImageNet. The final classification layer is adapted for this project's classes and then trained on the project dataset.

This resulted in a best validation accuracy of:

**89.79%**

Training performance improved steadily over 20 epochs. Validation performance began stabilizing around 88–90%, while training loss continued decreasing.

Example final training output:

```text
Epoch 16/20 | train loss 0.2156 | val loss 0.3421 | val acc 0.8854
Epoch 17/20 | train loss 0.2086 | val loss 0.3330 | val acc 0.8875
Epoch 18/20 | train loss 0.1877 | val loss 0.3360 | val acc 0.8979
Epoch 19/20 | train loss 0.1837 | val loss 0.3331 | val acc 0.8854
Epoch 20/20 | train loss 0.1808 | val loss 0.3358 | val acc 0.8812

Best validation accuracy: 0.8979
