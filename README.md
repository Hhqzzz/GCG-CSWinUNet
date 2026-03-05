# GCG-CSWinUNet
## Abstract
Accurate and automatic medical image segmentation is critical for computer-aided diagnosis. Although Transformer-based architectures have achieved significant progress by modeling long-range dependencies, they often struggle with preserving fine-grained local textures and distinguishing morphologically similar anatomical structures. In this paper, based on the successful segmentation model CSWin-UNet, we propose a novel framework GCG-CSWinUNet (Global guided and Cross-level Gating CSWinUNet), which contains two core components: a global Dense 2D Learnable Positional Encoding (D-LPE) and a Cross-level Jumping Attention Feature Fusion (CJAFF) scheme. Our D-LPE assigns unique and learnable parameters to dense ($4 \times 4$) local regions. This encoding mechanism can provide fine-grained anatomical priors, equipping the model to adapt to the spatial coordinate systems of different segmentation tasks. Meanwhile, the CJAFF scheme utilizes a jumping attention-guided mechanism to bridge the semantic gap between high-level semantic features and low-level structural details, which can effectively alleviate information loss during the decoding phase. Extensive experiments demonstrate the model demonstrated the competitive performance of the proposed model. Moreover, our model complexity analysis indicates that our model maintains a competitive parameter count and computational efficiency.
## Installation
```
CUDA 11.8 / Python 3.8 / PyTorch 2.0.0 / Nvidia 2080 GPU
```
## Prepare Data
[Synapse dataset](https://drive.google.com/file/d/1BvpY0g9mKkkhdHpAX1HqDw8iTJNbFuwq/view)

[ACDC dataset](https://humanheart-project.creatis.insa-lyon.fr/database/#collection/637218c173e9f0047faa00fb)

[ISIC2017 dataset](https://challenge.isic-archive.com/data/#2017)
## Train/Test
### Train
```
python train.py --dataset Synapse --cfg configs/cswin_tiny_224_lite.yaml --root_path your DATA_DIR --max_epochs 150 --output_dir your OUT_DIR  --img_size 224 --base_lr 0.05 --batch_size 24
```
### Test
```
python test.py --dataset Synapse --cfg configs/cswin_tiny_224_lite.yaml --is_saveni --volume_path your DATA_DIR --output_dir your OUT_DIR --max_epoch 150 --base_lr 0.05 --img_size 224 --batch_size 24
```
