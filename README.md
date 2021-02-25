# Microsoft Retail Analytics Case Competition
In this competition, teams were challenged to envision an AI use case within the retail and ecommerce space and then demonstrate its technical feasibility by developing a prototype using Microsoft Azure's Cloud Services. 

The product was judged in various categories including **orginality**, **technical feasibility** and **impact potential**.

Team Result: Top 15% out of 300+ submissions

## Business Opportunity

Target Customer: Best Buy Canada

| Business Opportunity | Status Quo  | Proposed AI Solution  |
| ---   | :-: | :-: |
| Understand the quality of customer in-store experience | In-store sales data | Combine with in-store video analytics |
| Personalize the customer experience through mobile app | Not addressed | Recommender system in mobile app |

## Project Success Metrics

1)	Maximize conversion rate 
2)	Maximize total ticket from the sale


## Dataset

The following data will be used as input to the proposed AI solution:

* Images from video recordings gathered from the in-store surveillance system
* In-store and mobile app transactions and other activity performed by the customer (orders, returns, exchanges)
*	Product and service list with detailed descriptions

## Minimum Viable Product

The following product features were selected for the Minimum Viable Product (MVP):

*	Personalizer App: Classifer model to understand a customer's affinity to a product category
*	Video Analytics: In-store customer's age and gender, footfall traffic, Store hot zones

## Technical Implementation Overview

### Content-Based Recommendation Engine Feature

Please refer to the two notebooks as follows:
1) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/mmlspark_lightgbm_prototype.ipynb) for collecting the synthetic dataset and training a **LightGBM** classifer model
2) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/lightgbm_prototype.ipynb) for deploying the model on **Azure Kubernetes Service** 

![Video Analytics](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/prototype_architecture.png)

The proposed architecture is as illustrated above. The following Azure services are used in the above Notebooks:

* **Azure Blob Storage** is a storage service optimized for storing massive amounts of unstructured data. In this case, the input data is stored here.
* **Azure Databricks** is a managed Apache Spark cluster where model training and evaluating is performed.
* **Azure Machine Learning service** is used in this scenario to register the machine learning model.
* **Azure Container Registry** is used to package the scoring script as a container image which is used to serve the model in production.
* **Azure Kubernetes Service** is used to deploy the trained models to web or app services.

For demonstration purposes, our app uses a synthetic dataset adapted from the Criteo dataset. A sample of the dataset is as provided below. The dataset contains a record of historic customer purchases through the Best Buy mobile app, which is thought to be readily available in the organization's database. We then build a classification model to predict the **product category** that a customer shows the highest affinity towards.

| Customer ID | Customer Name  | Product Category  | Purchase Value  |
| ---   | :-: | :-: | :-:  |
| 325478 | Gary Roberts | Video Game and Accessories | $50.45  |
| 325479 | Darryn Fynn | Karaoke Audio and Recording | $150.69  |
| 325480 | Frank Stable | Wearable Tech, Health and Fitness | $20.20  |
| 325481 | Hiba Tsonga | Outdoor Living | $20.60  |

### Video Analytics Feature
Please refer to the [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/image_analytics.ipynb) for the code implementing this app feature

![Video Analytics](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/sample_image_read.png)

As illustrated in the above figure, **Azure's Computer Vision Analyze Image Rest API** is able to extract the following metadata from the sample image provided:
*	the number of people from a given image
*	age and gender of each person
*	the location of the person within the store using bounding box coordinates. This is then mapped to particular areas within the store.

## Benefits of Proposed Approach
Our value proposition strives to capture the “low-hanging fruits” using AI i.e. high ratio of impact-to-implementation effort. Please refer to the attached [Customer Journey Theoretical Framework](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf) that forms the basis of our proposed AI solution. Reference to this Framework is made in the discussion below.

**Video Analytics (Azure Computer Vision Analyze Image Rest API)**

*	Most Best Buy stores already have an in-store surveillance system in place. This makes the proposed solution **readily adoptable**.
*	The AI extension to the current approach provides the decision makers with **the power to run tests to quantify the impact** of change in pricing, rewards/points, product display and promotions on the customer in-store experience.
*	The AI solution will achieve this by **measuring footfall traffic** and capturing the **hot spots** within the store to answer key questions such as: Why are customers visiting my store?
*	Improved visibility on the [trigger questions](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf) the customers are entering the store with.

Note: The entire video analytics process will be **anonymized** i.e. customers will NOT be ID’d to protect their privacy. Only their age and gender (as detected by MS Computer Vision) will be identified. Acceptable privacy and security standards will be identified and applied to the analytics process and data storage.

**App Recommender System (Azure Machine Learning)**

*	Personalized shopping experiences are delivered through **tailored product recommendations** to optimally support the customer through the **“active evaluation”** phase to maximize probability of arriving at the [moment of commitment](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf). It will also be designed to trigger new [moments of inspiration](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf)

## Product Vision
Please refer to the [Sample Dashboard](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Sample%20Dashboard.pdf) that illustrates the potential features that can be added to the app and the insights it'll provide to our target customer.
