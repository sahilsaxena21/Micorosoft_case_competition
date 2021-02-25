# Microsoft Case Competition

## Business Problem

| Challenge | Status Quo  | Proposed AI Solution  |
| ---   | :-: | :-: |
| Gap 1: Lack of understanding of the quality of customer in-store experience | In-store sales data | Combine with in-store video analytics |
| Gap 2: Personalizing the customer experience through mobile app | Not addressed | Recommender system in mobile app |

## Project Success Metrics

The success metrics of the proposed AI solution are:
1)	Maximize conversion rate 
2)	Maximize total ticket from the sale


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

## Dataset

### Inputs to AI Models

The following data will be used as input to the proposed AI solution:

*	In-store and mobile app transactions and other activity performed by the customer (orders, returns, exchanges)
*	Product and service list with detailed descriptions
*	Video recordings gathered from in-store surveillance system

### Outputs by AI Models

The following data will be the output from the proposed AI solution:

*	In-store customer age and gender
*	Dwell time of customer-product interactions
*	Footfall traffic

## Technical Implementation Overview

### Content-Based Recommendation Engine Feature

![Video Analytics](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/prototype_architecture.png)

The proposed architecture as illustrated above. The architecture is specifically designed to be scalable. 

As a demonstration of the technical feasibility of our proposed solution, we use a synthetic dataset adapted from the Criteo dataset, a well known dataset of website ads that can be used to optimize the Click-Through Rate (CTR). The dataset contains a record of historic customer purchases, which is thought to be readily available from the organization’s database. We then test the performance of the recommender engine on the sample dataset. The table below outlines the model performance results.

| evaluation_type | Precision  | Recall  | F1-Score  |
| ---   | :-: | :-: | :-:  |
| Classification | 0.83 | 0.83 | 0.83  |

Please refer to the two notebooks as follows:
1) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/mmlspark_lightgbm_prototype.ipynb) for collecting the synthetic dataset and training a **LightGBM** model
2) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/lightgbm_prototype.ipynb) for deploying the model on **Azure Kubernetes Service** 

### Video Analytics Feature

![Video Analytics](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/sample_image_read.JPG)

As illustrated in the above figure, **Azure's Computer Vision Analyze** Image Rest API is used to extract the following metadata from the sample image provided:
*	Extracts the number of people from a given image
*	Extracts the demographics information such as age and gender
*	Extracts the location of the person within the store using bounding box coordinates

Please refer to the [notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/image_analytics.ipynb) for the code implementing this app feature

## Insights from App

Please refer to the [Sample Dashboard](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Sample%20Dashboard.pdf) for an illustration of the insights gathered from our App.
