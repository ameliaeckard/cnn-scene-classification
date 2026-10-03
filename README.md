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

The selected model achieved a final test accuracy of:

**90.25%**

Training performance improved steadily over 20 epochs. Validation performance began stabilizing around 88–90%, while training loss continued decreasing.

Example final training output:

```text
Epoch 16/20 | train loss 0.2156 | val loss 0.3421 | val acc 0.8854
Epoch 17/20 | train loss 0.2086 | val loss 0.3330 | val acc 0.8875
Epoch 18/20 | train loss 0.1877 | val loss 0.3360 | val acc 0.8979
Epoch 19/20 | train loss 0.1837 | val loss 0.3331 | val acc 0.8854
Epoch 20/20 | train loss 0.1808 | val loss 0.3358 | val acc 0.8812

Best validation accuracy: 0.8979

## Reproducing the Experiment

1. Clone this repository.
2. Install the dependencies in `requirements.txt`.
3. Download the assignment dataset.
4. Organize the dataset with `train/` and `test/` directories containing one folder per class.
5. Update `PROJECT_ROOT` in the notebook to point to the local dataset.
6. Run `notebooks/ITCS_6169_8169_Assignment1_2026_Starter.ipynb` from top to bottom.
7. The notebook uses seed 0 and an 80/20 split of the provided training data.
8. The final model uses an ImageNet-pretrained ResNet18 with the convolutional backbone frozen and a new 16-class output layer.

## Final Configuration

- Architecture: ResNet18
- Initialization: ImageNet-1K pretrained weights
- Input: RGB
- Input resolution: 224 x 224
- Training images: 1,920
- Validation images: 480
- Test images: 400
- Batch size: 64
- Optimizer: Adam
- Learning rate: 0.001
- Epochs: 20
- Loss: CrossEntropyLoss
- Random seed: 0
- Pretrained backbone: Frozen
- Trainable layer: Final 512-to-16 fully connected classification layer
- Model selection: Highest validation accuracy
- Best validation accuracy: 89.79%
- Final test accuracy: 90.25%

## Model Checkpoint

The checkpoint used for the final evaluation is:

`resnet18_scene_classifier_best.pth`
