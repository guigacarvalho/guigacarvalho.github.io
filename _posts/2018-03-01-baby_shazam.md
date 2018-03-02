---
layout: post
title:  Processing audio with python to help first time parents
categories: personal
date:   2018-03-01 07:15:22 -0700
comments: true
---

> The infant's crying is a communication way, although more limited, it is similar to adult's speech. - José Orozco

This is aguarbly the creepiest (but kinda cool) project I've set myself to tackle. Couples of years ago, I stumbled upon this paper: "Detecting Pathologies from Infant Cry Applying Scaled Conjugate Gradient Neural Networks". At the time, my nephew was just born and I decided to give it a try.

This small project aims to identify what a baby needs based on the sound of his cry. The idea is to used a labeled set of baby cry audio files (in the dataset I've used, the labels were: *hunger*, *pain*, *normal*, *asphyxia*, *deafness*) to train a classifier and then try to predict the baby's needs. 

The only gotcha is that you need to process these audio files before feeding it to the training algorithm. You have to convert the audio signal to the frequency domain (more info about what that means here and here) to summarize the data contained in the audio files. 

Once that's done, there are a myriad of python librarys that help you to train your model and create predictions. I've used these:

- Audio file reading: Scipy.io
- Fourier Transform: Scikit talkbox
- Model training and prediction: Sklearn
- Efficient mathematical computations: numpy

You can checkout the code for more info [here](https://github.com/guigacarvalho/baby_shazam).

## Results

We've got around 72% accuracy with this model, which is better than a random guess, but not ideal if you are a first-time parent with a screamming child.

<amp-img alt="confusion matrix"
    width="400"
    height="400"
    layout="responsive"
    src="https://github.com/guigacarvalho/baby_shazam/raw/master/Result.png">
</amp-img>

## Random Thoughts

Better results would come with better audio processing (noise isolation) and bigger trainning dataset. I also think that the addition of a few other labels such as "It's time to change that diaper" or "wild child seeking attention" would be a great addition.
