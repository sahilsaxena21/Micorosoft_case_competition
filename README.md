# Microsoft Retail Analytics Case Competition
Teams were challenged to envision an AI use case within the retail and ecommerce space and then demonstrate its technical feasibility by developing a prototype using Microsoft Azure's Cloud Services. 

The product was judged in various categories including **orginality**, **technical feasibility** and **impact potential**.

Our Team's Result: Top 15% out of 300+ submissions

# Our Team's Submission

The following provides a summary of our team's selected AI use case, and provides an overview of our technical impelementation.

## Business Opportunity

Target Customer: Best Buy Canada

| Business Opportunity | Status Quo  | Proposed AI Solution  |
| ---   | :-: | :-: |
| Understand the quality of customer in-store experience | In-store sales data | Combine with in-store video analytics |
| Personalize the customer experience through mobile app | Not addressed | Recommender system in mobile app |

## Project Success Metrics

1)	Maximize conversion rate 
2)	Maximize total ticket from the sale

## Technical Implementation Overview

| Proposed AI Solution | Input Data  | Demonstrating Technical Feasbility  |
| ---   | --- | --- |
| Video Analytics |  Images from video recordings gathered from the in-store surveillance system | Extract in-store customer's age, gender, and the location of the detected person within the store, mapped to pre-defined sections of the store (e.g isle #, cashier queues etc.) |
| Mobile App Product Recommendations | Historic customer purchase data through mobile app, product listing with detailed descriptions | Probabilistic classifier that ranks a customer's affinity to product categories |

### Prototype Architecture

![Prototype Architecture](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/prototype_architecture.png)

The architecture employed to demonstrate technical feasbility of this idea is as illustrated above. The protytype architecture uses the following Azure services:

* **Azure Blob Storage**
* **Azure Databricks**
* **Azure Machine Learning service**
* **Azure Container Registry**
* **Azure Kubernetes Service**

### Content-Based Recommendation Engine Feature

Please refer to the two notebooks demonstrating technical feasbility of this feature as below:
1) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/mmlspark_lightgbm_prototype.ipynb) for collecting the synthetic dataset and training a **LightGBM** classifer model
2) [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/lightgbm_prototype.ipynb) for deploying the model on **Azure Kubernetes Services** 

### Video Analytics Feature
Please refer to the [Notebook](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/image_analytics.ipynb) demonstrating technical feasibility of this feature.

![Video Analytics](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/images/sample_image_read.png)

As illustrated in the above figure, **Azure's Computer Vision Analyze Image Rest API** is able to extract the following metadata from the [sample image](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/img_1_jpeg.jpg) provided:
* age and gender of detected individuals in the input image
*	the location of the person within the store using bounding box coordinates. This is then mapped to particular areas within the store.

## Benefits of Proposed Approach
Please refer to the [Customer Journey Theoretical Framework](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf) that forms the basis of our proposed AI solution. Reference to this Framework is made in the discussion below.

**Video Analytics (Azure Computer Vision Analyze Image Rest API)**

*	Most Best Buy stores already have an in-store surveillance system in place. This makes the proposed solution **readily adoptable**.
*	The AI extension to the current approach provides the decision makers with **the power to design tests to quantify the impact** of change in pricing, rewards/points, product display and promotions on the customer in-store experience. This can be tracked by monitoring changes in footfall traffic in areas within the store.
*	Footfall traffic analytics provides improved visibility on the [trigger questions](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf) the customers are entering the store with.

**App Recommender System (Azure Machine Learning)**

*	Personalized shopping experiences are delivered through **tailored product recommendations** to optimally support the customer through the **“active evaluation”** phase to maximize probability of arriving at the [moment of commitment](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf). It will also be designed to trigger new [moments of inspiration](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Customer%20Journey%20Theoretical%20Framework.pdf)

## Product Impact Demonstration
Please refer to the [Sample Dashboard](https://github.com/sahilsaxena21/case_competition_microsoft/blob/master/Sample%20Dashboard.pdf) illustrating the type of insights our app has the potential to unlock for our target customer i.e. Best Buy.
