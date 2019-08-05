# ABD-Net: Attentive but Diverse Person Re-Identification

Refer to Training Guides README [here](./README_Training_Guides.md), original README [here](./README_ORIG.md), datasets README [here](./DATASETS.md), Model ZOO README [here](./MODEL_ZOO.md).

We provide complete usage pretrained models for our paper.

- Market1501 [best ABD-Net model](https://drive.google.com/file/d/1TuxnwSecg0EFFd5Z_665kek_e0Q-N4tU/view?usp=sharing)
- Duke [best ABD-Net model](https://drive.google.com/file/d/1wQtbi8gBe_oMLc9GvDXrGF5yRBoz51o_/view?usp=sharing)
- MSMT17 [best ABD-Net model](https://drive.google.com/file/d/1_ZpSfOxrid9xpSecAxEA2WAa6h-uWc1O/view?usp=sharing)

More models will come soon. If you want a pretrained model for some specific datasets, please be free to post an issue in our repo.

[ABD-Net: Attentive but Diverse Person Re-Identification]()

Tianlong Chen, Shaojin Ding\*, Jingyi Xie\*, Ye Yuan, Wuyang Chen, Yang Yang, Zhou Ren, Zhangyang Wang

In ICCV 2019

## Overview

Attention mechanism has been shown to be effective for person re-identification (Re-ID). However, the learned attentive feature embeddings which are often not naturally diverse nor uncorrelated, will compromise the retrieval performance based on the Euclidean distance. We advocate that enforcing diversity could greatly complement the power of attention. To this end, we propose an Attentive but Diverse Network (ABD-Net), which seamlessly integrates attention modules and diversity regularization throughout the entire network, to learn features that are representative, robust, and more discriminative.

Here are the visualization of attention maps. (i) Original images; (ii) Attentive feature maps; (iii) Attentive but diverse feature maps. Diversity can be observed to make attention "broader" in general, and to correct some mistaken over-emphasis (such as clothes textures) by attention. (L: large values; S: small values.)

![](./doc_images/JET_VIS.png)

Here are the visualization of correlation matrix between channels from Baseline, Baseline + PAM + CAM and ABD-Net (XE). Brighter color indicates larger correlation.

![](./doc_images/corr1.pdf)



## Methods

![](./doc_images/Arch.pdf)

We add a CAM (Channel Attention Module) and O.F. on the outputs of res\_conv\_2 block. The regularized feature map is used as the input of res\_conv\_3. Next, after the res\_conv\_4 block, the network splits into a **global branch** and an **attentive branch** in parallel. We apply O.W. on all conv layers in our ResNet-50 backbone, i.e.​, from res\_conv\_1 to res\_conv\_4 and the two res\_conv\_5 in both branches. The outputs of two branches are concatenated as the final feature embedding. 

Here are the detailed structure of CAM (Channel Attention Module) and PAM (Position Attention Module).

![](./doc_images/att.png)



## Results

We compare ABD-Net against the state-of-the-art methods on Market-1501,  DukeMTMC-Re-ID and MSMT17 as shown in Table 2, 3 and 4.

![](./doc_images/res.png)

Here are the Re-ID qualitative results as shown in Fig. 9. Here are 12 Re-ID examples of ABD-Net (XE), Baseline + PAM + CAM and Baseline on Market-1501. Left: query image. Right: i): top-5 results of ABD-Net (XE). ii): top-5 results of Baseline + PAM + CAM. iii): top-5 results of Baseline. Images in red boxes are negative results.

![](./doc_images/qr.png)



## Citation

If you use this code for your research, please cite our paper.

```
​```
@inproceedings{,
  title={ABD-Net: Attentive but Diverse Person Re-Identification},
  author={},
  booktitle={},
  year={2019}
}
​```
```