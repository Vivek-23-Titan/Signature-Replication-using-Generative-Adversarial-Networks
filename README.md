# Signature-Replication-using-Generative-Adversarial-Networks
<a href="https://colab.research.google.com/github/Vivek-23-Titan/Covid-19-Masked-Face-Detection-using-YoloFace/blob/master/Copy_of_Signatures_CGAN.ipynb" target="_parent\"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

This IAS SRPF-2019 Project focuses on generating signatures along with their labels of 10 different people with the help of CGAN. With the help of a classifier, we can then classify those images when used as training data for the classifier. Also, with the help of multi-label classification, the transfer learning VGG19 model is able to separate the original real images from the generated fake ones.

## Dataset
The Dataset consists of 1000 signatures, subdivided into 10 different signature classes. Further information is available [here](http://www.reports.ias.ac.in/report/20439/signature-replication-and-fingerprint-bio-metric-forging-using-generative-adversarial-network).

## Code
The Code is available in the [Jupyter notebook](https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Copy_of_Signatures_CGAN.ipynb).

## Results
### The original and generated images
<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Signatures2.PNG" width=400> <img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Dataset_Gen_Signatures.PNG" width=400>

### The training history of Multi-Label Deep Convolutional Classifier
<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Training_History.PNG" width=450>

* The graph is underfitting due to high dropout of 0.6.

### Classification of validation/test set
3000 signature images were generated and classified using a CNN trained on the original 1000 signature dataset. The confusion matrix of the validation/test set is shown below.

<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Confusion_Matrix.PNG" width=500>

* The final accuracy achieved is 98%.

### Multi-Label Classification of the signatures into real and fake (with adversarial noise)
New datasets are formed by:
1. **Training data:** 400 real and 400 fake images.
2. **Validation data:** 100 real and 100 fake images.
3. **Test data:** 500 real and 500 fake images.

* The generated images consist of adversarial noise which helps a classifier (or discriminator model) to differentiate between real fake images.
* The Multi-Label ground truths consists of 10 one hot encoded vectors for each signature class and the 11th number for respresents 1 for real and 0 for fake signatures.
* Since Multi-Label classifications treats each output neuron as independent, hence sigmoid activation function with binary categorical loss is using for training.

### The training history of Multi-Label CNN trained on the new dataset

<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Training_History_99.8.PNG" width=700>

* The accuracies reach ~80% for training and ~90% for validation data, however these accuracies are based on **Sigmoid** activation function.

### Validation and Test dataset confusion matrix for classification

* Since the this is a classification problem, hence, for predicting **Softmax** (signature with highest probability is the output class) function can be employed in case of signature classes.

<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Confusion_Matrix_95.267_Precision_85.4_R.PNG" width=400>

## Requirements
Tensorflow 1.15
