# Intelligent noise suppression for gravitational wave observational data
[![release](https://img.shields.io/badge/release-v1.0.0-orange.svg)](https://img.shields.io/badge/release-v1.0.0-orange.svg)
[![license](https://shields.io/badge/license-Apachev2.0-green.svg)](https://shields.io/badge/license-Apachev2.0-green.svg)


## Introduction

This repository contains the code and data example of [our paper](). 
Data parallel and model parallel machanism are choosable during running the code.
Based on [Megatron-LM framework](https://github.com/NVIDIA/Megatron-LM), we achieved gravitational wave denoising and parameter estimation with transformer-based model.

## Results
Based on pretrained WaveFormer, we can achieve significant noise suppression on real observational gravitational waveforms.
Here, we present some results on reported binary black hole events.
It can be observed that both phase and amplitude information of the waveforms are well recovered.

<div align="center">
    TBA
</div>

## Requirements

* `python >= 3.8`
* `pytorch >= 1.8.0`
* `astropy == 4.3.1`
* `lalsimulation >= 3.0.0`
* `bilby >= 1.1.4`

## Run Training Demo

Download the whole repository and adapt the arguments in the script, then run:
```shell
bash demo.sh
```
Training curve would be as follows.

<div align="center">
    <img src='images/demo.png' alt='training curve' style='zoom:80%'>
</div>

### Arguments
There many different arguments to be adapted in `demo.sh`. If the other arguments are not specified, a default value will be assumed for them. Here are some of the commonly used arguments:

* `MASTER_ADDR`: IP address of your machine.
* `GPUS_PER_NODE`: Number of GPUs per machine used for training.
* `DATA_PATH`: Path to the training dataset (base folder).
* `CHECKPOINT_PATH`: Path to the checkpoint saving folder.
* `num-layers`: Number of encoder layers.
* `num-attention-heads`: Number of attention heads.
* `hidden-size`: Hidden size of each encoder layer.
* `micro-batch-size`: Batch size of each GPU.
* `lr`: Initial learning rate. Depending on decay style.
* `segment-length`: Number of samples in each token.
* `train-iters`: Maximum training iterations.


### More about Training
To train with your own data, you can define corresponding dataset class with reference to `class GwDataset` of [megatron/data/gw_dataset.py](megatron/data/gw_dataset.py)

### Python Environment
We have tested WaveFormer with python 3.8, pytorch 1.10.0, cuda 11.1, and nccl 2.8.3.

To use this repository, we recommend using one of NGC's PyTorch containers (`docker pull nvcr.io/nvidia/pytorch:20.12-py3`).

Optionally, we have build a docker image based on the above container that can be pulled through `docker pull zzhopezhou/astropre:1.5`.
Widely used libraries for gravitaional wave and astronomical analysis including `astropy`, `bilby`, `lalsimulation`, et. al. are already installed in the image.

## Citations
Please cite the following papers if you find the code useful:

```
@article{TBA
 
}

@inproceedings{narayanan2021efficient,
  title={Efficient large-scale language model training on gpu clusters using megatron-lm},
  author={Narayanan, Deepak and Shoeybi, Mohammad and Casper, Jared and LeGresley, Patrick and Patwary, Mostofa and Korthikanti, Vijay and Vainbrand, Dmitri and Kashinkunti, Prethvi and Bernauer, Julie and Catanzaro, Bryan and others},
  booktitle={Proceedings of the International Conference for High Performance Computing, Networking, Storage and Analysis},
  pages={1--15},
  year={2021}
}
```
