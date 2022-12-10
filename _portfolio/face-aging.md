---
title: "Face Aging with Different GAN-s Architectures"
excerpt: "Short description of portfolio item number 1<br/><img src='/images/face-aging-cover.png'>"
collection: portfolio
---

# Motivation

Face aging has many applications in various domains, including cross-age face recognition, finding lost children, and entertainment. Objectively evaluating how a person will look in the future certainly sparks a massive interest in the population. Additional interests arise when we want to see the older picture of ourselves and specify by how many years exactly we want to age ourselves. Many powerful aging methods exist nowadays, but none is perfect for solving the problem. We have explored various methods for performing Face Aging, and in the following project, we are driven to recreate State of the Art methods, evaluating them and providing the course for future work.

# Work

In the following project, we explore 3 GANs architectures: CycleGAN, IPCGAN, and Style-Based Regression Model. We are comparing generated images across various architectures, evaluating the results based on a qualitative assessment of the photos. We also consider different aspects of modeling, such as how much time it takes to train, how difficult it is to preprocess data and how fast it is to make predictions. 

# Dataset and Preprocessing 

We are using [Cross-Age Reference Coding for the Age-Invariant Face Recognition and Retrieval](https://bcsiriuschen.github.io/CARC/) dataset. The dataset contains images of celebrities taken during different years of their careers, allowing us to track how their faces have changed over the years. Dataset contains more than 163,000 images. However, many examples need to be corrected: the name of the celebrity is incorrect, the face is hidden, etc. For that reason, we apply a preprocessing step to clean the pictures by checking if the eyes, nose, and mouth are clearly visible. After that, we align the face by the angle between the nose and eyes, evening the examples across the dataset. The examples of pictures after the dataset is cleaned are provided below.

![dataset-example](https://github.com/LTCrazy/LTCrazy.github.io/blob/master/images/dataset-example.png)

# Modeling

* ## [CycleGAN]()

[CycleGAN](https://github.com/LTCrazy/LTCrazy.github.io/blob/master/images/CycleGAN.png)

For cycleGAN, we filtered the faces younger than 35 and older than 65. After that, we create corresponding pairs and use them as input for the model. Correspondingly, we are training GAN-s that are connected via cycle-consistency loss (as shown in the picture. Eventually, we are getting to generators, the one that ages a person and the other one, which de-ages.

* ## [IPCGAN](https://ieeexplore.ieee.org/document/8578926)

[IPCGAN](https://github.com/LTCrazy/LTCrazy.github.io/blob/master/images/IPCGAN.png)

IPCGAN is more challenging to train than CycleGAN since, for each iteration, we are generating 5 fake images corresponding to five progressing aging groups (20+,30+,40+,50+,60+). IPCGAN contains an additional age classifier that ensures that generated image falls into the target age. The value of IPCGAN is that it allows us to specify the exact age group we want our generated image to correspond to, making the model more flexible than CycleGAN.


# Results

# Repo

[CycleGAN](https://github.com/AleksandrSim/MSA_495_project)
