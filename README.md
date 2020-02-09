# Satellite image analysis and processing

Satellite mapping is way easier than traditional cartographic methods, but still, the main challenge is in recognizing particular objects in the image, like roads, buildings and landmarks. Getting up-to-date information about roadblocks and threats is even more essential. And that’s where machine learning-based solutions come into play.

Many applications could benefit from automatic analysis of satellite images : cartography, urban planning, traffic analysis, biomass estimation and so on. Therefore, lots of progresses have been made to use machine learning to help us have a better understanding of our Earth Observation data.

In this project, I show that deep learning allows a computer to parse and classify objects in an image and can be used for automatical cartography from remote sensing data. Especially, I provide examples of deep fully convolutional networks that can be trained for semantic labeling for airborne pictures of urban areas.

### Network architecture

A baseline fully-convolutional network uses a simple encoder-decoder framework to solve semantic segmentation tasks. It consists of only convolutional and pooling layers, without any fully connected layers. This allows it to make predictions on arbitrary-sized inputs. By propagating an image through several pooling layers, the resolution of feature maps is downsampled, which, due to information loss during pooling operations, results in low-resolution, coarse segmentation maps.

![](images/net_architecture.png)


1. Satellite image segmentation

2. Satellite image captioning
