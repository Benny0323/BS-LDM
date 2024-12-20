# BS-LDM: Effective Bone Suppression in High-Resolution Chest X-Ray Images with Conditional Latent Diffusion Models

![](https://img.shields.io/badge/-Github-181717?style=flat-square&logo=Github&logoColor=FFFFFF)
![](https://img.shields.io/badge/-Awesome-FC60A8?style=flat-square&logo=Awesome&logoColor=FFFFFF)
![](https://img.shields.io/badge/-Python-3776AB?style=flat-square&logo=Python&logoColor=FFFFFF)
![](https://img.shields.io/badge/-Pytorch-EE4C2C?style=flat-square&logo=Pytorch&logoColor=FFFFFF)

This code is a **pytorch** implementation of our paper **"BS-LDM: Effective Bone Suppression in High-Resolution Chest X-Ray Images with Conditional Latent Diffusion Models"**.

## Primary Contributions
1) We developed an innovative end-to-end **conditional LDM**, **BS-LDM**, designed for **bone suppression** in **high-resolution CXR images (1024 × 1024 pixels)**. This model aids in the clinical diagnosis of lung diseases such as **inflammation**, **tuberculosis**, and **masses or nodules**.
2) We demonstrated the effectiveness of **offset noise** in generating low-frequency information in soft tissue images. Additionally, we introduced a **dynamic clipping strategy** to enhance the pixel intensity of the generated images.
3) We compiled a substantial and high-quality bone suppression dataset named **SZCH-X-Rays**, consisting of high-resolution paired CXR and DES soft tissue images from 818 patients gathered from partner hospitals. Moreover, we pre-processed and publicized 241 pairs of CXR and DES soft tissue images from the **JSRT** dataset.

## Proposed Method
Overview of the proposed BS-LDM. The top side of the framework describes the training process of BS-LDM, where the latent variables of the CXR images are used as conditional guidance for the estimation of the offset noise. At the bottom, the sampling process of BS-LDM is detailed, where the latent variables obtained after each sampling step are dynamically clipped to ensure that the resulting pixel intensities are consistent with real soft tissue images.

<div align="center">
<img src="https://github.com/diaoquesang/BS-LDM/blob/main/images/frame.png" width="100%">
</div>

## Visualization of high- and low-frequency feature decomposition of latent variables before and after Gaussian noise addition
<div align="center">
<img src="https://github.com/diaoquesang/BS-LDM/blob/main/images/freq.png" width="100%">
</div>

## Illustration of the composition of offset noise
<div align="center">
<img src="https://github.com/diaoquesang/BS-LDM/blob/main/images/off.png" width="100%">
</div>

## Visualization of soft tissue images on SZCH-X-Rays and JSRT datasets produced by different methods
<div align="center">
<img src="https://github.com/diaoquesang/BS-LDM/blob/main/images/comp.png" width="100%">
</div>

## Visualization of ablation studies of offset noise and the dynamic clipping strategy of BS-LDM
<div align="center">
<img src="https://github.com/diaoquesang/BS-LDM/blob/main/images/abl2.png" width="80%">
</div>

## Presentation of CXR and DES soft tissue images in SZCH-X-Rays and JSRT datasets
<div align="center">
<img src="https://github.com/diaoquesang/BS-LDM/blob/main/images/dataset.png" width="80%">
</div>

## Detailed Clinical Evaluation Results

### Image Quality Assessment
The soft tissue images generated by BS-LDM on the SZCH-X-Rays dataset were independently evaluated for image quality based on established clinical criteria  widely used to assess bone suppression efficacy. Three radiologists, with 6, 11, and 20 years of experience, respectively, conducted these evaluations at our partner hospitals. The average scores for lung vessel visibility, airway visibility, and degree of bone suppression were 2.758, 2.714, and 2.765, respectively, on a scale where the maximum score was 3. These results indicate that our BS-LDM not only effectively suppresses bones but also retains fine details and lung pathology.

<table align="center">
<thead align="center" valign="center">
  <tr>
    <th colspan="2">Clinical Evaluation Criteria</th>
    <th>Junior Physician</th>
    <th>Intermediate Physician</th>
    <th>Senior Physician</th>
  </tr>
</thead>
<tbody align="center" valign="center">
  <tr>
    <td rowspan="3">Lung vessel visibility</td>
    <td>Clearly displayed (3)</td>
    <td rowspan="3">2.431</td>
    <td rowspan="3">2.858</td>
    <td rowspan="3">2.984</td>
  </tr>
  <tr>
    <td>Displayed (2)</td>
  </tr>
  <tr>
    <td>Not displayed (1)</td>
  </tr>
  <tr>
    <td rowspan="3">Airway visibility</td>
    <td>Lobar and intermediate bronchi (3)</td>
    <td rowspan="3">2.561</td>
    <td rowspan="3">2.643</td>
    <td rowspan="3">2.937</td>
  </tr>
  <tr>
    <td>Main bronchus and rump (2)</td>
  </tr>
  <tr>
    <td>Trachea (1)</td>
  </tr>
  <tr>
    <td rowspan="3">Degree of bone suppression</td>
    <td>Nearly perfect suppression (3)</td>
    <td rowspan="3">2.781</td>
    <td rowspan="3">2.793</td>
    <td rowspan="3">2.722</td>
  </tr>
  <tr>
    <td>Unsuppressed bones less than 5 (2)</td>
  </tr>
  <tr>
    <td>5 or more bones unsuppressed (1)</td>
  </tr>
</tbody>
</table>

### Diagnostic Utility Assessment
The diagnostic value of soft tissue imaging was independently evaluated by two radiologists with 6 and 11 years of experience, respectively, following the X-ray diagnostic standard. For this analysis, we used the SZCH-X-Rays dataset, which included confirmed lesions through computed tomography, covering common lung diseases such as inflammation, tuberculosis, and masses or nodules.

Among the 818 data pairs assessed, 79 pairs contained one or more of these lesions. The radiologists independently evaluated both the conventional CXRs and the soft tissue images generated by our model. The findings indicate that the soft tissue images produced by BS-LDM enable radiologists to diagnose lesions more thoroughly and accurately than conventional CXRs, thereby validating the high clinical diagnostic value of our model.



<table align="center">
<tbody align="center" valign="center">
  <tr>
    <td>Junior Radiologist</td>
    <td>Precision (↑)</td>
    <td>Recall (↑)</td>
    <td>F1 Score (↑)</td>
  </tr>
  <tr>
    <td>CXR</td>
    <td>0.70</td>
    <td>0.40</td>
    <td>0.51</td>
  </tr>
    <tr>
    <th>Tissue</th>
    <th>0.73</th>
    <th>0.56</th>
    <th>0.63</th>
  </tr>
  <tr>
    <td>Senior Radiologist</td>
    <td>Precision (↑)</td>
    <td>Recall (↑)</td>
    <td>F1 Score (↑)</td>
  </tr>
  <tr>
    <td>CXR</td>
    <td>0.74</td>
    <td>0.51</td>
    <td>0.60</td>
  </tr>
    <tr>
    <th>Tissue</th>
    <th>0.75</th>
    <th>0.75</th>
    <th>0.75</th>
  </tr>
</tbody>
</table>

## Pre-requisties
* Linux

* Python>=3.7

* NVIDIA GPU (memory>=6G) + CUDA cuDNN

### Pre-trained models
[VQGAN - SZCH-X-Rays](https://drive.google.com/file/d/1KcVK0F7lG5L9Zc0-pWPS9pucAWIG3yFc/view?usp=sharing)
[UNet - SZCH-X-Rays](https://drive.google.com/file/d/1zt5rV-d5wXVXCOgYqqM3C3r4wap6XkBe/view?usp=sharing)
[VQGAN - JSRT](https://drive.google.com/file/d/17qp7H3v6L4fOqZJCTWifpzXGydEQSloU/view?usp=sharing)
[UNet - JSRT](https://drive.google.com/file/d/12b2rykq6lw1hajEbMJtidJZRVl-ZXX3a/view?usp=sharing)


### Download the dataset
The original JSRT dataset and precessed JSRT dataset are located at [https://drive.google.com/file/d/1RkiU85FFfouWuKQbpD7Pc7o3aZ7KrpYf/view?usp=sharing](https://drive.google.com/file/d/1RkiU85FFfouWuKQbpD7Pc7o3aZ7KrpYf/view?usp=sharing) and [https://drive.google.com/file/d/1o-T5l2RKdT5J75eBsqajqAuHPfZnzPhj/view?usp=sharing](https://drive.google.com/file/d/1o-T5l2RKdT5J75eBsqajqAuHPfZnzPhj/view?usp=sharing), respectively.

Three paired images with CXRs and DES soft-tissues images of SZCH-X-Rays for testing are located at
```
└─BS-LDM
    ├─ CXR
    │   ├─ 0.png
    │   ├─ 1.png
    │   └─ 2.png
    └─ BS
        ├─ 0.png
        ├─ 1.png
        └─ 2.png
```

### Install dependencies
```
pip install -r requirements.txt
```

## Evaluation
To do the evaluation process of VQGAN, please run the following command:
```
python vq-gan_eval.py
```      
To do the evaluation process of the conditional latent diffusion model, please run the following command:
```
python ldm_eval.py
```

## Training
If you want to train our model by yourself, you are primarily expected to split the whole dataset into training, validation and testing sets. Please run the following command:
```
python dataSegmentation.py
```
Then, you can run the following command to train the VQGAN model:
```
python vq-gan_train.py
```
Then after finishing the training of VQGAN, you can use the saved VQGAN model as a decoder when training the conditional latent diffusion model by running the following command:
```
python ldm_train.py
```

## Metrics
You can also run the following command about evaluation metrics in our experiment including BSR, MSE, PSNR and LPIPS:
```
python metrics.py
```

## Citation
```
Upcoming Soon!
```
