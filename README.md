# Supplementary Material for EUSIPCO 2025
Supplementary Material for EUSIPCO 2025
**Impact of a Sharpness Based Loss Function for Removing Out-of-Focus Blur** <br />
Authors: <samp>{aurangau, ramsookd, anil.kokaram}@tcd.ie</samp>

## Abstract
Recent research has explored complex loss functions for deblurring. In this work, we explore the impact of a previously introduced loss function – $Q$ which explicitly addresses sharpness and employ it to fine-tune State-of-the-Art (SOTA) deblurring models. Standard image quality metrics such as PSNR or SSIM do not distinguish sharpness from ringing. Therefore, we propose a novel full-reference image quality metric $\Omega$ that combines PSNR
with $Q$. This metric is sensitive to ringing artifacts, but not to a slight increase in sharpness, thus making it a fair metric for comparing restorations from deblurring mechanisms. Our approach shows an increase of 15% in sharpness ($Q$) and up to 10% in $\Omega$ over the use of standard losses.

## Network Architectures

### XY-Deblur
![XY-Deblur](Network_Architectures/XY_Deblur_arch.png)
| --- |
| XY-Deblur |

The image above has been taken from the paper - [1](https://openaccess.thecvf.com/content/CVPR2022/papers/Ji_XYDeblur_Divide_and_Conquer_for_Single_Image_Deblurring_CVPR_2022_paper.pdf) <br>
XY-Deblur introduced by Ji et. al. [1] is a single encoder multiple decoder architecture initially intended for restoring images degraded by motion blur. The model leverages the fact that employing multiple decoders allows for decomposing features into directional components, namely horizontal and vertical. The use of shared kernels amongst the decoders allows for improved deblurring performance. These caveats keep the total number of trainable parameters identical to a standard U-Net, viz. 4.2 million, while producing significantly sharper restorations. 

![EHNet](Network_Architectures/EHNet.png)
| --- |
| EHNet |

The image above has been taken from the paper - [2](https://www.mdpi.com/1424-8220/24/20/6545) <br>
EHNet proposed by Ho et. al. [2] is a transformer based architecture that combines Convolutional Neural Networks (CNNs) and transformers to create a hybrid deblurring mechanism. The CNNs allow for efficient local feature extraction, whereas the transformer decoder with dual-attention enable the model to capture spatial and channel-wise dependencies. The model consists of approximately 8.7 million trainable parameters.

![ARKNet](Network_Architectures/ARKNet_EUSIPCO.png)
| --- |
| ARKNet |

The image from has been taken from the paper - [3](https://ieeexplore.ieee.org/abstract/document/10743912) <br>
ARKNet proposed by Aurangabadkar et. al. [3] is a standard U-Net based architecture comprising of 4 encoder layers, where each layer consists of 5 convolutional blocks. Each block, in turn, comprises of a single 3 × 3 convolution layer, followed by Batch Normalization and GELU activation. The model contains a total of 4.2 million trainable parameters.

## Loss Functions
We first define a restored image as $\tilde{I}$ and a Ground Truth (GT) image as $I$. Let us now list the losses that were used by the authors to train their models initially. These losses are denoted by $\cal L_\varphi$. To use the proposed loss $Q$ [3] in the training routine, we use a composite loss that is defined as follows:
```math
\mathcal{L} = \mathcal{L}_\varphi (I, \tilde{I}) - \beta \cdot Q(\tilde{I})
```
Table 1 shows the model and the associated loss $\mathcal{L}_\varphi$ used in training.
**Table 1: Models and their losses**
| Model Name | $\mathcal{L}_\varphi$ |
| ---------- | -------------------- |
| XY- Deblur |         QA           |
XY-Deblur uses the $\mathcal{l_1}$ loss 

## References
[1] Seo-Won Ji, Jeongmin Lee, Seung-Wook Kim, Jun-Pyo Hong, Seung-Jin Baek, Seung-Won Jung, and Sung-Jea Ko, “Xydeblur: divide and conquer for single image deblurring,” in Proceedings of the IEEE/CVF conference on computer vision and pattern recognition, 2022, pp.17421–17430
[2] Quoc-Thien Ho, Minh-Thien Duong, Seongsoo Lee, and Min-Cheol Hong, “Ehnet: Efficient hybrid network with dual attention for image deblurring,” Sensors, vol. 24, no. 20, pp. 6545, 2024.
[3] Uditangshu Aurangabadkar, Darren Ramsook, and Anil Kokaram, “A sharpness based loss function for removing out-of-focus blur,” in 2024 IEEE 26th International Workshop on Multimedia Signal Processing (MMSP), 2024, pp. 1–6.
