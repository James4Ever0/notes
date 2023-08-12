---
tags: [CoreML, darling, hackintosh, paddlepaddle, Swift]
title: Deeplearning on MacOS M-series Processors
created: '2022-08-06T18:25:22.000Z'
modified: '2023-08-12T14:06:28.323Z'
---

# Deeplearning on MacOS M-series Processors

it is funny that macOS still supports AMD GPUs, means any intel Mac (not M-series!) can now utilize internal/external AMD GPUs as long as frameworks like [jax](https://developer.apple.com/metal/jax/) and [pytorch](https://pytorch.org/docs/stable/notes/mps.html) support MPS/Metal.

----

calling python code from swift using pythonkit:
```swift
    func downloadVideo(link: String){
        let sys = Python.import("sys")
        sys.path.append(dirPath)
        let example = Python.import("sample")
        let response = example.downloadVideo(link, dirPath)
        videoPath = String(response)
    }
```

[run macos in docker](https://github.com/sickcodes/Docker-OSX) with kvm

## neural engine

it is used for coreml inference, not training

## run coreml on hackintosh

first, download macos montery using the mac.
then, install it on hackintosh, with associated nvidia drivers.
next test gpu avalibility via system info panel.
then install xcode commandline tools and check coreml avalibility

## run coreml with swift on linux

darling is at its very premature stage, just like the wine. now it is testing something called "darlingserver" which is a full userspace implementation and is prone to tons of problems. swift repl is not working and installing xcode commandline tools 14 will hang this thing. i suggest you to do light model training on macbook air and convert it to onnx if want to use it everywhere.

before reinstallation of darling, make sure you have removed all darling related files by checking `updatedb; locate darling | grep -v <compile directory>`

visit [here](https://docs.darlinghq.org/build-instructions.html) to install darling from source (maybe that's the only way)

if want to install darling on kali, you must outsource all deeplearning models to other disks, and collect all other big files to somewhere else or trash them. use systemwide user broadcast method to warn me if any of the disk is missing. use automatic symlink change method to adapt the external disk mountpoint changes.

darling can [install xcode commandline tools with macos sdk](https://github.com/darlinghq/darling-docs/blob/master/src/installing-software.md#:~:text=To%20install%20command-line%20developer%20tools%20such%20as%20the,install%20only%20command-line%20tools%20from%20Apple%20by%20running), so maybe it can run coreml models with swift using cpu. gpu support is currently not known. maybe that requires metal support.

## thermal and battery life concerns, and more

consider [using external gpus (eGPUs) with thunderbolt 3 and AMD GPUs](https://support.apple.com/en-us/HT208544) to avoid overheating. currently that can only be done with intel Macs.

battery life is currently bad for intel/amd notebooks of x86/64 architecture.

heavy lifting jobs are likely to be run on Mac Studio with M1 Ultra and 128GB RAM. Macbook Air M1 with 8GB RAM is simply not feasible.

aside of Apple platforms, these APIs are virtually useless.

to run these on other non-apple machines, you need to tweak and install macOS on x86-64 platforms with macOS supported GPUs(may have low performance), which will definitely not taking any advantage of huge shared RAM with CPU, and may run poorly on CoreML/CreateML, may not support deepspeed stage 2/3 or BMI(big model inference)

<details><summary>Non-Supported NVIDIA Cards, use AMD GPU instead</summary>
High Sierra no longer supports NVIDIA Mac.
Mojave – Catalina – BigSur only works with AMD graphics and Intel onboard graphics and only a very small number of old NVIDIA products. Suppose you have GTX 1070, 1080, and the like, you can not use High Sierra onwards because Nvidia does not provide any updates for Mac and can not be used in any other way.
In general, the graphics of the Turing, Pascal, and Maxwell series will never be supported again. The latest Mac version that can use this series of graphics is High Sierra.
</details>

## tensorflow with m1 support

using [tensorflow metal plugin](https://developer.apple.com/metal/tensorflow-plugin/), which sets up miniforge and install tensorflow-metal within.

install without miniforge(works!)
```bash
pip3 install tensorflow-macos tensorflow-metal
```

validation:
```bash
python3 -c "import tensorflow as tf; physical_devices = tf.config.list_physical_devices('GPU'); print('Num GPUs:', len(physical_devices)); print(physical_devices)"
```

## pytorch with m1 support, using MPS (Metal performance shader)

install from nightly release channel, with minimum system version requirements 12.3 (which this machine had been qualified after system update, now 12.5)

```bash
# MPS acceleration is available on MacOS 12.3+
pip3 install --pre torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/nightly/cpu
```

validation
```bash
python3 -c "import torch; print('MPS avaliable:',torch.backends.mps.is_available()); print('Built with MPS:',torch.backends.mps.is_built())"
```

## run python inside swift

use [pythonkit](https://github.com/pvieito/PythonKit.git)

## automatic machine learning using CreateML

```swift
import CreateML
```

CreateML is similar to any other [AutoML](https://www.automl.org/automl/) tools, like [AutoKeras](https://autokeras.com/), [AutoTrain by Huggingface](https://huggingface.co/autotrain) (works by training against a selected set of user-provided models)

## using CoreML

[curated, largest coreml models collection](https://github.com/likedan/Awesome-CoreML-Models)

CoreML models can be created by CreateML and some customization can be done via `protocol MLCustomLayer`.

[onnxruntime](https://onnxruntime.ai/) can run onnx models on CoreML, via c#, since that library is maintained by microsoft.

to install c# on macos:
```bash
brew install dotnet-sdk
```

to install and launch [dotnet repl](https://github.com/jonsequitur/dotnet-repl):
```bash
dotnet tool install -g dotnet-repl
dotnet repl
```

## paddlepaddle support

convert into onnx first, then run on onnxruntime.

paddlepaddle itself currently only supports running on M1 CPU only via rosetta 2.

## Links

[Swift Core ML 3 implementations of GPT-2, DistilGPT-2, BERT, and DistilBERT for Question answering.](https://github.com/huggingface/swift-coreml-transformers)

[train image classifier and text classifier](https://www.appcoda.com/create-ml/) in which `CreateMLUI` is deprecated (gone)

[train source code classifier](https://flight.school/articles/classifying-programming-languages-with-createml/) with [flightschool](https://flight.school/) which is a free swift tutorial books provider

[classifying sounds with coreml](https://developer.apple.com/documentation/soundanalysis/classifying_sounds_in_an_audio_file) return sound type along with timestamp

[detect human pose using coreml](https://developer.apple.com/documentation/coreml/model_integration_samples/detecting_human_body_poses_in_an_image)

[apple speech recognization api request](https://developer.apple.com/documentation/speech/sfspeechrecognitionrequest)

[pytorch mps backend](https://pytorch.org/docs/stable/notes/mps.html)

[text classification using createml](https://heartbeat.comet.ml/text-classification-on-ios-using-create-ml-f71d7191404a)

[onnx model zoo](https://github.com/onnx/models)

[Getting CoreML Models](https://developer.apple.com/documentation/coreml/getting_a_core_ml_model)

[CoreML Model Zoo](https://developer.apple.com/machine-learning/models/)
<details>
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

[Apple Machine Learning Related APIs](https://developer.apple.com/machine-learning/api/) (may need user permission within or without xcode by means of Info.plist or something)
<details>
<p>
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
</p></details>
