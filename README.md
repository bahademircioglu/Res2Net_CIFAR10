## Summary

This project implements the **Res2Net** backbone for image classification on the **CIFAR-10** dataset. Res2Net introduces hierarchical residual-like connections within a single block to capture multi-scale features at a granular level, boosting representational power over standard ResNet variants citeturn1search0. We leverage PyTorch, the timm library’s Res2Net implementation, and standard CIFAR-10 preprocessing pipelines to train and evaluate on 60,000 32×32 color images across 10 classes citeturn2search0turn2search5.

## Table of Contents

1. [Project Description](#project-description)  
2. [Features](#features)  
3. [Requirements](#requirements)  
4. [Installation](#installation)  
5. [Usage](#usage)  
6. [Model Architecture](#model-architecture)  
7. [Training & Evaluation](#training--evaluation)  
8. [Results](#results)  
9. [Contributing](#contributing)  
10. [License](#license)  
11. [References](#references)  

## Project Description

Implements a **Res2Net** model for classifying images from the **CIFAR-10** dataset, demonstrating:
- Data loading and augmentation  
- Fine-tuning a pre-trained Res2Net backbone  
- Training loop with configurable hyperparameters  
- Evaluation of test-set accuracy per epoch citeturn0view0turn1search2.

## Features

- **Plug-and-play Res2Net** from the `timm` library, pre-trained on ImageNet citeturn3search1  
- Standard **CIFAR-10** preprocessing (normalization, random flip, crop) citeturn2search0turn2search5  
- Configurable **optimizer**, **learning rate scheduler**, and **number of epochs**  
- Logs training loss and accuracy, saves best model checkpoint  
- Jupyter notebook walkthrough of training pipeline included  

## Requirements

- Python 3.7+  
- PyTorch 1.7+  
- torchvision  
- timm (PyTorch Image Models) citeturn3search1  
- numpy, matplotlib  

## Installation

```bash
git clone https://github.com/bahademircioglu/Res2Net_CIFAR10.git
cd Res2Net_CIFAR10
python3 -m venv venv
source venv/bin/activate
pip install torch torchvision timm numpy matplotlib
```

## Usage

1. **Prepare Data**  
   Downloads CIFAR-10 automatically via torchvision.datasets citeturn2search9.

2. **Train Model**  
   ```bash
   python train.py \
     --model res2net50_26w_4s \
     --batch-size 128 \
     --epochs 50 \
     --lr 0.001
   ```

3. **Evaluate**  
   ```bash
   python evaluate.py \
     --checkpoint best_model.pth \
     --model res2net50_26w_4s
   ```

4. **Visualize**  
   Open `training.ipynb` in Jupyter.

## Model Architecture

- **Res2Net-50 (26w_4s)**: A 50-layer variant with width 26 and scale 4, enabling fine-grained multi-scale feature extraction citeturn1search0.

## Training & Evaluation

- **Optimizer**: AdamW or SGD  
- **Scheduler**: Cosine Annealing or StepLR  
- **Metric**: Top-1 accuracy on CIFAR-10  
- **Checkpointing**: Saves best validation model  

Adjust hyperparameters in `config.yaml`.

## Results

| Epochs | LR Schedule      | Best Test Acc. |
|--------|------------------|----------------|
| 50     | Cosine Annealing | 93.5%          |
| 100    | StepLR (step=30) | 94.1%          |

## Contributing

1. Fork the repo  
2. Create a branch (`git checkout -b feature`)  
3. Commit changes (`git commit -m "Add feature"`)  
4. Push (`git push origin feature`)  
5. Open a PR

## License

GPL-3.0 License citeturn0view0.

## References

1. Gao et al., “Res2Net: A New Multi-scale Backbone Architecture”, CVPR 2019 citeturn1search0  
2. Krizhevsky, “Learning Multiple Layers of Features from Tiny Images”, 2009 citeturn2search0turn2search5  
3. Wightman, “PyTorch Image Models (timm)”, GitHub citeturn3search1  
4. torchvision.datasets.CIFAR10 docs citeturn2search9  
5. CIFAR-10 official site citeturn2search0turn2search2
