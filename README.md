# 🔍 SRGAN-Canny

In the **Single-Image Super-Resolution** task one of the models that achieved best results is the **[SRGAN](https://arxiv.org/abs/1609.04802)**, whose architecture is based on the GAN model and uses a VGG-based **perceptual loss** in order to produce upscaled images.

In the notebook contained in the repository we re-implemented their architecture and trained it on the **[DIV2K](https://data.vision.ee.ethz.ch/cvl/DIV2K/)** dataset.

Starting from their architecture, we designed an alternative version which uses the **edge detection** mechanism in order to refine countours and enhance details. Therefore, using the **multi-task learning** paradigm we trained our model in order to reproduce not only the upscaled image but also the result of the **Canny edge detection operator** on the input image. 

<br /><br />
![architecture](https://user-images.githubusercontent.com/58000595/218801478-5b7d7a32-ea8f-4bc1-9db4-66f72b7d6a9c.png)

The pipeline used for training of the SRGAN-Canny and the original SRGAN is available on Colab.

<a href="https://colab.research.google.com/github/dotmat3/SRGAN-Canny/blob/main/SRGAN-Canny.ipynb">
  <img src="https://img.shields.io/badge/Colab-Open%20Notebook-green?style=for-the-badge&logo=googlecolab&color=blue">
</a>
<br /><br />

In the file [`Presentation.pdf`](https://github.com/dotmat3/SRGAN-Canny/blob/main/Presentation.pdf), a presentation of the work and challenges encountered during the development of this project is illustrated.

## Results

In this section, some of the results obtained by the model are presented. In particular, on the left we can see the low resolution image and on the right the upscaled version produced by the SRGAN-Canny model.
<br /><br />
<img src="https://user-images.githubusercontent.com/58000595/218803472-742dd0b7-4bad-44c7-b1bf-c47f94a80eb4.png" alt="baboon-lr" width="49%"></img>
<img src="https://user-images.githubusercontent.com/58000595/218802929-8e28d403-b3cd-4290-b2b7-60b557a13501.png" alt="baboon-sr" width="49%"></img>

<img src="https://user-images.githubusercontent.com/58000595/218803591-d0a33654-8c36-4c07-be76-02962cef1da4.png" alt="plane-lr" width="49%"></img>
<img src="https://user-images.githubusercontent.com/58000595/218802770-d12f51a8-99ef-47da-adf8-42a4fba28064.png" alt="plane-sr" width="49%"></img>

<img src="https://user-images.githubusercontent.com/58000595/218803540-a52a38bd-4e78-4939-8541-7750ac88d0a3.png" alt="camel-lr" width="49%"></img>
<img src="https://user-images.githubusercontent.com/58000595/218802840-fae6bfd4-cdb9-4897-bb92-fa1509b12f7b.png" alt="camel-sr" width="49%"></img>

Moreover, in the following table the average MSE, SSIM and PSNR are reported for the dataset used as test sets (Set5, Set14, BSD100) with both the baseline SRGAN architecture proposed in the original paper but trained on our dataset and our SRGAN-Canny version enhanced by the edge detection task.

|             | AVG MSE | AVG SSIM | AVG PSNR |
|-------------|:-------:|:--------:|:--------:|
| **SRGAN-VGG54** | 0,01971 | 0,59896  | 23,87128 |
| **SRGAN-Canny** | 0,01808 | 0,61142  | 24,25129 |

## Contributors

<a href="https://github.com/dotmat3" target="_blank">
  <img src="https://img.shields.io/badge/Profile-Matteo%20Orsini-green?style=for-the-badge&logo=github&labelColor=blue&color=white">
</a>
<br /><br />
<a href="https://github.com/SkyLionx" target="_blank">
  <img src="https://img.shields.io/badge/Profile-Fabrizio%20Rossi-green?style=for-the-badge&logo=github&labelColor=blue&color=white">
</a>

## Technologies

In this project, the following libraries for Python were used:
- TensorFlow
- OpenCV
- Numpy
- Matplotlib for plotting
- Weights and Biases in order to track the experiments
