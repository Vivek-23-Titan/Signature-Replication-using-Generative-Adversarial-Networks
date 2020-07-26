# Signature-Replication-using-Generative-Adversarial-Networks

This Project focuses on generating signatures along with their labels of 10 different people with the help of CGAN. With the help of a classifier, we can then classify those images as well as see their effects when used as training data for the classifier.

### Dataset
The Dataset consists of 1000 signatures, subdivided into 10 different signature classes.

### Code
The Code is available in the [Jupyter notebook](https://github.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/blob/master/Copy_of_Signatures_CGAN.ipynb).

### Results
#### The generated and original images
<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Signatures1.PNG" width=400> <img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Signatures2.PNG" width=400>

##### The training history of Deep Convolutional Classifier trained on generated data and validated on original data
<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/Training_History.PNG" width=450>
The graph is underfitting due to high dropout of 0.6.

#### Confusion matrix of the validation data/test data

<img src="https://raw.githubusercontent.com/Vivek-23-Titan/Signature-Replication-using-Generative-Adversarial-Networks/master/Images/GAN_Confusion_Matrix.PNG" width=600>
The accuracy achieved is 98%.

### Requirements
Tensorflow 1.15
