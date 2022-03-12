# Removing Pixel Noises and Structured Artefacts Using Generative Diversity Denoising Methods

Mangal Prakash<sup>1,2</sup>, Mauricio Delbracio<sup>3</sup>, Peyman Milanfar<sup>3</sup>, Florian Jug<sup>1,2,4</sup></br>
<sup>1</sup>Max Planck Institute of Molecular Cell Biology and Genetics (**[MPI-CBG](https://www.mpi-cbg.de/home/)**) <br>
<sup>2</sup>Center for Systems Biology (**[CSBD](https://www.csbdresden.de/)**), Germany <br>
<sup>3</sup>Google Research, USA <br>
<sup>4</sup>Fondazione Human Technopole (**[HT](https://humantechnopole.it/en/)**), Italy <br>

![teaserFigure]( https://user-images.githubusercontent.com/31291854/116880534-69deb280-ac22-11eb-98cc-5a0ffdfaab16.png "Figure 1 taken from publication")

Image denoising and artefact removal are complex inverse problems admitting many potential solutions.
Variational Autoencoders (VAEs) can be used to learn a whole distribution of sensible solutions, from which one can sample efficiently.
However, such a generative approach to image restoration is only studied in the context of pixel-wise noise removal (e.g. Poisson or Gaussian noise). 
While important, a plethora of application domains suffer from imaging artefacts (structured noises) that alter groups of pixels in correlated ways.
In this work we show, for the first time, that generative diversity denoising (GDD) approaches can learn to remove structured noises without supervision.
To this end, we investigate two existing GDD architectures, introduce a new one based on hierarchical VAEs, and compare their performances against a total of seven state-of-the-art baseline methods on five sources of structured noise (including tomography reconstruction artefacts and microscopy artefacts).
We find that GDD methods outperform all unsupervised baselines and in many cases not lagging far behind supervised results (in some occasions even superseding them).
In addition to structured noise removal, we also show that our new GDD method produces new state-of-the-art (SOTA) results on seven out of eight benchmark datasets for pixel-noise removal.
Finally, we offer insights into the daunting question of how GDD methods distinguish structured noise, which we like to see removed, from image signals, which we want to see retained.

### Information

This repository hosts the the code for the **[publication](https://openreview.net/forum?id=DfMqlB0PXjM&referrer=%5BAuthor%20Console%5D(%2Fgroup%3Fid%3DICLR.cc%2F2022%2FConference%2FAuthors%23your-submissions))** **Removing Pixel Noises and Spatial Artefacts with Generative Diversity Denoising Methods**. 

### Citation
If you find our work useful in your research, please consider citing:

```
@inproceedings{
prakash2022interpretable,
title={Interpretable Unsupervised Diversity Denoising and Artefact Removal},
author={Mangal Prakash and Mauricio Delbracio and Peyman Milanfar and Florian Jug},
booktitle={International Conference on Learning Representations},
year={2022},
url={https://openreview.net/forum?id=DfMqlB0PXjM}
}
```

### Dependencies 
To install all dependencies, follow the following steps.

You could use the same virtual environment (`HDN.yml`) as used by us by following the steps below.
 
1. Clone the repository locally by using the command `git clone https://github.com/juglab/HDN.git`
2. Move into the cloned folder by using the command `cd HDN`. 
3. Create a new environment by entering the python command in the terminal `conda env create -f HDN.yml`. This will install all dependencies needed to run the notebooks.
4. Then run the command `conda activate HDN`.
5. After this, run the command `pip install ipykernel`.
6. Finally, run the command `python -m ipykernel install --user --name HDN --display-name 'HDN'`.

Then, before running the notebooks, select kernel as `HDN` if it is not selected automatically.

***__Note:__*** We used cudatoolkit 10.1 and pytorch 1.7 for our experiments and the installation steps above install these versions.


### Getting Started
Look in the `examples` directory and try out the notebooks. 
For pixel wise noise removal with Hierarchical DivNoising networks, look into the subdirectory `Pixel_Noise` and for Structured Noise Removal with Hierarchical DivNoising networks, look into the subdirectory `Structured_Noise`.

##### Pixel Noise Removal
The subdirectory `examples/Pixel_Noise/Natural` contains training, evaluation and generation notebooks for natural image dataset BSD68 corrupted with synthetic Gaussian noise. In case, your noisy data is generated using a Gaussian noise model, then you can start with the training step directly.
For this, begin by running : (i) `1-Training.ipynb`. This will download the data and train a Hierarchical DivNoising network. (ii) `2-Evaluation.ipynb` starts network prediction on test data.

The subdirectory `examples/Pixel_Noise/Convallaria` contains training, evaluation and generation notebooks for microscopy image dataset Convallaria which is intrinsically noisy (pixel wise noise). In case your noisy data is NOT generated by a gaussian noise process and contains real-world pixel noise, then you should start by preparing the noise model by first running : (i) `1-CreateNoiseModel.ipynb`. This will download the data and create a suitable noise model. Then proceed to (ii) `2-Training.ipynb` which starts network training and finally run (iii) `3-Evaluation.ipynb` for prediction part.

##### Structured Noise Removal
The subdirectory `examples/Structured_Noise/Convallaria` contains training and evaluation notebooks for microscopy image dataset Convallaria which is intrinsically noisy (containing both pixel noise and horizontal line artefacts). First start by preparing the noise model by first running : (i) `1-CreateNoiseModel.ipynb`. This will download the data and create a suitable pixel wise noise model. Then proceed to (ii) `2-Training.ipynb` which starts network training and finally run (iii) `3-Evaluation.ipynb` for prediction part.

