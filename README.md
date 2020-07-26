# Signature-Replication-using-Generative-Adversarial-Networks

This IAS SRPF-2019 Project focuses on generating signatures along with their labels of 10 different people with the help of CGAN. With the help of a classifier, we can then classify those images as well as see their effects when used as training data for the classifier.

## Dataset
The Dataset consists of 1000 signatures, subdivided into 10 different signature classes. Further information is available [here](http://www.reports.ias.ac.in/report/20439/signature-replication-and-fingerprint-bio-metric-forging-using-generative-adversarial-network)

## Code
The Code is available in the [Jupyter notebook](https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Copy_of_Signatures_CGAN.ipynb).

## Results
### The original and generated images
<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Signatures2.PNG" width=400> <img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Signatures1.PNG" width=400>

#### The training history of Deep Convolutional Classifier trained on generated data and validated on original data
<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Training_History.PNG" width=450>

* The graph is underfitting due to high dropout of 0.6.

### Classification of validation/test set
3000 signature images were generated and classified using a CNN trained on the original 1000 signature dataset. The confusion matrix of the validation/test set is shown below.

<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Confusion_Matrix.PNG" width=600>

* The final accuracy achieved is 98%.

## Requirements
Tensorflow 1.15
