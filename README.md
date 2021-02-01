# StyleFlow: Attribute-conditioned Exploration of StyleGAN-Generated Images using Conditional Continuous Normalizing Flows (ACM TOG 2021)

![Python 3.7](https://img.shields.io/badge/Python-3.7-green.svg?style=plastic)
![pytorch 1.1.0](https://img.shields.io/badge/Pytorch-1.1.0-green.svg?style=plastic)
![TensorFlow 1.15.0](https://img.shields.io/badge/TensorFlow-1.15.0-green.svg?style=plastic)
![Torchdiffeq 0.0.1](https://img.shields.io/badge/Torchdiffeq-0.0.1-green.svg?style=plastic)
![pyqt5 5.13.0](https://img.shields.io/badge/pyqt5-5.13.0-green.svg?style=plastic)

![image](./docs/assets/teaser.png)
**Figure:** *Sequential edits using StyleFlow*

High-quality, diverse, and photorealistic images can now be generated by unconditional GANs (e.g., StyleGAN). However, limited options exist to control the generation process using (semantic) attributes, while still preserving the quality of the output. Further, due to the entangled nature of the GAN latent space, performing edits along one attribute can easily result in unwanted changes along other attributes. In this paper, in the context of conditional exploration of entangled latent spaces, we investigate the two sub-problems of attribute-conditioned sampling and attribute-controlled editing. We present StyleFlow as a simple, effective, and robust solution to both the sub-problems by formulating conditional exploration as an instance of conditional continuous normalizing flows in the GAN latent space conditioned by attribute features. We evaluate our method using the face and the car latent space of StyleGAN, and demonstrate fine-grained disentangled edits along various attributes on both real photographs and StyleGAN generated images. For example, for faces, we vary camera pose, illumination variation, expression, facial hair, gender, and age. Finally, via extensive qualitative and quantitative comparisons, we demonstrate the superiority of StyleFlow to other concurrent works.

> **StyleFlow: Attribute-conditioned Exploration of StyleGAN-Generated Images using Conditional Continuous Normalizing Flows (ACM TOG 2021)** <br>
>  Rameen Abdal, Peihao Zhu, Niloy Mitra, Peter Wonka <br>



[[Paper](https://arxiv.org/pdf/2008.02401.pdf)]
[[Project Page](https://rameenabdal.github.io/StyleFlow/)]
[[Demo](https://youtu.be/LRAUJUn3EqQ)]
[[Promotional Video](https://youtu.be/Lt4Z5oOAeEY)]


## Note: This repo works only in Windows 10 



## Installation

Clone this repo.
```bash
git clone https://github.com/justinjohn0306/StyleFlow.git
cd StyleFlow/
```

This code requires PyTorch, TensorFlow, Torchdiffeq, Python 3+ and Pyqt5. Please install dependencies by
```bash
1. conda env create -f env_windows.yml (Install anaconda: [Download Anaconda 64-Bit Graphical Installer]
                                                          (https://www.anaconda.com/products/individual)

2. conda activate styleflow

3. conda install pytorch==1.2.0 torchvision==0.4.0 cudatoolkit=10.0 -c pytorch <<--- Important 
                                                                                     [Also available here:(https://pytorch.org/get-started/previous-versions/)]
4. Download and Install MICROSOFT VISUAL STUDIO COMMUNITY 2017   (https://visualstudio.microsoft.com/vs/older-downloads/)
   Make sure to add Microsoft Visual Studio to windows path [eg-: (C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat)]

5. add compiler_bindir_search_path inside custom_ops.py open this folder inside the StyleFlow-Windows-10 folder  ==>> dnnlib\tflib 
[eg: ('C:/Program Files (x86)/Microsoft Visual Studio/2017/Community/VC/Tools/MSVC/14.10.25017/bin/HostX64/x64',)]
```

StyleGAN2 relies on custom TensorFlow ops that are compiled on the fly using [NVCC](https://docs.nvidia.com/cuda/cuda-compiler-driver-nvcc/index.html). To correctly setup the StyleGAN2 generator follow the **Requirements** in [this repo](https://github.com/NVlabs/stylegan2).

## Installation (Docker)

Clone this repo.

```bash
git clone https://github.com/RameenAbdal/StyleFlow.git
cd StyleFlow/
```

You must have CUDA (>=10.0 && <11.0) and [nvidia-docker2](https://github.com/NVIDIA/nvidia-docker) installed first !

Then, run :

```bash
xhost +local:docker # Letting Docker access X server
wget -P stylegan/ http://d36zk2xti64re0.cloudfront.net/stylegan2/networks/stylegan2-ffhq-config-f.pkl
docker-compose up --build # Expect some time before UI appears
```

When finished, run :

```bash
xhost -local:docker
```

## UI Illustration

<img src="./docs/assets/main.gif" alt="main"  width=400> <img src="./docs/assets/attribute.gif" alt="main"  width=400>


**Loading images may take 2 - 3 seconds on the first click. Move the slider smoothly to render results.**




## Editing Images Using Pretrained Models


1.  Run the main UI

    ``` bash
	python main.py
    ```

2. Run the Attribute Transfer UI
	```bash
   python main_attribute.py 
    ```


## Training New Model

To be added



## License

All rights reserved. Licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode) (**Attribution-NonCommercial-ShareAlike 4.0 International**) The code is released for academic research use only.

## Citation
If you use this research/codebase, please cite our papers.
```
@article{abdal2020styleflow,
  title={Styleflow: Attribute-conditioned exploration of stylegan-generated images using conditional continuous normalizing flows},
  author={Abdal, Rameen and Zhu, Peihao and Mitra, Niloy and Wonka, Peter},
  journal={arXiv e-prints},
  pages={arXiv--2008},
  year={2020}
}
```
```
@INPROCEEDINGS{9008515,
  author={R. {Abdal} and Y. {Qin} and P. {Wonka}},
  booktitle={2019 IEEE/CVF International Conference on Computer Vision (ICCV)}, 
  title={Image2StyleGAN: How to Embed Images Into the StyleGAN Latent Space?}, 
  year={2019},
  volume={},
  number={},
  pages={4431-4440},
  doi={10.1109/ICCV.2019.00453}}
```
## Acknowledgments
This implementation builds upon the awesome work done by Karras et al. ([StyleGAN2](https://github.com/NVlabs/stylegan2)), Chen et al. ([torchdiffeq](https://github.com/rtqichen/torchdiffeq)) and Yang et al. ([PointFlow](https://arxiv.org/abs/1906.12320)). This work was supported by Adobe Research and KAUST Office of Sponsored Research (OSR).
