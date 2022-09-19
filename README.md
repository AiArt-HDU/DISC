# DISC

## Introduction

- DISC is an open  source, PyTorch-based method for **facial sketch synthesis(FSS)**.


-  For more information about efficientSegmentation, please read the following paper:  "Depth-Informed and Style-Controllable Facial Sketch Synthesis via Dynamic Adaptation" .


- This project generates a quality and vivid sketch portrait from a given photo using a GAN-based model.  Besides, our method allows precise style control of the synthesised sketch. Please also cite this paper if you are using the method for your research! 


## Sample Results

- **Comparison with SOTAs on the FS2K dataset:**

![localFace1](https://github.com/AiArt-HDU/DISC/blob/main/images/localFace1.jpg)

![localFace2](https://github.com/AiArt-HDU/DISC/blob/main/images/localFace2.jpg)

![localFace3](https://github.com/AiArt-HDU/DISC/blob/main/images/localFace3.jpg)

(a)Photo   (b)Depth   (c)Ours   (d)Pix2PixHD   (e)FSGAN   (f)SCA-GAN   (g)GT   (h)Pix2Pix   (i)MDAL   (j)CycleGAN   (k)GENRE

- **Performance on faces in-the-wild:**

![wildFace1](https://github.com/AiArt-HDU/DISC/blob/main/images/wildFace1.jpg)

![wildFace2](https://github.com/AiArt-HDU/DISC/blob/main/images/wildFace2.jpg)

![wildFace3](https://github.com/AiArt-HDU/DISC/blob/main/images/wildFace3.jpg)

(a)Photo   (b)Ours(Style1)   (c)Ours(Style2)   (d)Ours(Style3)   (e)GENRE   (f)Pix2Pix   (g)CycleGAN   (h)SCA-GAN

-  **Performance of our DISC model on natural images:**

![cat](https://github.com/AiArt-HDU/DISC/blob/main/images/cat.png)

![building1](https://github.com/AiArt-HDU/DISC/blob/main/images/building1.png)

![building2](https://github.com/AiArt-HDU/DISC/blob/main/images/building2.png)

(a)Photo   (b)Depth   (c)Ours(Style1)   (d)Ours(Style2)   (e)Ours(Style3)

- **More Results:**

We offer more results here: https://drive.google.com/file/d/1vT0nqEVVByBW1QltYVX_mIYCcZ4wXsQD/view?usp=sharing

## Prerequisites

- Linux or macOS
- Python 3.8.12
- Pytorch-lightning 0.7.5
- CPU or NVIDIA GPU + CUDA CuDNN

## Getting Started

### Installation

- Clone this repo:

  ```
  git clone https://github.com/AiArt-HDU/DISC
  cd DISC
  ```

- Install PyTorch 1.7.1 and torchvision from [http://pytorch.org](http://pytorch.org/) and other dependencies (e.g., [visdom](https://github.com/facebookresearch/visdom) and [dominate](https://github.com/Knio/dominate)). You can install all the dependencies by

  ```
  pip install -r requirements.txt
  ```

- The installation environment of DCN-V2 depandency is more complicated，you can refer to the 

  [official installation method]: https://github.com/EMI-Group/FaPN

## Apply a pre-trained model

- A face photo↦sketch model pre-trained on dataset [FS2K](https://drive.google.com/file/d/1ATeDl-Vu2Ztq3i0jeu9Qyap0MyOdg05v/view?usp=sharing)
- The [pre-trained model](https://drive.google.com/file/d/1q9S7nHaweH8OMmfVZ9Zv4FcHNHjfBsDy/view?usp=sharing) need to be save at `./checkpoint`
- Then you can test the model

### Train/Test

- Download the dataset [FS2K](https://drive.google.com/file/d/1ATeDl-Vu2Ztq3i0jeu9Qyap0MyOdg05v/view?usp=sharing) here

- Train a model

  ```
  python train.py --root your_root_path_train
  ```

- Test the model: please prepare your test data's depth maps using 3DDFA methods

  ```
  python test.py --data_dir your_data_path_test --depth_dir your_depth_path_test 
  ```

- If you want to train on your own data, please first align your pictures and prepare your data's depth maps according to tutorial in **preprocessing steps**.

### Preprocessing steps

Face photos (and paired drawings) need to be aligned and have depth maps. And depth maps after alignment are needed in our code in training.

In our work, depth map is generated by method in [1]

- First, we need to align, resize and crop face photos (and corresponding drawings) to 250x250
- Then,we use code in 

[3DDFA]: https://github.com/cleardusk/3DDFA_V2

 to generate depth maps for face photos and drawings.

[^1]: J. Guo, X. Zhu, Y. Yang, F. Yang, Z. Lei, and S. Z. Li, “Towards fast, accurate and stable 3d dense face alignment,” in *Proceedings of the* *European Conference on Computer Vision (ECCV)*, 2020.

## Demo

Our sketch portrait drawing demos:

![demo](https://github.com/fei-hdu/genre/blob/master/imgs/demo.jpg)

 (a) QR code of the applet of WeChat, (b) QR code of the Web API, (c)-(e) layouts of the applet of WeChat, and (f) picture of the drawing robot. Readers can try our demos by scanning the QR codes.

## Citation

 If you use this code for your research, please cite our paper. 

## Acknowledgments

Our code is inspired by [pytorch-CycleGAN-and-pix2pix](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix) and 

[Genre]: https://github.com/fei-hdu/genre



.