**Image_Forgery_Detection**

**DSCI-6011-03-DL-Project**

**DL Final Project on Image Forgery Detection using Transfer Learning**

In the digital age, the manipulation and dissemination of visual content have become ubiquitous, giving rise to the critical challenge of ensuring the authenticity and integrity of digital images. The project, "Image Forgery Detection Using Transfer Learning" addresses this pressing concern by presenting an innovative solution that leverages the power of deep learning and advanced image analysis techniques to detect image forgeries.

As the use of image editing tools and the ease of digital content creation continue to expand, the potential for digital image manipulation, alteration, and forgery has never been greater. This poses serious implications for various domains, including journalism, forensics, social media, and e-commerce, where the credibility of visual content is paramount. It is imperative to develop robust and reliable methods for detecting manipulated images to safeguard trust and ensure the integrity of digital visual information.

The proposed project takes a multi-faceted approach to digital image forgery detection, combining Convolutional Neural Networks (CNNs), a cutting-edge deep learning architecture, with Error Level Analysis (ELA), a powerful image analysis technique. By synergizing these methods, the system aims to excel in identifying tampered images, distinguishing between authentic and manipulated content with a high degree of accuracy and robustness.

**Project Structure**:

Image_foergery_detection.py: This have all the code

Requirements.txt: Contains the requirements of the project

**System Overview**

The pipeline of the system is:

a. Train the CNN with image patches close to the distribution of the images that the network will work on. The training patches contain both tampered and untampered regions from the corresponding images.

b. Extract features from unseen images by breaking them into patches and applying feature fusion after the final convolutional layer of the network.

c. Use an SVM classifier on the 400 extracted features of the previous step for the final classification.

The high-level pipeline is shown in the following image:

![image](https://github.com/Yegnesh135/Image_Forgery_Detection/assets/115040502/fd8f3606-96d7-46cd-acf8-f5a18fdfb8e5)


**Network Architecture**

The CNN architecture of this project is shown in the image below. The network structure is 2 convolutions, max pooling, 4 convolutions, max pooling and then 3 convolutions. In the training phase, after the final convolution, a fully connected layer with softmax is applied. In the testing phase, the 400-D output of the final convolutional layer is used in the next Feature Fusion step that creates the feature vectors.

![image](https://github.com/Yegnesh135/Image_Forgery_Detection/assets/115040502/61be4e0b-846c-4abb-98bc-f363861169b3)

**Feature Extraction**

In order to create a feature representation of an image during the test phase, 224*224 patches are extracted and passed through the network. After this procedure, those feature maps are being exported. These feature maps are fused into one feature vector for each image either using max or mean fusion.

**Classification Using SVM**

For the final part of the pipeline an SVM classifier is trained and tested using the 400-D representations from the previous step. In particular, we use stratified 10-fold cross-validation to obtain an unbiased error estimate.



