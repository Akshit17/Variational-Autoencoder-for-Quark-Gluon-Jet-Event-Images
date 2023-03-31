# ML4SCI DeepFalcon Tasks

This repository contains evaluation Common Task 1 listed [here](https://docs.google.com/document/d/1bwRaHc0IYIcFOokMcW-mYJv2i24iP1mm08ALTSyQ4EI/edit#)

Common Task 1: https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images

Common Task 2:  https://github.com/Akshit17/GNN-based-classification

Specific Task 2: https://github.com/Akshit17/Diffusion-model-for-Quark-Gluon-Jet-images

Applying for :- “Diffusion Models for Fast Detector Simulation” project

---
## Jet events reconstruction

The accurate and efficient simulation of particle physics processes is crucial for the high-energy physics community, as simulating particle interactions in the detector is time-consuming and computationally expensive.  Jet event images reconstruction is needed to pave the way for full detector level fast simulation, as it can potentailly provide effective reconstruction of LHC events on the level of calorimeter deposits and tracks. 

For this particular evaluation task Variational autoencoder was used. Variational Autoencoder (VAE) is a type of generative model used for unsupervised learning. It is composed of two main components, an encoder and a decoder, which work together to learn a compressed representation of input data. The encoder takes the input data and maps it to a lower-dimensional latent space representation, while the decoder generates new data points from the learned latent representation.

---
## Dataset
[Dataset](https://drive.google.com/file/d/1WO2K-SfU2dntGU4Bb3IYBp9Rh7rtTYEr/view?usp=sharing) given consists of four keys X_jets(image), m0(mass), pt(transverse momentum), y(labels for quark and gluon jet). 
Each image is 125x125 consisting of three channels Track, ECAL and HCAL respectively.

#### Channels for a sample image :-
![All channels](https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/Visualizing_channels_VIRIDIS.PNG?raw=true)

#### Combined channels image samples :-
![Combined channels samples](https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/Combined_3channels_Samples.PNG?raw=true)

---

## Model building and training

#### Encoder Architecture :-

![Encoder Architecture](https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/Encoder_architecture.PNG?raw=true)

#### Decoder Architecture :-

![Decoder Architecture](https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/Decoder_architecture.PNG?raw=true)

Different architectures, loss function, hyperparameters like learning rate, bottleneck(latent_dim) dimensions, batch size etc were tried out. However the reconstructed images didn't come out to be similar to original images.  
Current model presented in the notebook uses these hyperparameters: `learning rate: 0.001`, `optimizer: Adam`, `latent_dim : 1024` 

## Performance

#### Training and validation loss plot:-
![training and validation loss plot](https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/trainingvsvalidationloss_plot.PNG?raw=true)

#### Latent space distribution plot:-
<img src="https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/latentspacedistribution_plot.PNG" alt="drawing" style="width:500px;"/>

## Discussion

*  Plot of training and validation loss suggests that validation losses for every epoch seem to be stuck around a value, indicating that the model is not improving much. Possible reasons can be:-
    *   Model architecture not being complex enough to capture the underlying patterns in the data, 
    *   Only a subset of dataset was used for training(~8000 images) 
    *   Data being too noisy and not providing clear patterns for the model to learn.
*   Data augmentation techniques like random blur, random crop, random rotation did not seem suitable as we are not working with classical images but with raw physical data.

*   Distribution of latent space plot shows only a few dots far away from the rest of the dots that are clustered in one place. This suggests that the model is unable to differentiate between the two classes of images, quark and gluon, and is instead producing a single cluster of images.



## Original vs Reconstructed images
#### Original images:-
![Original images](https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/original_events_3.PNG?raw=true)

#### Reconstructed images with different archietctures:-
![Reconstructed images 3](https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/reconstructed_events_3.PNG?raw=true)

![Reconstructed images 2](https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/reconstructed_events_2.PNG?raw=true)

![Reconstructed images 1](https://github.com/Akshit17/Variational-Autoencoder-for-Quark-Gluon-Jet-Event-Images/blob/master/assets/reconstructed_events_1.PNG?raw=true)




