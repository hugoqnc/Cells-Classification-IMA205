# Pap smear cells classification

## Introduction
The goal of this project is to classify images of cells first in a binary way (cancerous cells or not), then in multi-classes. This is achieved using Machine Learning, Probabilistic Models and Neural Networks.

To classify these images, there are two main steps. First, we have to find features that characterize the images and that allow us to discriminate them according to their classes. Then, once these features are found, we have to find a way to separate the space of features: we determine a classifier from the training set. This will then allow us to make class predictions on the test images.

## Quick Start
There are two Python Jupyter Notebooks.

The first one, [`Binary_Code.ipynb`](Binary_Code.ipynb) which predicts the *normal* or *abnormal* state of the cell.

The second Jupyter Notebook, [`Multi_Code.ipynb`](Multi_Code.ipynb) predicts the classe of the cell among 7 detailed classes :
|Class| Category|Cell type|
|---|---|---|
1| Normal|Superficial squamous epithelial
2| Normal|Intermediate squamous epithelial
3| Normal|Columnar epithelial
4| Abnormal|Mild squamous non-keratinizing dysplasia
5| Abnormal|Moderate squamous non-keratinizing dysplasia
6| Abnormal|Severe squamous non-keratinizing dysplasia
7| Abnormal|Squamous cell carcinoma in situ intermediate

To use these Notebooks, you need to put Train images in `./Train/Train/`. For an image with the ID 64, the folder should contain the color image `64.bmp`, its cytoplasm segmentation `64_segCyt.bmp` and its nucleus segmentation `64_segNuc.bmp`. Same thing for the Test images, in the folder `./Test/Test/`.

For the train set, the Notebooks also need a CSV file `metadataTrain.csv` with columns *ID*, *ABNORMAL* (0 or 1) and *GROUP* (0 to 6).

The Notebooks will give you the option between showing accuracy results based on a split of the Train set, or exporting a CSV file with prediction of the actual Test set.


## Data
Data comes from two publicly available data-sets: the [DTU/HERLEV](https://mde-lab.aegean.gr/downloads) database and the [SIPaKMeD](https://www.cs.uoi.gr/~marina/sipakmed.html) database.

## Choice of features
I have used the following features : `mean_intensity`, `max_intensity`, `min_intensity`, `area`, `equivalent_diameter`, `perimeter`, `euler_number`, `centroid`, `solidity` from `measure.regionprops` in `skimage`.

## Results
Finally, I obtained good results with Non-linear SVM, Histogram Gradient Boosting, and MLP, which allow me to make **correct predictions in 96% of the cases** for the binary prediction, and 87% for the multi-class prediction.

You will find more details in the complete [report (in French)](Report.pdf).
