# ***Clustering In Melanoma Cancer Detection***

***Abstract*** — The latest skin cancer data shows that Melanoma of skin is the 17th most common cancer worldwide. This report explores the application of KMeans clustering and MobileNetV2 for the classification of skin cancer images, addressing the need for effective diagnostic tools in dermatology. By implementing KMeans clustering, the project aims to segment skin lesion images into groups indicative of benign or malignant characteristics, enhancing the accuracy of preliminary diagnoses. The integration of the MobileNetV2 is used for its efficiency and high performance in extracting features. Additionally, Principal Component Analysis (PCA) is used to condense the feature set into a two-dimensional format for easier visualization and analysis. Results showed that clustering, particularly KMeans clustering, proved to be effective given the higher overall score for the segmented image cluster and the improved performance in CNN.

***Keywords*** — KMeans clustering, feature extraction, machine learning applications,  skin cancer classification

---

This is a repository for my group's final project in the Machine Learning class, aimed towards advanced use in clustering algorithms. This project aims to use KMeans Clustering and observe its performance in preprocessing and classification. The method used is performing clustering on extracted features on the melanoma cancer images, on both preprocessed and not preprocessed images. The flow of the overall project can be seen in fig. 1 below. 

![Project FlowChart](docs/flowchart.png?raw=true "Project FlowChart")

*fig 1.0: project flowchart*

---
### ***Data Acquisition***

The dataset used in this project is from the [Melanoma Cancer Dataset](https://www.kaggle.com/datasets/bhaveshmittal/melanoma-cancer-dataset) from Kaggle. 

![dataset](docs/dataset.png?raw=true "dataset")

*fig 2.0: dataset*

For this particular project, only 100 images from each class are taken to reduce computational burden. 

---
### ***Data Preprocessing***

The main preprocessing methods used in this project is image segmentation, in addition to grayscaling. The image segmentation method uses KMeans Clustering, and to find the optimal KMeans Clustering, Silhouette Analysis and Elbow Method is performed. 

![Elbow](docs/elbow.png?raw=true "elbow")

*fig 3.0: elbow method for clusters*

![Silhouette](docs/silhouette.png?raw=true "Silhouette")

*fig 3.1: silhouette analysis for clusters*

Finally, after a few manual testing, 5 clusters are used for this stage. 

---
### ***Feature Extraction***

This project utilizes Transfer Learning for feature extraction. The [MobileNetV2](https://keras.io/api/applications/mobilenet/) pre-trained model is used as it is efficient and yields high performance. The output of this stage is features mapped in  the form of arrays. This will be the input for the clustering. 

---
### ***Clustering for Classification***

After getting the image features mapped in array, the dimensionality is reduced into 2 for efficient two-dimensional clustering. The method used of dimensionality reduction is the PCA. The clustering in this stage aims to cluster similar images/features together, ideally Malignant with Malignant and Benign with Benign. The output can be seen in fig 4.0 and 4.1.

![segmented](docs/segmented.png?raw=true "segmented")

*fig 4.0: PCA and Clustering of segmented images*

![ori](docs/clusori.png?raw=true "ori")

*fig 4.1: PCA and Clustering of original images*

---
### ***Validation using CNN***

To strengthen the findings in the classification section, predictions using CNN is implemented. The method used is once again Transfer Learning, using MobileNetV2 with extra layers for specialization towards this dataset. 

---
### ***Evaluation, Results, and Discussion***

The results of classification using clustering is evaluated using Purity and Silhouette Score of the clusters. It can be seen in table 1.0 below.

|    **Cluster**   | **Segmented Images Cluster** | **Original Images Cluster** |
|:----------------:|:----------------------------:|:---------------------------:|
|      Purity      |             0.695            |            0.715            |
| Silhouette Score |             0.187            |            0.054            |

*table 1.0: cluster evaluation*   

Given the information above, we can conclude that the segmented images made better clusters that Original Images clusters. 
This means similar images/features are better clustered after clustering as preprocessing is performed. In addition to that, evaluations of validation with CNN using confusion matrixes can be seen in fig 5.0 and 5.1 below. 

![confseg](docs/confseg.png?raw=true "conf seg")

*fig 5.0: confusion image of segmented images*

![conf ori](docs/ori.png?raw=true "conf ori")

*fig 5.1: confusion matrix of original images*


Using the trained model for final predictions, the model performed with 82% accuracy on original images, but 87% on segmented images, proving contributions of Clustering algorithms in Classification. 
