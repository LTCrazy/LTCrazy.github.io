---
title: "Face Aging with Different GAN-s Architectures"
excerpt: "Generating portraits of individuals at different age of their life using CycleGAN, IPCGAN, and Style-Based Regression Model<br/><img src='/images/face-aging-cover.png'>"
collection: portfolio
---
[Aleksandr Simonyan](https://github.com/AleksandrSim) [[Email](aleksandrsimonyan2022@U.NORTHWESTERN.EDU)], [Tianchang Li](https://github.com/LTCrazy]) [[Email](tianchangli2022@U.NORTHWESTERN.EDU)]

## Motivation

Face aging has many applications in various domains, including cross-age face recognition, finding lost children, and entertainment. Objectively evaluating how a person will look in the future certainly sparks a massive interest in the population. Additional interests arise when we want to see the older picture of ourselves and specify by how many years exactly we want to age ourselves. Many powerful aging methods exist nowadays, but none is perfect for solving the problem. We have explored various methods for performing Face Aging, and in the following project, we are driven to recreate State of the Art methods, evaluating them and providing the course for future work.

## Work

In the following project, we explore 3 GANs architectures: CycleGAN, IPCGAN, and Style-Based Regression Model. We are comparing generated images across various architectures, evaluating the results based on a qualitative assessment of the photos. We also consider different aspects of modeling, such as how much time it takes to train, how difficult it is to preprocess data and how fast it is to make predictions. 

## Dataset and Preprocessing 

We are using [Cross-Age Reference Coding for the Age-Invariant Face Recognition and Retrieval](https://bcsiriuschen.github.io/CARC/) dataset. The dataset contains images of celebrities taken during different years of their careers, allowing us to track how their faces have changed over the years. Dataset contains more than 163,000 images. However, many examples need to be corrected: the name of the celebrity is incorrect, the face is hidden, etc. For that reason, we apply a preprocessing step to clean the pictures by checking if the eyes, nose, and mouth are clearly visible. After that, we align the face by the angle between the nose and eyes, evening the examples across the dataset. The examples of pictures after the dataset is cleaned are provided below.
<br/><img src='/images/dataset-example.png' width="600">

## Modeling

* ### [CycleGAN](https://arxiv.org/abs/1703.10593)

<br/><img src='/images/CycleGAN.png' width="800">

For cycleGAN, we filtered the faces younger than 35 and older than 65. After that, we create corresponding pairs and use them as input for the model. Correspondingly, we are training GAN-s that are connected via cycle-consistency loss (as shown in the picture. Eventually, we are getting to generators, the one that ages a person and the other one, which de-ages.

* ### [IPCGAN](https://ieeexplore.ieee.org/document/8578926)
<br/><img src='/images/IPCGAN.png' width="800">

IPCGAN is more challenging to train than CycleGAN since, for each iteration, we are generating 5 fake images corresponding to five progressing aging groups (20+,30+,40+,50+,60+). IPCGAN contains an additional age classifier that ensures that generated image falls into the target age. The value of IPCGAN is that it allows us to specify the exact age group we want our generated image to correspond to, making the model more flexible than CycleGAN.

* ### [Style-Based Regression Model](https://arxiv.org/abs/2102.02754)

The most powerful Aging model that exists today receives an input face image and the desired target age. First, the aging encoder encodes feature maps. Then, map2style blocks down-sample the feature maps into style vectors. A pre-trained StyleGAN is then used to generate the desired age-transformed image using the aggregated latent code. Eventually, the model is capable of generating images of very high fidelity and very precise alignment with the target age.

## Results Examples

* ### CycleGAN

* * Aging
<br/><img src='/images/aging.png' width="300">

* * De-aging
<br/><img src='/images/de-aging.png' width="300">

* ### IPCGAN
<br/><img src='/images/face-aging-cover.png' width="800">

* ### Style-based Regression Model
<br/><img src='/images/Style-based-example.png' width="800">

## Evaluation of CycleGAN and IPCGAN 

* CycleGAN outperforms IPCGAN regarding aging effect fidelity
* IPCGAN has an intuitive, meaningful architecture but only capture macro features in aging (e.g. large patch of shadows, face color)
* CycleGAN attends to finer details (e.g. wrinkles, contour lines)
* CycleGAN are much easier and faster to train

## Final Thoughts and Future work

As we can see, Age Transformation via the Style-Based Regression Model outperforms both CycleGAN and IPCGAN. While fidelity for CycleGAN is high, it cannot generate images for different age groups. The style-Based Regression Model, however, is extremely difficult to train since the model has a complex architecture and various loss criteria. In addition, even Age Transformation via Style-Based Regression does not generate perfect examples while having a very long inference time. Difficult preprocessing is another limitation of the model. The future work will be based on Diffusion Models, capable of generating high-fidelity images much faster while maintaining much simpler architecture and criteria. Weighted Guidance for Diffusion models will be a very useful technique for conditioning generated images under various age groups, thus allowing us to achieve the same effects as we achieved with Age Transformation via the Style-Based Regression Model.


## GitHub Repo

[CycleGAN](https://github.com/AleksandrSim/MSA_495_project), 
[IPCGAN](https://github.com/AleksandrSim/AleksandrSim-COMP_SCI_496-0_final_project)
