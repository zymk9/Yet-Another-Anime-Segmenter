# Yet-Another-Anime-Segmenter

![sample1](./sample/64535234_p0_seg.jpg)
Instance segmentation for anime characters based on [CondInst](https://arxiv.org/abs/2003.05664) and [SOLOv2](https://arxiv.org/abs/2003.10152), using the implementation from [AdelaiDet](https://github.com/aim-uofa/AdelaiDet) and [detectron2](https://github.com/facebookresearch/detectron2).

Many thanks to [AniSeg](https://github.com/jerryli27/AniSeg) created by jerryli27, as part of the dataset originates from the segmentation data provided in this [repo](https://github.com/jerryli27/AniSeg#about-the-models). The rest of the dataset is retrieved from [Pixiv](https://www.pixiv.net/) and manually annotated.

A model based on SOLOv2 had been added, which generally outperforms previous CondInst model. Evaluation results may be added soon.

Newer version of the model is still under development, stay tuned if you are interested.

## Usage
### Installation
Both AdelaiDet and detectron2 are required. Please refer to the official guide from [AdelaiDet](https://github.com/aim-uofa/AdelaiDet#installation) and [detectron2](https://github.com/facebookresearch/detectron2/blob/master/INSTALL.md). A [Colab tutorial](https://colab.research.google.com/drive/1d49vI0lS2MKHx-j5VVnzPUhpRrNjueHI?usp=sharing) is provided.

### Inference
1. Download the pretrained model and use the corresponding config file.
   * CondInst: [model weights](https://drive.google.com/file/d/1-AmeAiTrtaPcNLUnRAovpveMkSxxpkKQ/view?usp=sharing), [config](./configs/CondInst.yaml).
   * SOLOv2: [model weights](https://drive.google.com/file/d/1-wFdQ4jwSTeJ7wGD3YKNJdcpSS5Ho8c9/view?usp=sharing), [config](./configs/SOLOv2.yaml).

2. Run inference with
   ```bash
    python AdelaiDet/demo/demo.py \
        --config-file path/to/config.yaml \
        --input input1.jpg input2.jpg \
        --opts MODEL.WEIGHTS path/to/pretrained/model
   ```
## Training and Results
Training using transfer learning from [pretrained models](https://github.com/aim-uofa/AdelaiDet/tree/master/configs/SOLOv2) on COCO Instance Segmentation. Parameters can be found in the [config file](./configs/SOLOv2.yaml).

Dataset is augmented by placing segmentations on pure backgrounds. Models are trained with multi-scale augmentation.

![sample2](./sample/52206792_p0_seg.jpg)
![sample3](./sample/64113607_p0_seg.jpg)
