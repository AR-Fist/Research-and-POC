# Research and POC

## Detectron2

### Dependencies & Requirements

Linux or macOS with Python ≥ 3.6

- torch 1.7
- torchvision 0.8.1 + cuda 10.1 (https://pytorch.org/)
- onnx
- caffe2

### Installation

1. `git clone https://github.com/facebookresearch/detectron2.git`
2. `python3 -m pip install -e detectron2`

### Before deployment

Load Datasets from COCO (https://cocodataset.org/#download)

Panoptic Segmentation Case :

```
detectron2/tools/deploy
│
└───datasets/coco
    │
    └───annotations
    │   │   instances_val2017.json (2017 Train/Val annotations [241MB])
    │   
    └───val2017 (2017 Val images [5K/1GB])
    │   │   xxxx.jpg
    │   │   ...
    │
    └───panoptic_stuff_val2017 (2017 Panoptic Train/Val annotations [821MB])
        │   xxxx.jpg
        │   ...

```

### Deployment

This will create **output** folder and protobuff file

1. `cd tools/deploy`
2. ```python3 ./export_model.py --config-file ../../configs/COCO-PanopticSegmentation/panoptic_fpn_R_50_3x.yaml --output ./output --export-method caffe2_tracing --format caffe2 MODEL.WEIGHTS detectron2://ImageNetPretrained/MSRA/R-50.pkl MODEL.DEVICE cpu```
