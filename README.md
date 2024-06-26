# CatFaceGAN - Generating Realistic Cat Faces with GANs
# Objective:
The primary objective of CatFaceGAN is to develop a deep learning model capable of generating highquality, diverse, and realistic images of cat faces. This project aims to explore and harness the capabilities
of Generative Adversarial Networks (GANs) to produce images that are indistinguishable from real photographs of cats. The generated images can serve various purposes:<br></br>
• Including enhancing the dataset for other machine learning projects. <br></br>
• Creating virtual pets. <br></br>
• Providing content for entertainment and educational purposes.<br></br>

# Background:
GANs have shown remarkable success in the field of generative models, especially in tasks related to image generation, modification, and enhancement. By leveraging a dueling network architecture —
comprising a generator that creates images and a discriminator that evaluates them — GANs can learn to produce highly realistic outputs. This project focuses on the specific domain of cat faces, which
presents unique challenges due to the variety in fur patterns, colors, shapes, and expressions inherent
to felines.<br></br>

# Methodology: 
# Dataset: 
This dataset is a collection of 15,700 pictures from kaggle, all showing cat faces. Each picture has the same size of 64x64 pixels. This size makes the pictures easy to work with while still clear enough to see the cat's face details.<br></br>
# Key Attributes: <br></br>
Number of Images: 15,700
Content Focus: Cat Faces
Image Resolution: 64x64 pixels
Link: https://www.kaggle.com/datasets/spandan2/cats-faces-64x64-for-generative-models/code

# Preprocessing: 
The steps implemented in our preprocessing stage included: <br></br>
Read: Each selected image file was read into memory. <br></br>
Decode: The binary content of the image was decoded into an image format TensorFlow could work with, specifying 3 channels to ensure the image was in color. <br></br>
Resize: Images were resized to 64x64 pixels, the required input size for the GAN.<br></br>
Normalize: Pixel values, typically in the range [0, 255], were normalized to fall within [-1, 1]. This normalization helped the GAN model converge faster during training.<br></br>
Preprocessing steps like resizing and normalization were critical in GANs to ensure that our model could effectively learn from the data. Normalization adjusted the input data to a scale that neural networks
worked with more effectively, contributing to faster learning and more stable training processes.

# Training Model: 
# Generator:
The training model for generating cat faces using GANs was constructed through a collaboration of three key components: the generator, the discriminator, and the training process. Each function played a
crucial role in the model's ability to learn and produce realistic cat faces from random noise. <br></br>
The generator's job was to produce new, synthetic images that looked as close to real images as
possible, starting from a random noise vector and transforming this into an image through a series of layers.
key components:<br></br>
• Began with a dense layer to expand the input noise vector. <br></br>
• Utilized Conv2DTranspose layers (deconvolution) to upsample the image to the target size of 64x64 pixels.<br></br>
• Employed BatchNormalization and LeakyReLU to stabilize the training process and encourage gradient flow.<br></br>
The generator was critical for creating the synthetic images that the GAN used to fool the discriminator. Its architecture was designed to efficiently transform simple noise into complex image structures
resembling cat faces.
# Discriminator:
The discriminator's role was to distinguish between real images (actual cat faces) and fake images
produced by the generator.<br></br>
key components: <br></br>
• A series of Conv2D layers that downsampled the image, learning to recognize various features of cat faces.<br></br>
• LeakyReLU activation for non-linearity without blocking the gradient flow during training.<br></br>
• Dropout to prevent overfitting by randomly omitting a subset of features during training.<br></br>
The discriminator guided the generator in producing more realistic images. By getting better at
identifying fake images, it pushed the generator to improve its output, creating a feedback loop that enhanced the model's performance over time.<br></br>

# Train:

Across all models, the discriminator tended to improve as indicated by the decreasing loss values, effectively distinguishing between real and generated images over time.<br></br>
 • The generator also improved but faced challenges as indicated by the fluctuations in loss values. <br></br>
• The increase in the number of images and epochs generally led to a more nuanced training process, likely contributing to a generator capable of creating more realistic images. <br></br>
• It is important to note that a perfectly trained generator would cause the discriminator loss to approximate 0.5, indicating an inability to distinguish real from fake, which seems to be approached more closely in the later epochs of the models with more training.
