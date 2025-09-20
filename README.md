# A Prior-Driven Lightweight Network for Endoscopic Exposure Correction (MICCAI 2025)
Zhijian Wu, Hong Wang, Yuxuan Shi, Dingjiang Huang, and Yefeng Zheng

# Environment
Make Conda Environment
```
conda create -n WTNet python=3.7
conda activate WTNet
```

Install Dependencies
```
conda install pytorch=1.11 torchvision cudatoolkit=11.3 -c pytorch
pip install matplotlib scikit-learn scikit-image opencv-python yacs joblib natsort h5py tqdm tensorboard
pip install einops gdown addict future lmdb numpy pyyaml requests scipy yapf lpips
```
pytorch_wavelets
```
git clone https://github.com/fbcotter/pytorch_wavelets
cd pytorch_wavelets
pip install .
```
# Dataset
1. [Kvasir-Capsule Dataset](https://osf.io/dv2ag/) and [Red Lesion Endoscopy Dataset](https://rdm.inesctec.pt/dataset/nis-2018-003) (The low-light and ground-truth image pairs are released by [LLCaps](https://github.com/longbai1006/LLCaps).)
3. [Endo4IE Dataset](https://data.mendeley.com/datasets/3j3tmghw33/1)
4. [Capsule endoscopy Exposure Correction (CEC) Dataset](https://mycuhk-my.sharepoint.com/:u:/g/personal/1155161502_link_cuhk_edu_hk/EZuLCQk1SjRMr7L6pIpiG5kBwhcMGp1hB_g73lySKlVUjA?e=g84Zl8)

# Training
```
#CEC
python3 basicsr/train.py --opt Options/WTNet_CEC.yml

#Endo4IE
python3 basicsr/train.py --opt Options/WTNet_Endo4IE.yml

#KC
python3 basicsr/train.py --opt Options/WTNet_KC.yml

#RLE
python3 basicsr/train.py --opt Options/WTNet_RLE.yml
```
# Testing

```
python3 Enhancement/test_from_dataset.py --opt Options/WTNet_CEC.yml --weights pretrained_weights/xxxx.pth --dataset CEC
```
# Checkpoints
Please see Releases.

[CEC](https://github.com/charonf/WTNet/releases/download/checkpoints/CEC.pth)

[Endo4IE](https://github.com/charonf/WTNet/releases/download/checkpoints/Endo4IE.pth)

[KC](https://github.com/charonf/WTNet/releases/download/checkpoints/KC.pth)

[RLE](https://github.com/charonf/WTNet/releases/download/checkpoints/RLE.pth)

# Citations
```
@InProceedings{WTNet,
author="Wu, Zhijian and Wang, Hong and Shi, Yuxuan and Huang, Dingjiang and Zheng, Yefeng",
title="A Prior-Driven Lightweight Network for Endoscopic Exposure Correction",
booktitle="Medical Image Computing and Computer Assisted Intervention -- MICCAI 2025",
year="2026",
publisher="Springer Nature Switzerland",
address="Cham",
pages="13--23",
}
```

# Acknowledgement
The code is partly built on [Retinexformer](https://github.com/caiyuanhao1998/Retinexformer), [EndoUIC](https://github.com/longbai1006/EndoUIC?tab=readme-ov-file).
