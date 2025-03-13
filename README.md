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
| XY-Deblur introduced by Ji et. al. [13] is a single encoder
multiple decoder architecture initially intended for restoring
images degraded by motion blur. The model leverages the
fact that employing multiple decoders allows for decomposing
features into directional components, namely horizontal and
vertical. The use of shared kernels amongst the decoders
allows for improved deblurring performance. These caveats
keep the total number of trainable parameters identical to a
standard U-Net, viz. 4.2 million, while producing significantly
sharper restorations |

![EHNet](Network_Architectures/EHNet.png)
| --- |
| EHNet |

![ARKNet](Network_Architectures/ARKNet_EUSIPCO.png)
| --- |
| ARKNet |
