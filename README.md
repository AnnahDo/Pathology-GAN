# Pathology-GAN

## Demo Materials:
* Fake images with the smallest distance to real: For each row, the first image is a generated one, the remaining seven images are close Inception-V1 neighbors of the fake image:
<p align="center">
  <img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/unconditional/neigbor_selected.png" width="400">
</p>

* Hand-selected fake images: For each row, the first image is a generated one, the remaining seven images are close Inception-V1 neighbors of the fake image:
<p align="center">
  <img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/unconditional/neighbors_min_dist.png" width="400">
</p>

* Individual Images:
<p align="center">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_0.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_1.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_2.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_3.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_4.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_5.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_6.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_7.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_8.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_9.png" width="100"> <img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_10.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_11.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_12.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_13.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_14.png" width="100">
<img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/er_negative/individual_images/gen_15.png" width="100">
</p>

* Images:
  * [Unconditional](https://github.com/AdalbertoCq/Pathology-GAN/tree/master/demos/unconditional)
  * ER: [Positive](https://github.com/AdalbertoCq/Pathology-GAN/tree/master/demos/er_positive), [Negative](https://github.com/AdalbertoCq/Pathology-GAN/tree/master/demos/er_negative)
  * Survival time: [Smaller five years](https://github.com/AdalbertoCq/Pathology-GAN/tree/master/demos/survival_negative), [Larger or equal to five years](https://github.com/AdalbertoCq/Pathology-GAN/tree/master/demos/survival_postive).

## Datasets:
H&E breast cancer databases from the Netherlands Cancer Institute (NKI) cohort and the Vancouver General Hospital (VGH) cohort with 248 and 328 patients respectevely. Each of them include tissue micro-array (TMA) images, along with clinical patient data such as survival time, and estrogen-receptor (ER) status. The original TMA images all have a resolution of 1128x720 pixels, and we split each of the images into smaller patches of 224x224, and allow them to overlap by 50%. We also perform data augmentation on these images, a rotation of 90 degrees, and 180 degrees, and vertical and horizontal inversion. We filter out images in which the tissue covers less than 70% of the area. In total this yields a training set of 249K images, and a test set of 62K.

We use these Netherlands Cancer Institute (NKI) cohort and the Vancouver General Hospital (VGH) previously used in Beck, A.H. and Sangoi, A.R. and Leung, S. Systematic analysis of breast cancer morphology uncovers stromal features associated with survival. Science translational medicine (2018)

You can find a pre-processed HDF5 file with patches of 224x224x3 resolution [here](), each of the patches also contains labeling information of the estrogen receptor status and survival time.

This is a sample of an original TMA image:
<p align="center">
  <img src="https://github.com/AdalbertoCq/Pathology-GAN/blob/master/demos/original_tma.jpg" width="400">
</p>

## Python Enviroment:
```
h5py                    2.9.0
numpy                   1.16.1
pandas                  0.24.1
scikit-image            0.14.2
scikit-learn            0.20.2
scipy                   1.2.0
seaborn                 0.9.0
sklearn                 0.0
tensorboard             1.12.2
tensorflow              1.12.0
tensorflow-probability  0.5.0
python                  3.6.7
```

## Training PathologyGAN:
```
usage: run_gans.py [-h] --type TYPE [--epochs EPOCHS]
                   [--batch_size BATCH_SIZE]

PathologyGAN trainer.

optional arguments:
  -h, --help               show this help message and exit
  --type TYPE              Type of PathologyGAN: unconditional, er, or survival.
  --epochs EPOCHS          Number epochs to run: default is 45 epochs.
  --batch_size BATCH_SIZE  Batch size, default size is 64.
```

* Unconditional Pathology GAN:
```
python3 run_gans.py --type unconditional
```
* Estrogen Receptor Pathology GAN:
```
python3 run_gans.py --type er
```
* Survival Time Pathology GAN:
```
python3 run_gans.py --type survival
```

