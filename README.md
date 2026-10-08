# CNN Scene Classification _(cnn-scene-classification)_

Lab report: [CNN Scene Classification](https://lab.ameliaeckard.com/notes/2026-09-26-cnn-scene-classification)

A 16-class scene-recognition study comparing CNN baselines, preprocessing, augmentation, and transfer learning.

## Background

This project tests how representation and architecture choices affect scene classification on 2,400 images. Early experiments exposed limited generalization; transfer learning with ImageNet-pretrained ResNet18 produced the strongest result.

## Install

```bash
git clone https://github.com/ameliaeckard/cnn-scene-classification.git
cd cnn-scene-classification
pip install -r requirements.txt
```

## Usage

Open the notebook under `notebooks/`, point `PROJECT_ROOT` at the dataset, and run the cells from top to bottom.

```text
train/
  class_01/
  ...
test/
  class_01/
  ...
```

## Results

| Experiment | Validation accuracy |
| --- | ---: |
| Baseline TNet | 49.79% |
| Four-way flip augmentation | 47.08% |
| RGB input | 51.88% |
| ResNet18 transfer learning | **89.79%** |

Final test accuracy: **90.25%**.

The final model uses ImageNet-pretrained ResNet18 with a frozen convolutional backbone and a new 16-class head.

## Maintainer

[Amelia Eckard](https://github.com/ameliaeckard)

## Contributing

Issues are welcome for bugs or documentation problems. Please open an issue before a substantial pull request.
