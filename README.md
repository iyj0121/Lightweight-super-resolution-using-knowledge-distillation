**About PyTorch 1.6.0**
  * Now the main branch supports PyTorch 1.6.0 by default.

# Attention transfer을 활용한 EDSR-PyTorch모델 경량화

**About PyTorch 1.6.0**
  * feature map transfer 방식을 위에서 언급한 EDSR에 적용하여 모델 경량화 실험 진행 예정


![스크린샷_2023-05-03_오후_8.07.38](/uploads/ea0da2b1a3e3b2ae50c7043ca4c7a633/스크린샷_2023-05-03_오후_8.07.38.png)
![그림1](/uploads/70deee4757ab0a0395c4d50ececbb6d6/그림1.png)

This repository는 **"Enhanced Deep Residual Networks for Single Image Super-Resolution"** from **CVPRW 2017, 2nd NTIRE**.[here](https://github.com/LimBee/NTIRE2017) EDSR모델을 **"Paying More Attention to Attention: Improving the Performance of Convolutional Neural Networks via Attention Transfer"** from **ICLR2017: https://openreview.net/forum?id=Sks9_ajex** [here](https://arxiv.org/abs/1612.03928) 방식을 활용하여 모델 경량화를 진행하려고 한다.

<img width="834" alt="스크린샷 2023-05-08 오후 6 35 06" src="https://user-images.githubusercontent.com/90498398/236798239-85baa08e-fd66-49ea-acc2-aa07c482110e.png">

중간 실험 결과
학생 모델과 교사 모델로 부터 지식을 받은 ours 모델은 patch_size=96, n_resblocks=16, epochs=100, batch_size=8으로 진행함.
교사 모델은 patch_size=96, n_resblocks=32, epochs=300, batch_size=16으로 진행함.

[1] Bee Lim, Sanghyun Son, Heewon Kim, Seungjun Nah, and Kyoung Mu Lee, **"Enhanced Deep Residual Networks for Single Image Super-Resolution,"** <i>2nd NTIRE: New Trends in Image Restoration and Enhancement workshop and challenge on image super-resolution in conjunction with **CVPR 2017**. </i> [[PDF](http://openaccess.thecvf.com/content_cvpr_2017_workshops/w12/papers/Lim_Enhanced_Deep_Residual_CVPR_2017_paper.pdf)] [[arXiv](https://arxiv.org/abs/1707.02921)] [[Slide](https://cv.snu.ac.kr/research/EDSR/Presentation_v3(release).pptx)]
```
@InProceedings{Lim_2017_CVPR_Workshops,
  author = {Lim, Bee and Son, Sanghyun and Kim, Heewon and Nah, Seungjun and Lee, Kyoung Mu},
  title = {Enhanced Deep Residual Networks for Single Image Super-Resolution},
  booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR) Workshops},
  month = {July},
  year = {2017}
}
@inproceedings{Zagoruyko2017AT,
    author = {Sergey Zagoruyko and Nikos Komodakis},
    title = {Paying More Attention to Attention: Improving the Performance of
             Convolutional Neural Networks via Attention Transfer},
    booktitle = {ICLR},
    url = {https://arxiv.org/abs/1612.03928},
    year = {2017}}
```

## Dependencies
* Python 3.6
* PyTorch >= 1.6.0
* numpy
* skimage
* **imageio**
* matplotlib
* tqdm
* cv2 >= 3.xx (Only if you want to use video input/output)

## Code
Clone this repository into any place you want.
```bash
git clone https://github.com/thstkdgus35/EDSR-PyTorch
cd EDSR-PyTorch
```

## Quickstart (Demo)
You can test our super-resolution algorithm with your images. Place your images in ``test`` folder. (like ``test/<your_image>``) We support **png** and **jpeg** files.

Run the script in ``src`` folder. Before you run the demo, please uncomment the appropriate line in ```demo.sh``` that you want to execute.
```bash
cd src       # You are now in */EDSR-PyTorch/src
sh demo.sh
```

You can find the result images from ```experiment/test/results``` folder.

You can evaluate your models with widely-used benchmark datasets:

[Set5 - Bevilacqua et al. BMVC 2012](http://people.rennes.inria.fr/Aline.Roumy/results/SR_BMVC12.html),

[Set14 - Zeyde et al. LNCS 2010](https://sites.google.com/site/romanzeyde/research-interests),

[B100 - Martin et al. ICCV 2001](https://www2.eecs.berkeley.edu/Research/Projects/CS/vision/bsds/),

[Urban100 - Huang et al. CVPR 2015](https://sites.google.com/site/jbhuang0604/publications/struct_sr).

**Update log**
