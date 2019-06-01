# MSCS Project

This repository overviews an Artificial Intelligence design project which I completed while completing my Master's in Computer Science at Georgia Tech. The source code for this project is not publically available, in compliance with the Georgia Institute of Technology Academic Honor Code<sup><a href="https://policylibrary.gatech.edu/student-affairs/academic-honor-code">[1]</a></sup>.

Instead, I have substituted my raw code with a guided walkthrough of the project itself, the steps I went through to complete it, and the skills I acquired by solving it.

# Overview

Automatic image processing is a key component to many AI systems, including facial recognition and video compression. One basic method for processing is segmentation, by which one divides an image into a fixed number of components in order to simplify its representation. For example, I can train a mixture of Gaussians to represent an image, and segment it according to the simplified representation as shown in the images below.

<p align="center"><img width="370" height="208" src=images/self-driving-1.png></img></p>
<div align="center"><b>Fig 1. Footage from a Self-Driving Car</b></div>

<p align="center"><img width="370" height="208" src=images/self-driving-2.png></img></p>
<div align="center"><b>Fig 2. Simplified Footage</b></div>

In this image, I learned how to perform image segmentation by implemenenting Guassian mixture models and iteratively improving their performance. I implemented several methods of image segmentation, with increasing complexity:

1. Implemented k-means clustering to segment a color image.
2. Built a Gaussian mixture model to be trained with expectation-maximization.
3. Experimented with varying the details of the Gaussian mixture model’s implementation.
4. Implemented and tested a new metric called the Bayesian information criterion, which guaranteed a more robust image segmentation.

# Gaussian Mixture Models

A Gaussian mixture model is a generative model<sup><a href="https://en.wikipedia.org/wiki/Generative_model">[2]</a></sup> for representing the underlying probability distribution of a complex collection of data, such as the collection of pixels in a grayscale photograph.

In the context of this problem, a Gaussian mixture model defines the joint probability f(x) as:

<p align="center"><img width="374" height="122" src=images/formula-1.png></img></p>

* x is a grayscale value [0,1]
* f(x) is the joint probability of that gray scale value
* m<sub>i</sub> is the mixing coefficient on component i 
* N<sub>i</sub> is the i<sup>th</sup> Gaussian distribution underlying the value x with mean μ<sub>i</sub> and variance σ<sub>i</sub><sup>2</sup>.

I used this model to segment photographs into different grayscale regions. The idea of segmentation is to assign a component i to each pixel x using a maximum posterior probability, which equates to:

<p align="center"><img width="562" height="78" src=images/formula-2.png></img></p>

Then I replaced each pixel in the image with its corresponding μ<sub>i</sub>, to produce a result similar to what I showed in Figure 2.
