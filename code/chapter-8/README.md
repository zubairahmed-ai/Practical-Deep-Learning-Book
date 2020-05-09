# Code for Chapter 8: Cloud APIs for Computer Vision: Up and Running in 15 Minutes

Work smart, not hard. We utilize the power of cloud AI platforms from Google, Microsoft, Amazon, IBM and Clarifai in under 15 minutes. For tasks not solved with existing APIs, we then use custom classification services to train classifiers without coding. And then we pit them against each other in an open benchmark, you might be surprised who won. [Read online here.](https://learning.oreilly.com/library/view/practical-deep-learning/9781492034858/ch08.html)

## Code

In this chapter, we will be going through two experiments of image tagging or object recognition, and optical character recognition (OCR). Image tagging helps us understand what objects are present inside an image. OCR helps decipher the characters present in an image. We will be uploading images from the MSCOCO dataset to various cloud providers and comparing the results.

We will be using the Google, Microsoft, and Amazon cloud providers to test for image tagging and optical character recognition. Please sure you register and generate an API key for each and replace it in the [`script.py`](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/experiment-scripts/script.py).

In addition, if you want to experiment with Clarifai and IBM Watson, please install their packages using:

```
pip install clarifai
pip install --upgrade watson-developer-cloud
```
And, add their corresponding API keys to the `script.py`.

### Optical Character Recognition

1. [1-get-MSCOCO-validation-image-ids-with-legible-text.ipynb](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/optical-character-recognition/1-get-MSCOCO-validation-image-ids-with-legible-text.ipynb): We will develop a dataset of images from the MSCOCO dataset that contain at least a single instance of legible text and are in the validation split.

2. [2-test-ocr-from-cloud-providers.ipynb](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/optical-character-recognition/2-test-ocr-from-cloud-providers.ipynb):This code sample details how one image and a directory of images can be uploaded to various cloud providers using the [`script.py`](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/experiment-scripts/script.py). We will be using this script for both the OCR and image tagging experiments. This file is fairly generic and is intended to explain the usage of `script.py`.

3. [3-upload-validation-images-to-cloud-providers.ipynb](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/optical-character-recognition/3-upload-validation-images-to-cloud-providers.ipynb): In this file we will gather the data that enables us to do the benchmarking.

4. [4-compile-ground-truth-ocr.ipynb](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/optical-character-recognition/4-compile-ground-truth-ocr.ipynb): In this file we will compile the ground truth for all the test images.

5. [5-compile-results-ocr.ipynb](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/optical-character-recognition/5-compile-results-ocr.ipynb): In this file we will compile the results using the ground truth and the collected data for all the test images. Each cloud provider sends the results in slightly different formats and we need to parse each of them correctly. So, we will develop a parsing function unique to each cloud provider in this file as well.

### Image Tagging

1. [1-setup.ipynb](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/image-tagging/1-setup.ipynb): Compile the intermediate files that we need for the benchmarking.

2. [2-compile-ground-truth-tags.ipynb](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/image-tagging/2-compile-ground-truth-tags.ipynb): Compile the ground truth for all the test images.

3. [3-upload-validation-images-to-cloud-providers.ipynb](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/image-tagging/3-upload-validation-images-to-cloud-providers.ipynb
): Gather the data that enables us to do the benchmarking. We will be using the Google, Microsoft, and Amazon cloud providers

4. [4-compile-results-tags.ipynb](https://github.com/PracticalDL/Practical-Deep-Learning-Book/blob/master/code/chapter-8/image-tagging/4-compile-results-tags.ipynb): Compile the final results by comparing ground truth against the received predictions.

## Data

Please download both the MSCOCO images, available on the [MSCOCO project website](http://mscoco.org/dataset/#download). To make experimentation seamless, we have also provided the predictions obtained from our runs in August 2019 in the `data` directory.

### Optical Character Recognition

We will be using the COCO-Text dataset for Optical Character Recognition. We will utilize its Python API for loading and parsing the annotations. More information on the COCO-Text dataset is available on its [website](http://vision.cornell.edu/se3/coco-text/). Please download the API. The various files that we will be utilizing from COCO-Text are:

1. `cocotext.v2.json`: Please download this file and update the path in the corresponding notebooks.
2. `coco_evaluation.py`
3. `coco_text.py`: This file is being imported in various notebooks. Please make sure that this file is available in the same folder as the notebooks.

Please download the text annotations from the [coco-text website](https://bgshih.github.io/cocotext/).

### Image Tagging

Please download Gensim, which we will be using for comparing word similarity between ground truth with predicted class. The paths to the `GoogleNews-vectors-negative300.bin` will need to be updated in the corresponding notebooks.
