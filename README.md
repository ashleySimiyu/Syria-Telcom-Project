# SyriaTel Customer Churn, Models built to predict Customer churn


## Overview
SyriaTel is a telecommunication company which provides state of the art communication services. However, it is grappling with a challenge of customers churning. The business is facing revenue losses as a result of customers terminating their subscription. The primary goal of this project is to analyse the factors fueling customer churn and build a predictive model to identify patterns and indicators of the customers likely to churn soon. The target stakeholders are executives, product managers, marketing teams, finance and account teams, and contact centre team at Syria Tel. The data used can be accessed from [here](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset)


## Business Problem

SyriaTel has noticed that customers are terminating their services, which has resulted in the company's loss of revenue and decreased market share. The stakeholders are afraid that this may eventually damage the company's brand. It is imperative to understand the factors driving the rate of customer churn before they can implement strategies to retain subscribers. The problem at hand is to develop a classifier model based on historical customer data to analyse churn patterns and predict the users at risk of unsubscribing. This will enable the company to implement various retention startegies, improve customer satisfaction, and eventually lessen the overall impact of turnover on its operations.

For this challenge, the project will explore various types of classification models like logistic regression, decision trees and random forests. These algorithms are ideal as we are predicting binary outcomes, that is, customer churn or no customer churn.



### The Dataset Understanding

We will use historical data from SyriaTel which contain information about customer call data obtained from [Kaggle](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset). The dataset has numerous features like user phone numbers, total calls, total call durations, state, customers churning e.t.c.distributed across 21 columns with 3333 records.

#### Data understanding 
We investigated the data to identify:
- Previewed the dataset.
- Checked the data types.
- Checked the correlation between the data columns.
- Viewed the unique value counts in each column.

#### Data preparation
- We dropped unnecessary columns eg the phone numbers
- Checked for missing values and duplicates which were not there.
- We converted categorical data to numeric data e.g. voice mail plan, international plan.
- We converted boolean to numeric.
- We checked for multicollinearity e.g. churn

#### EDA
International plan and Voice mail plan Usage

![Image]('./images/pie_chart_int_voice_plans.png')

International plan'9.7% of the customers do use the international plans while 27.7% use the voice mail plan

##### States in relation to churn
 Churn distribution based on the top 10 states

![Image]('./images/top_10_states.png')
The states with the highest churn rates include MN, NY, CT. However, there isn't a definitive explanation for why certain states outperform others in this regard, prompting a shift to analyzing regions instead.

###### Churn distribution based on the customer service calls
![Image]('./images/churn_customer_service.png')

As the number of customer service calls increases, the likelihood of churning also increases. Above 4 calls, the churn rate increases.

##### Customer service calls and are codes in relation to churn
![Images]('./images/churn_customer_service_boxplot.png')
Churn rate based on the customer service calls and the area codes

Area Code 415 & 510 have a high customer service calls which in turn have a high churn rate



## Modeling that works the best
For Classification modeling we used Logistic Regression, K-Nearest Neighbours, Decision Trees,  Random Forest. With the final model was a Random Forest classifier hyperparameter tuned, which can predict customer churn with The performs the best with an AUC score of 94%.


#### Logistic Regression
Based on these metrics, it seems like the resampled data with SMOTE has slightly better performance compared to the other datasets, especially in terms of recall and F1-score.Resampled Data with SMOTE balancing :Testing Accuracy: 75.0%,Testing F1-Score: 45.5%.
Original: Testing Accuracy: 68.2%,Testing F1-Score: 45.6%.Resampled Data: Testing Accuracy: 75.4%Testing F1-Score: 45.2%.These results suggest that the resampled data with SMOTE technique slightly outperforms the other datasets in terms of model evaluation metrics.
For logistic we have to consider the limitations of each approach when selecting the best model for your specific hence the need to explore other techniques or algorithms may be necessary to further improve model performance.


