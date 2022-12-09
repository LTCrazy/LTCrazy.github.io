---
title: "Face Aging with GANs"
excerpt: "Short description of portfolio item number 1<br/><img src='/images/500x300.png'>"
collection: portfolio
---

This is an item in your portfolio. It can be have images or nice text. If you name the file .md, it will be parsed as markdown. If you name the file .html, it will be parsed as HTML. 

Face Aging with Modified Identity-Preserved Conditional GANs
=======================

1. Introduction

The project aims to implement Identity-Preserved Conditional Generative Adversarial Networks (IPCGANs) to create synthetic images of people that will show how people will look after a certain number of years are passed. Previously, a similar problem has been solved using Cycle Gan, in which an image of a person has been used as input, and both aged and de-aged (depending on the condition) synthetic photo of a person has been returned. 
Now, we will make the project more complicated and powerful by training the model to output not only an aged and de-aged version of a person but several images corresponding to different age groups of the same person. For example, we will input an image of a 45-year-old person and generate 5 synthetic images corresponding to 5 age groups, the 20s, 30s, 40s, 50, and 60s, thus simulating how one’s face will change the years.
