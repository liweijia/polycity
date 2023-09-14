# PolyCity

## Introduction

This is the official code for the paper entitled '**[Joint Semantic-Geometric Learning for Polygonal Building Segmentation from High-Resolution Remote Sensing Images](https://doi.org/10.1016/j.isprsjprs.2023.05.010)**'.

## Environment

- All the code has been run and tested on Ubuntu 18.04, Python 3.7.4, Pytorch 1.6.0, CUDA 10.1 and GTX 2080Ti GPUs.

- Setup python environment：

```
pip install -r requirements.txt
```

## Usage

### Step1：Building-HRNet

#### Data Preparation

- The dataset we use is [SpaceNet AOI 2 – Las Vegas](https://spacenet.ai/las-vegas/). If you want to use other datasets, you need to prepare the dataset following the format of example data in `building_hrnet/data/example_data` we prepared. 

- The Python script `building_hrnet/BinaryAnnotationGeneration.py` can convert the coco format file into the binary file.

- The MATLAB script `building_hrnet/AnnotationGenerationFromBinary.m`  can convert the binary file into annotation file in the required format and corresponding colormap.

- Modify the data directory in `building_hrnet/files/vegas_train(val)_list.txt` for your machine.

#### Train & Test

Modify the parameters for your machine in `building_hrnet/train(test)_vegas.sh`, then run:

```
For train: sh train_vegas.sh
For test: sh test_vegas.sh
```

#### Post-processing

Modify the data directory in `building_hrnet/generate_vertex_115/select-vertex.sh` and then run it.

### Step2：Polygon-rnnpp

#### Data Preparation

- Download the pre-trained Pytorch Resnet-50 model from [here](https://download.pytorch.org/models/resnet50-19c8e357.pth).

- Edit the experiment file at `polygon-rnnpp/Experiments/spaceNet/building_ggnn_vegas_epsilon1.json & building_ggnn_vegas_epsilon1_0.6.json`.

- Please prepare the dataset following the format of example data in `polygon-rnnpp/data/example_data` we prepared.

#### Train

- Edit the data folder name in `polygon-rnnpp/Scripts/train/train_spNb_ggnn_epsilon1.py` at line 39 & 40.

- Run `polygon-rnnpp/train_spNb_ggnn_epsilon1.sh`.

#### Test

- Edit the data folder name in `polygon-rnnpp/Scripts/prediction/generate_annotation_ggnn_epsilon1_0.6.py` at line 36.

- Run `polygon-rnnpp/test_spNb_ggnn_epsilon1_0.6.sh`.

## Citing

If you find our work useful in your research, please consider cite.

```latex
@article{LI202326,
    author = {Weijia Li and Wenqian Zhao and Jinhua Yu and Juepeng Zheng and Conghui He and Haohuan Fu and Dahua Lin},
    title = {Joint semantic–geometric learning for polygonal building segmentation from high-resolution remote sensing images},
    journal = {ISPRS Journal of Photogrammetry and Remote Sensing},
    volume = {201},
    pages = {26-37},
    year = {2023},
    issn = {0924-2716},
    doi = {https://doi.org/10.1016/j.isprsjprs.2023.05.010}
}
```

## Contact

If you need the complete code of this project, please send email to [liweij29@mail.sysu.edu.cn](mailto:liweij29@mail.sysu.edu.cn).