#### K-Nearest Neighbours
Imbalanced Data: The model performed poorly on the imbalaced data, with an accuracy score of 22%. The precision of 78% shows that the able is able to identify true positives in the prediction. However, the recall score of 36% suggests a poor ability to capture all actual positive cases. The F1 score of 50% balances precision and recall.Fine Tuning: This was done on a balanced dataset Hyperparameter tuning using cross validation led to a refined model with an AUC score 98%. The accuracy of 90.72% shows a successful generalization to unseen data, decreasing the risk of overfitting


#### Decision Trees
The decision tree model trained on scaled data exhibited the highest testing accuracy at 92.4%, albeit with potential overfitting, while the models using entropy criterion and SMOTE balancing achieved lower accuracies of 82.9% and 89.2% respectively, indicating the need for further evaluation to balance accuracy and generalization


#### Random Forest
The model performed poorly on the imbalaced data, with an accuracy score of 39%. The precision of 17% shows that the able is able to identify true positives in the prediction. However, the recall score of 82% suggests a moderate ability to capture all actual positive cases. The F1 score of 77% balances precision and recall.

Hyperparameter Tuning: Hyperparameter tuning using Gridsearch led to a refined model with an AUC score 98%. The difference between train and test scores 98% vs. 94% accuracy shows the successful generalization to unseen data, decreasing the risk of overfitting.


## Evaluation
After developing three final models (logistic regression, decision tree, k-nearest neighbors, and random forest), we compared their metrics. Upon comparison, we realized that the final model of Random Forest:

The final model had the following training and test Accuracy and F1 scores:

Train Accuracy: 0.9879969992498124 

Test Accuracy: 0.9490254872563718 

Train F1 Score: 0.9562841530054645 

Test F1 Score: 0.8111111111111111 

The most significant drivers of customer churn according to this model are:

    - The total number of day minutes a customer spend on call. 
    - The total amount a customer is charged on daytime calls
    - The number of customer service calls a customer make
    - The presence or absence on an international plan


## Conclusion 
In conclusion, this project aimed to predict customer churn in the telecom industry using a machine learning model. The dataset was cleaned. EDA was performed to analyze the distribution of the independent variables and the target variable. 4 models were used to predict customer churn, and the Random Forest model had the highest accuracy.


## Recommendations
-Implement targeted promotional offers or discounts for customers in area codes 415 and 510, where the churn rate is notably higher. This strategy aims to incentivize customer loyalty in these specific regions.

- Area codes 415 & 510 have a higher churn rate. We recommend to implement various promotional offers or discounts for customers. This will help decrease the churn rate.

-Enhance the overall quality of customer service and actively work towards reducing the number of customer service calls. A seamless and efficient customer service experience can positively impact customer satisfaction and retention.

- Conduct a thorough evaluation of the pricing structure for day, evening, night, and international charges. Ensure that the pricing aligns with customer expectations and market competitiveness.

- Develop and implement robust customer retention strategies, with a special focus on states exhibiting higher churn rates. States like Minnesota, Conneticut, Oregon, New york should be targeted for personalized retention efforts.

- Review and improve the value proposition of the voicemail plan to make it more appealing to customers. This may involve introducing additional features, enhancing user experience, or adjusting pricing to increase the perceived value of the voicemail service.

By addressing these key areas, Syria Tel can create a comprehensive strategy to reduce churn, enhance customer satisfaction, and foster long-term customer relationships..

## Future Work
-Look for more customer data like feedback, reasons for calling customer service numbers. Employ other robust models like Xboost etc,

 
 ## For More Information
 For more info please review our full analysis in: [notebook]('./SyriaTel_Customer_Churn') and [slides]('./predicting_syriaTel_customer_churn_presentation.pdf')


## Authors
1. Mercy Ronoh
2. Ashley Simiyu
3. Andrew Maina
4. Tasha Kanyiva
5. Diana Mbuvi
6. Emmanuella Karisa
