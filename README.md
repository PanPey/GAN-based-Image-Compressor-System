# GAN-based-Image-Compressor-System

Traditionally image compression techniques such as JPEG is not designed specifically for the data being compressed, and therefore do not achieve the best possible compression rates for images. In this project, we aim to construct a deep neural network- based compression architecture using a GAN model. A GAN consists of two networks called the generator and the discriminator. During training, the network tries to minimize an adversarial loss function. To achieve this the generator tries to create images that cannot be differentiated from true images while the discriminator tries to correctly classify images as real or generated. The discriminator is constructed just for the training purposes and is discarded after training.


GAN Model

A generative adversarial network (GAN) has two parts:
•	The generator learns to generate plausible data. The generated instances become negative training examples for the discriminator.
•	The discriminator learns to distinguish the generator's fake data from real data. The discriminator penalizes the generator for producing implausible results.
When training begins, the generator produces obviously fake data, and the discriminator quickly learns to tell that it's fake:
Both the generator and the discriminator are neural networks. The generator output is connected directly to the discriminator input. Through backpropagation, the discriminator's classification provides a signal that the generator uses to update its weights. 

The Discriminator

The discriminator in a GAN is simply a classifier. It tries to distinguish real data from the data created by the generator. It could use any network architecture appropriate to the type of data it's classifying.

Discriminator Training Data
The discriminator's training data comes from two sources:
•	Real data instances, such as real pictures of people. The discriminator uses these instances as positive examples during training.
•	Fake data instances created by the generator. The discriminator uses these instances as negative examples during training.


The Generator
The generator part of a GAN learns to create fake data by incorporating feedback from the discriminator. It learns to make the discriminator classify its output as real.
Generator training requires tighter integration between the generator and the discriminator than discriminator training requires. The portion of the GAN that trains the generator includes:
•	random input
•	generator network, which transforms the random input into a data instance
•	discriminator network, which classifies the generated data
•	discriminator output
•	generator loss, which penalizes the generator for failing to fool the discriminator

Alternating Training
The generator and the discriminator have different training processes. So how do we train the GAN as a whole?
GAN training proceeds in alternating periods:
1.	The discriminator trains for one or more epochs.
2.	The generator trains for one or more epochs.
3.	Repeat steps 1 and 2 to continue to train the generator and discriminator networks.
We keep the generator constant during the discriminator training phase. As discriminator training tries to figure out how to distinguish real data from fake, it has to learn how to recognize the generator's flaws. That's a different problem for a thoroughly trained generator than it is for an untrained generator that produces random output.
Similarly, we keep the discriminator constant during the generator training phase. Otherwise the generator would be trying to hit a moving target and might never converge.
It's this back and forth that allows GANs to tackle otherwise intractable generative problems. We get a toehold in the difficult generative problem by starting with a much simpler classification problem. Conversely, if you can't train a classifier to tell the difference between real and generated data even for the initial random generator output, you can't get the GAN training started.

Convergence
As the generator improves with training, the discriminator performance gets worse because the discriminator can't easily tell the difference between real and fake. If the generator succeeds perfectly, then the discriminator has a 50% accuracy. In effect, the discriminator flips a coin to make its prediction.
This progression poses a problem for convergence of the GAN as a whole: the discriminator feedback gets less meaningful over time. If the GAN continues training past the point when the discriminator is giving completely random feedback, then the generator starts to train on junk feedback, and its own quality may collapse.
For a GAN, convergence is often a fleeting, rather than stable, state


Future work &  Conclusion

We can basically aim to improve the quality of the compressed image and  future goal should be to improve the loss function used for latent vector training even further. This will enable us to build compressors that achieve more perceptual reconstructions with higher fidelity.
We have achieved a compressed image of the original input image, though the quality is compromised a bit. But with more work on it we get a better quality image. We believe that this new compression scheme is very promising for the future, since it utilizes the semantic relations of a group of images using a pretrained GAN, thus eliminating the redundant side information that can be stored elsewhere to allow for extreme compression


References-


[1] High-Fidelity Generative Image Compression
     https://arxiv.org/abs/2006.09965

[2] Eirikur Agustsson, Michael Tschannen, Fabian Mentzer, Radu Timofte, and     Luc Van Gool. Generative adversarial networks for extreme learned image compression. CoRR, abs/1804.02958, 2018 
    http://arxiv.org/abs/1804.02958.

[3] Feng Jiang, Wen Tao, Shaohui Liu, Jie Ren, Xun Guo, and Debin Zhao. An end-to-end compression framework based on convolutional neural networks. CoRR, abs/1708.00838, 2017.
   http: //arxiv.org/abs/1708.00838

