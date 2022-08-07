---
title: Deeplearning on MacOS M-series Processors
created: '2022-08-06T18:25:22.471Z'
modified: '2022-08-07T11:43:17.525Z'
---

# Deeplearning on MacOS M-series Processors

## tensorflow with m1 support

## pytorch with m1 support

## run python inside swift

use [pythonkit](https://github.com/pvieito/PythonKit.git)

## automatic machine learning using CreateML

```swift
import CreateML
```

CreateML is similar to any other [AutoML]() tools, like [AutoKeras](https://autokeras.com/), 

## using CoreML

CoreML models can be created by CreateML and some customization can be done via `protocol MLCustomLayer`.

[onnxruntime]() can run onnx models on CoreML.

## Links


<details><summary><a href="https://developer.apple.com/machine-learning/models/">CoreML Models</a></summary>
<p>
FCRN-DepthPrediction
Depth Estimation

Predict the depth from a single image.
View Models

MNIST
Drawing Classification

Classify a single handwritten digit (supports digits 0-9).
View Model

UpdatableDrawingClassifier
Drawing Classification

Drawing classifier that learns to recognize new drawings based on a K-Nearest Neighbors model (KNN).
View Model and Code Sample

MobileNetV2
Image Classification

The MobileNetv2 architecture trained to classify the dominant object in a camera frame or image.
View Models and Code Sample

Resnet50
Image Classification

A Residual Neural Network that will classify the dominant object in a camera frame or image.
View Models and Code Sample

SqueezeNet
Image Classification

A small Deep Neural Network architecture that classifies the dominant object in a camera frame or image.
View Models and Code Sample

DeeplabV3
Image Segmentation

Segment the pixels of a camera frame or image into a predefined set of classes.
View Models

YOLOv3
Object Detection

Locate and classify 80 different types of objects present in a camera frame or image.
View Models and Code Sample

YOLOv3-Tiny
Object Detection

Locate and classify 80 different types of objects present in a camera frame or image.
View Models and Code Sample

PoseNet
Pose Estimation

Estimates up to 17 joint positions for each person in an image.
View Models and Code Sample
Text

BERT-SQuAD
Question Answering

Find answers to questions about paragraphs of text.
View Model and Code Sample
</p></details>

[CoreML APIs](https://developer.apple.com/machine-learning/api/) (may need user permission within or without xcode by means of Info.plist or something)

Vision
Build features that can process and analyze images and video using computer vision.

View Vision framework


Image Classification
Automatically identify the content in images.

View API


Image Saliency
Quantify and visualize the key part of an image or where in the image people are likely to look.

View API


Image Alignment
Analyze and manage the alignment of images.

View API


Image Similarity
Generate a feature print to compute distance between images.

View API


Object Detection
Find and label objects in images.

View API


Object Tracking
Track moving objects in video.

View API


Trajectory Detection
Detect the trajectory of objects in motion in video.

View API


Contour Detection
Trace the edges of objects and features in images and video.

View API


Text Detection
Detect regions of visible text in images.

View API


Text Recognition
Find, recognize, and extract text from images.

View API


Face Detection
Detect human faces in images.

View API


Face Tracking
Track faces from a camera feed in real time.

View API


Face Landmarks
Find facial features in images by detecting landmarks on faces.

View API


Face Capture Quality
Compare face capture quality in a set of images.

View API


Human Body Detection
Find regions that contain human bodies in images.

View API


Body Pose
Detect landmarks on people in images and video.

View API


Hand Pose
Detect landmarks on human hands in images and video.

View API


Animal Recognition
Find cats and dogs in images.

View API


Barcode Detection
Detect and analyze barcodes in images.

View API


Rectangle Detection
Find rectangular regions in images.

View API


Horizon Detection
Determine the horizon angle in images.

View API


Optical Flow
Analyze the pattern of motion of objects between consecutive video frames.

View API


Person Segmentation New
Produce a matte image for a person in an image.

View API


Document Detection New
Detect rectangular regions in images that contain text.

View API

Natural Language
Analyze natural language text and deduce its language-specific metadata.

View Natural Language framework


Tokenization
Enumerate the words in text strings.

View API


Language Identification
Recognize the language of bodies of text.

View API


Named Entity Recognition
Use a linguistic tagger to name entities in a string.

View API


Part of Speech Tagging
Classify nouns, verbs, adjectives, and other parts of speech in a string.

View API


Word Embedding
Get a vector representation for any word and find similarity between two words or nearest neighbors for a word.

View API


Sentence Embedding
Get a vector representation for any string and find similarity between two strings.

View API


Sentiment Analysis
Score text as positive, negative, or neutral based on the sentiment.

View API

Speech
Take advantage of speech recognition and saliency features for a variety of languages.

View Speech framework


Speech Recognition
Recognize and analyze speech in audio and get back data like transcripts.

View API

Sound Analysis
Analyze audio and recognize it as a particular type, such as laughter or applause.

View Sound Analysis framework


Sound Classification
Analyze sounds in audio using the built-in sound classifier or a custom Core ML sound classification model.

View API

[]

