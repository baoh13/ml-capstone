# Machine Learning Engineer Nanodegree July 2020

## Capstone Proposal
Bao Hoang
July 13, 2020

## Proposal 

## Domain Background

Customer acquisition process is vital for companies to grow their customer base. In this project, a mail-order sales company wants to identify segments of the general population to target with their marketing campaigns. To create customer segments, demographics information of the general population and existing customers has been provided. Furthuremore, the project will also identify the individuals who are most likely to responsd to a campaign and become new customers using response data of targeted customers through mailout marketing campaigns.


## Problem Statement

To complete the project, the following steps will be done:
- Customer Segmentation report
    Demographics information of the general population and established customers are provided. We will use unsupervised learning methods to analyze the dataset attributes to create customer segments.
- Supervised learning model
    Using a third dataset with customer responses from a mail-order campaign, we will use the previous analysis to build a machine learning model to predict whether an individual will respond and become a new customer or not. 
- Kaggle competition
    Lastly, the supervised machine learning model will be used to make predictions on the campaign data and see how likely the individuals are to become customers.


## Datasets & Inputs

There are 4 datasets which are used in this project:

- 'Udacity_AZDIAS_052018.csv': Demographics information of the general population of Germany; 891 211 rows x 366 features
- 'Udacity_CUSTOMERS_052018.csv': Demographics information of the existing customers; 191 652 rows x 369 features 
- 'Udacity_MAILOUT_052018_TRAIN.csv': Demographics information of individuals who were targeted by a marketing campaign; 42 982 rows * 367 features
- 'Udacity_MAILOUT_052018_TEST.csv': Demographics information of individuals who were targeted by a marketing campaign; 42 833 rows * 366 features

Each row of the datasets represent a single person. It includes personal information such as household, building, neighborhood, etc. 'CUSTOMER' dataset has extra information about the customers such as ('CUSTOMER_GROUP', 'ONLINE_PURCHASE', 'PRODUCT_GROUP'). The 'TRAIN' dataset has 'RESPONSE' column which indicates whether the person has become a customer or not. This 'RESPONSE' column has been removed in 'TEST' dataset, the model will be scored in the Kaggle competition for its 'RESPONSE' predictions 


## Solution

In this project, we will first use a unsupervised learning model to create customer segments analysis using the 2 datasets 'AZDIAS' and 'CUSTOMERS' based on how similar to or differ from the general population. That customer segment analysis is then used to build a machine learning model to predict if a target person is likely to response to the marketing campaign using a supervised learning model and 'TRAIN' dataset with responses from a campaign. The 'TEST' dataset will then be used to score the model by its predictions. 

## Evaluation Metrics

AUC for the ROC curve is used as evaluation metrics. The plot will show the model's performance. It starts by accepting no individuals as customers the gradually increase the threshold for accepting customers until all individuals are accepted. The AUC (area under the curve) summerizes the performance of the model. 


## Project Design 

The project will go through a number of steps:

- Customer Segmentation Report
    - Data loading and exploration: 
        I would need to understand the features in the 'AZDIAS' and 'CUSTOMERS' datasets however there are 369 features so I need to figure which features are important and which are not. 
    - Data cleaning and pre-processing
        I need to evaluate missing data in each attribute and row. The data needs to be pre-processed and clean. 
        I also need to think which features I can drop and which I can keep. How many data types are there in the dataset? Do I need to transform them? 
        The data will also need to be normalized 
    - Dimensionality reduction with PCA
        I am going to use PCA to reduce the number of features within the dataset and thanks to that I will be able to test and pick the top n components 
    - Feature engineering and data transformation 
        From the n components in the previous step, I have transformed the original dataset into a n PCA components and the data is ready to be fed into K-Means model for clustering 
    - Clustering transformed data with k-means
        Using a K-Means model, I can cluster the transformed data 
    - Extracting trained model attributes and visualizing k clusters
        By visualizing k clusters, I can analyse the similarities of the 2 original datasets 'AZDIAS' and 'CUSTOMERS' to identify which features the 2 datasets have in common.

- Supervised model part
    - Data loading and exploration: 
        I will need to explore the dataset which can be imbalanced in regards to RESPONSES
    - Using different supervised algorithms to train 'TRAIN' dataset
    - Test the 'TEST' dataset and improve the performance
