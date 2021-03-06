# Satellite image analysis and processing

Satellite mapping is way easier than traditional cartographic methods, but still, the main challenge is in recognizing particular objects in the image, like roads, buildings and landmarks. Getting up-to-date information about roadblocks and threats is even more essential. And that’s where machine learning-based solutions come into play.

![](images/block_diagram2.jpg)

- Image enhancement: improve the quality of image
- Image restoration: restore degraded images
- Object detection: AI algorithms for detection, segmentation, captioning and classification
- Representation and description

Many applications could benefit from automatic analysis of satellite images : cartography, urban planning, traffic analysis, biomass estimation and so on. Therefore, lots of progresses have been made to use machine learning to help us have a better understanding of our Earth Observation data.

In this project, I show that deep learning allows a computer to parse and classify objects in an image and can be used for automatical cartography from remote sensing data. Especially, I provide examples of deep fully convolutional networks that can be trained for semantic labeling for airborne pictures of urban areas.

### Satellite image segmentation

Image Segmentation is a topic of machine learning where one needs to not only categorize what’s seen in an image, but to also do it on a per-pixel level. Here, I want to go from a satellite image to a map representation where things in the image are automatically categorized just like generating a map view automatically from satellite images.

#### Network architecture
A convolution is an operation that changes a function into something else. We do convolutions so that we can transform the original function into a form to get more information.

Convolutions have been used for a long time in image processing to blur and sharpen images, and perform other operations, such as, enhance edges and emboss.


A baseline fully-convolutional network uses a simple encoder-decoder framework to solve semantic segmentation tasks. It consists of only convolutional and pooling layers, without any fully connected layers. This allows it to make predictions on arbitrary-sized inputs. By propagating an image through several pooling layers, the resolution of feature maps is downsampled, which, due to information loss during pooling operations, results in low-resolution, coarse segmentation maps.

![](images/net_architecture.png)

1. Convolutional Layer: A convolution operation is an element wise matrix multiplication operation. Where one of the matrices is the image, and the other is the filter or kernel that turns the image into something else. The output of this is the final convoluted image.
The job of the convolutional layer is feature extraction. It learns to find spatial features in an input image. This layer is produced by applying a series of different image filters to an input image. These filters are known as convolutional kernels. A filter is a small grid of values that slides over the input image pixel by pixel to produce a filtered output image that will be of the same size as the input image.  Multiple kernels will produce different filtered output images.

![](images/convolution.gif)

2. Batch Normalization: Batch normalization is a technique for training very deep neural networks that standardizes the inputs to a layer for each mini-batch. This has the effect of stabilizing the learning process and dramatically reducing the number of training epochs required to train deep networks.

![](images/bn.png)

3. The activation function is a mathematical “gate” in between the input feeding the current neuron and its output going to the next layer. It can be as simple as a step function that turns the neuron output on and off, depending on a rule or threshold. Or it can be a transformation that maps the input signals into output signals that are needed for the neural network to function.

ReLU (Rectified Linear Unit)

![](images/relu.jpeg)

Advantages: 
- Computationally efficient—allows the network to converge very quickly.
- Non-linear—although it looks like a linear function, ReLU has a derivative function and allows for backpropagation.

4. Pooling: The pooling layer reduces the spatial size of the input representation, which then reduces the number of parameters and computations in the network. This makes it easier to detect objects in an image no matter where they’re located.

![](images/pooling.png)

### Transfer Learning
Transfer learning (TL) is a research problem in machine learning (ML) that focuses on storing knowledge gained while solving one problem and applying it to a different but related problem. For example, knowledge gained while learning to recognize cars could apply when trying to recognize trucks. 
We download and load the pre-trained weights from VGG-16 on ImageNet. This step is optional but it makes the network converge faster. We skip the weights from VGG-16 that have no counterpart in our network.

