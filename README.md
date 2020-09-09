# Signature-Replication-using-Generative-Adversarial-Networks

This IAS SRPF-2019 Project focuses on generating signatures along with their labels of 10 classes with the help of CGAN. To separate the signature classes and determine whether the signatures are genuine or generated (signatures with adversarial noise), multi-label classified is used. Also, when the adversarial noise is removed, with the help of a CNN classifier, the images can be classified into the 10 classes however, cannot distinguished as real or fake since, the classifiers exploit adversarial noise.

## Dataset
The Dataset consists of 1000 signatures, subdivided into 10 different signature classes. Further information is available [here](http://www.reports.ias.ac.in/report/20439/signature-replication-and-fingerprint-bio-metric-forging-using-generative-adversarial-network).

## Code

1. Multi-Label Classification (with adversarial noise): [Jupyter notebook](https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Multi_Label_Signatures_CGAN.ipynb).
2. Classification of real+fake images (without adversarial noise): [Jupyter notebook](https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Copy_of_Signatures_CGAN.ipynb).

## Results
### The original and generated images
<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Signatures2.PNG" width=400> <img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Dataset_Gen_Signatures.PNG" width=400>

### Multi-Label Classification of the signatures into real and fake (with adversarial noise)
New datasets are formed by:
1. **Training data:** 400 real and 400 fake images.
2. **Validation data:** 100 real and 100 fake images.
3. **Test data:** 500 real and 500 fake images.

* The generated images consist of adversarial noise which helps a classifier (or discriminator model) to differentiate between real fake images.
* The Multi-Label ground truths consists of 10 one hot encoded vectors for each signature class and the 11th number for respresents 1 for real and 0 for fake signatures.
* Since Multi-Label classifications treats each output neuron independently, hence sigmoid activation function with binary categorical loss is using for training.

### The training history of Multi-Label CNN trained on the new dataset

<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Training_History_99.8.PNG" width=500>

* The accuracies reach ~80% for training and ~90% for validation data, however these accuracies are based on **Sigmoid** activation function.
* The graph is underfitting due to high dropout of 0.6.

### Validation and Test dataset confusion matrix for classification

* Since the this is a classification problem, hence, for predicting **Softmax** (signature with highest probability is the output class) function can be employed in case of signature classes.

#### Signature Classification (Validation and Testing Data)

<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Signature_Confusion_Matrix_99.5.PNG" width=350><img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Confusion_Matrix_99.8.PNG" width=350>

&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Confusion_Matrix_Metrics_99.8.PNG" width=270>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Signature_Confusion_Matrix_Metrics_99.5.PNG" width=270>

* The Signature classification results for validation data is 99.5% and for 99.8% for test data respectively.

#### Real or Fake Classification (Validation and Testing Data)

<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Fake_Confusion_Matrix.PNG" width=300>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Fake_Confusion_Matrix_99.5.PNG" width=300>

* In case of real vs fake, for both the datasets, the classification accuracy remains 100%.

### The training history of Deep Convolutional Classifier

* A classifier can differentiate real images from images with adversarial noise, however,the images are stored or corresponding signature images are converted into the standard 256 gray intensity level.
* This results in the loss of adversial noise since the pixel values now take on discrete integer intensity values.
* After removing the adversarial noise, a regular CNN is trained on fake+real images, and the classifier (or the discriminator) can no longer distinguish real from fake images.

<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/CNN_history.PNG" width=450>

### Classification of validation/test set
3000 signature images were generated and classified using a CNN trained on the original 1000 signature dataset. The confusion matrix of the validation/test set is shown below.

<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Confusion_Matrix_0.9997.PNG" width=350>
<img src="https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Images/Confusion_Matrix_Metrics0.9997.PNG" width=300>


* The final accuracy achieved is 99.97%.

## Requirements
Tensorflow 2.3
