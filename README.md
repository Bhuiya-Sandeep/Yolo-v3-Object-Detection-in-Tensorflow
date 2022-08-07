# Yolo v3 Object Detection in Tensorflow

Object detection is a task in computer vision that involves identifying the presence, location, and type of one or more objects in a given photograph.

It is a challenging problem that involves building upon methods for object recognition (e.g. where are they), object localization (e.g. what are their extent), and object classification (e.g. what are they).

In recent years, deep learning techniques are achieving state-of-the-art results for object detection, such as on standard benchmark datasets and in computer vision competitions. Notable is the “You Only Look Once,” or YOLO, family of Convolutional Neural Networks that achieve near state-of-the-art results with a single end-to-end model that can perform object detection in real-time.

![This is an image](https://i.ytimg.com/vi/yQwfDxBMtXg/maxresdefault.jpg)

YOLO for Object Detection
Object detection is a computer vision task that involves both localizing one or more objects within an image and classifying each object in the image.

It is a challenging computer vision task that requires both successful object localization in order to locate and draw a bounding box around each object in an image, and object classification to predict the correct class of object that was localized.

The “You Only Look Once,” or YOLO, family of models are a series of end-to-end deep learning models designed for fast object detection, developed by Joseph Redmon, et al. and first described in the 2015 paper titled “You Only Look Once: Unified, Real-Time Object Detection.”

The approach involves a single deep convolutional neural network (originally a version of GoogLeNet, later updated and called DarkNet based on VGG) that splits the input into a grid of cells and each cell directly predicts a bounding box and object classification. The result is a large number of candidate bounding boxes that are consolidated into a final prediction by a post-processing step.

There are three main variations of the approach, at the time of writing; they are YOLOv1, YOLOv2, and YOLOv3. The first version proposed the general architecture, whereas the second version refined the design and made use of predefined anchor boxes to improve bounding box proposal, and version three further refined the model architecture and training process.

Although the accuracy of the models is close but not as good as Region-Based Convolutional Neural Networks (R-CNNs), they are popular for object detection because of their detection speed, often demonstrated in real-time on video or with camera feed input.

# Interpret the prediction vector

The input image is divided into an S x S grid of cells. For each object that is present on the image, one grid cell is said to be responsible for predicting it. That is the cell where the center of the object falls into.

Each grid cell predicts B bounding boxes as well as C class probabilities. The bounding box prediction has five components x, y, w, h, confidence. The (x, y) coordinates represent the center of the box, relative to the grid cell location. These coordinates are normalized to fall between 0 and 1. The (w, h) box dimensions are also normalized to [0, 1], relative to the image size.

![This is an image](https://miro.medium.com/max/1050/1*etbDtmj-pqQC2sxtiqC_Bw.png)

# The Network

The network structure looks like a CNN, with convolutional and max pooling layers, followed by 2 fully connected layers in the end.

![This is an image](https://miro.medium.com/max/1050/1*ab_OTjlniZG77E9Tnv0xxg.png)

# Loss Function
We only want one of the bounding boxes to be responsible for the object within the image since the YOLO algorithm predicts multiple bounding boxes for each grid cell. To achieve this, we use the loss function to compute the loss for each true positive.

![This is an image](https://miro.medium.com/max/1050/1*ipcAZNtO2O4oZTMsef2uYQ.png)

This equation computes the loss related to the predicted bounding box position (x,y). The function computes a sum over each bounding box predictor (j = 0.. B) of each grid cell (i = 0 .. S²). 𝟙 obj is defined as:

1, If an object is present in grid cell i and the jth bounding box predictor is “responsible” for that prediction
0, otherwise.

# The result

![This is an image](https://miro.medium.com/max/900/1*aFZBri3yg2lxV5eovy9KnA.gif)

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install Yolo v3 Object Detection in Tensorflow.

```bash
pip install Yolo v3 Object Detection in Tensorflow
```
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
