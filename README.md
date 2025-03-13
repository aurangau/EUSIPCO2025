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
The image above has been taken from the paper - [1](https://openaccess.thecvf.com/content/CVPR2022/papers/Ji_XYDeblur_Divide_and_Conquer_for_Single_Image_Deblurring_CVPR_2022_paper.pdf) 
XY-Deblur introduced by Ji et. al. [1] is a single encoder multiple decoder architecture initially intended for restoring images degraded by motion blur. The model leverages the fact that employing multiple decoders allows for decomposing features into directional components, namely horizontal and vertical. The use of shared kernels amongst the decoders allows for improved deblurring performance. These caveats keep the total number of trainable parameters identical to a standard U-Net, viz. 4.2 million, while producing significantly sharper restorations. 

![EHNet](Network_Architectures/EHNet.png)
| --- |
| EHNet |

![ARKNet](Network_Architectures/ARKNet_EUSIPCO.png)
| --- |
| ARKNet |

## References
[1] Seo-Won Ji, Jeongmin Lee, Seung-Wook Kim, Jun-Pyo Hong, Seung-Jin Baek, Seung-Won Jung, and Sung-Jea Ko, “Xydeblur: divide and conquer for single image deblurring,” in Proceedings of the IEEE/CVF conference on computer vision and pattern recognition, 2022, pp.17421–17430
[2] Uditangshu Aurangabadkar, Darren Ramsook, and Anil Kokaram, “A sharpness based loss function for removing out-of-focus blur,” in 2024 IEEE 26th International Workshop on Multimedia Signal Processing (MMSP), 2024, pp. 1–6.
[3] Quoc-Thien Ho, Minh-Thien Duong, Seongsoo Lee, and Min-Cheol Hong, “Ehnet: Efficient hybrid network with dual attention for image deblurring,” Sensors, vol. 24, no. 20, pp. 6545, 2024.
