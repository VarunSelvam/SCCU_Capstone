# Swire Coca Cola Capstone Project
This is a group project that I completed for my final Capstone with 3 other colleagues. Swire Coca Cola (SCCU) is a bottling company that has partnered with the Coca-Cola Company to manufacture Coke and distribute it. Coca-Cola produces a unique concentrate which Swire mixes with water and sweeteners to produce the actual drink. Afterwards, Swire will deliver the finished product to customers in the United States.

## Business Problem

This project will mainly focus on SCCU's logistics within their delivery operations. SCCU has two delivery methods:

- Red Trucks, which are directly controlled by Swire and used for direct deliveries and are ideal for high-volume customers. This enables SCCU to maintain direct relationship with them. 
- Alternate Route to Market (ARTM) - White Trucks, are operated by third-party companies, resulting in less direct contact between Swire and the customer. These trucks are better suited for customers with lower volume needs.

SCCU is seeking a **cost-efficient** strategy to optimize logistics to drive operational efficiencies and increases revenue. To achieve this, SCCU is currently using a threshold of **400** gallons to determine if a customer should be on Red Trucks or sent to an ARTM. Customers who **annually order more** than 400 gallons should remain on the Red Trucks while the rest of the customers should be placed on White Trucks. Misclassification with the existing threshold risks missed opportunities for revenue growth and weakens customer relationships by misclassifying customers who have the potential to grow.

### Project Objectives
- Leverage advanced analytics to ensure that high-growth accounts remain on direct delivery routes. This will optimize **cost-efficiency** by switching low-growth accounts to ARTM. Additionally, explore what characteristics enable a customer to grow beyond 400 gallons.
  
- The analysis will focus on two key customer segments requested by SCCU:
  - Local Market Partners (fountain-only buyers): Customers who purchase only fountain drinks, with no CO2, cans, or bottles.
  - All Customers: The broader customer base, including all buyers of CO2, cans, bottles, and fountain drinks, regardless of partnership status.
 
- SCCU has also requested that alternative considerations for the threshold be considered such as 100 gallons, etc. to determine if a customer should be on the Red Truck or White Truck.

## Problem Solution

Our group's solution to the project was the following: 

### 1. Target "Mid-Volume" Customers
**Focus Segment:** 300-449 gallon/year customers

**Growth Potential:** 22% higher conversion rate than 450+ gallon cohort

**Tactics:**
  - Personalized replenishment plans via MY_COKE360 portal
  - Dynamic discounting for incremental volume commitments

### 2. Optimize Partnership Channels
**High-Impact Channels:**
- Sales Rep Outreach : 38% conversion lift with dedicated account managers
- EDI Integration : 27% faster order fulfillment for chain stores
- MY_COKE360 : 41% customer retention in pilot markets

### 3. Geographic Focus
**High-Priority States:**
  - Massachusetts
  - Kansas
  - Kentucky
  - Maryland

These 4 states comprise 62% of high-density customers

### 4. New Threshold
**Revenue Impact of Threshold Adjustment**
| Metric                | 300-Gallon Threshold | 400-Gallon Threshold | Difference    |
|-----------------------|----------------------|----------------------|---------------|
| Net Annual Revenue    | **+$26,476.83**      | Baseline             | +$5/unit profit|

**Implementation Insight:** Lowering threshold to 300 gallons captures 34% more growth-ready customers with sustainable margins.

## Business Value

The Business Value of this solution is that it enables SCCU to identify potential threshold exceeding customers in a **targeted** approach. For instance, instead of analyzing **all** the customers to identify potential threshold exceeding customers, SCCU can focus marketing and sales resources on Mid-Volume Customers. These Mid-Volume Customers also have a 22% higher conversion rate of becoming permanent threshold exceeding customers compared to their 450+gallon/year cohort who may occasionally order large volumes but not frequently. 

Furthermore, this targeted approach can be be further drilled down by also focusing on the specific Sales Channels. (Sales Channels are how the customer places an order.) For instance, customers who place orders through a Sales Representative have a 38% increase in converting customers into threshold exceeding customers. This solution when combined with the previous recommendation of targeting the Mid-Volume customers creates a distinct segment that SCCU could potentially target. Moreover, when integrated with the Geographic Focus recommendation, a comprehensive understanding of the target customer profile becomes evident.

- For instance, SCCU could target Mid-Volume Customers who order through Sales Representatives and are in Massachusetts. Afterwards, Account Managers and Sales Representatives would collaborate to create personalized replenishment plans via MY_COKE360 portal and provide dynamic discounting for incremental volume commitments. This consequently would help with converting the customer to a threshold exceeding customer utilizing the new threshold.
- SCCU could similarly do this for other customers as well.

The Geographic Focus Recommendation shows where most of SCCU's customers are located. This is very valuable for SCCU since they can ensure that any deliveries for potential high growth customers occur in states with pre-existing customers. This will ensure that SCCU does not spend resources delivering to a few customers when those resources should be better optimized for delivering to several customers who are located close together. As previously mentioned, the geographic location can be combined with the other recommendations to allow for more precise targeting. (I.e the example of targeting Mid-Volume customers in MA and having the customer work with a Sales Rep and Account Manager.)

Finally, the new threshold will help with enabling more customers to exceed the threshold which provides more revenue opportunities by capturing 34% more growth-ready customers, especially when combined with the above recommendations for a more targeted approach.

## My Contribution

I contributed to this project by creating several models to see what characteristics can identify customers who are not exceeding the threshold currently but have the potential to exceed it in the future. Decision Trees, XGBoost Models and Logistic Regression were used to help identify these characteristics. Decision Trees and Logistic Regression were chosen since they are whitebox models which give more predictor insights compared to XGBoost. XGBoost was chosen for its predictive power and because it can provide limited insights about the predictors via "Importance Scores". I also ran these models across both thresholds, to analyze the predictors that remained the same and which predictors changed. Afterwards, we picked the most common predictors in these models across both thresholds which are the channels described in the "High-Impact Channels" detailed in the __Problem_Solution__ section.

Additionally, I also did a segmentation utilizing a Ridge Logistic Regression model to segment customers by their probability of exceeding the threshold. This segmentation, although not incorporated in the final section, did give us a perspective of how many customers could possibly exceed the threshold. (For reference 2.54% to 2.69% of customers had a very high chance of exceeding the threshold.)

Finally, I converted `Zip_Code` column into states to make the column more useful. Afterwards, I created visualizations to show the relationships between the customers by states, volume delivered by state along with local market partner numbers for each state. These initial visualizations were then built upon further by my colleague for clustering analysis to help with deciding the high priority states.

## Difficulties Encountered

During the course of this project, my team encountered several difficulties:

__Strange Predictors__: The target variable which is `Transition_Status` had to be created first before doing any modelling. Transition Status keeps track of customers who were below the Threshold in 2023 and moved above the threshold in 2024. This scenario will be labelled as __Up__. There are 3 other scenarios however that also must be considered:

  * __Down__: Moving from above the Threshold in 2023 to below the Threshold in 2024.
  * __Stays above Threshold__: Remaining above the Threshold in both 2023 and 2024.
  * __Stays below Threshold__: Remaining below the Threshold in both 2023 and 2024.

The main objective was to model the __Up__ customers which is why we decided to model __UP__ as 1 and code the other scenarios as zero. The problem however occurred when we started modelling because our XGboost model stated that being below the threshold was the strongest predictor. The prominence of this feature in determining transition likelihood is misleading, since being below the threshold is merely a prerequisite for transitioning. It is embedded in the way the transition_status variable is defined. 

  - __Solution:__ To solve this issue, any threshold related variables were removed from the dataset to prevent the model from mapping a customer's threshold status to whether they moved up, since it made the model create an erroneous relationship where any customer below the threshold will very likely transition. 

__Negative Volume Coefficients__: A few of our logistic regression models had coefficients that stated that ordering less volume would improve the log-odds of them exceeding the threshold. This does not make sense in context and was due to multi-collinearity and the model design.

  - Several of the numerical variables like `Delivery Cost` and `Volume` were highly correlated at .96. This meant that some of the coefficients had inflated values which made model interpretation hard and could have contributed to the sign change.
  - The other reason is again due to how `Transition_Status` is designed. A customer must be below the threshold to transition. If they are below the threshold, then they are also ordering less volume. Thus, from the model's perspective it would seem that ordering less volume means that a customer will transition, since some of these low volume ordering customers exceed the threshold the next year. This is again an erroneous perspective and shows that the model has built a negative relationship between volume and transitioning.

  - __Solution:__ We implemented various solutions like recoding the transition variable to include all the scenarios. We thought that with all the scenarios encoded, the model could learn to distinguish between the scenarios and this would improve the coefficients. It however did not, and the model still made that mistake. The next idea we tried was to identify any correlated variables and drop one of them from the dataset. This is because multi-colinearity affects coefficient interpretation, but not predictive performance. This did fix the issue somewhat, however some of the volume related variables were still negative. We decided to evaluate the ROC-AUC score for the Logistic Regression model which was .73 on the Train and Test sets. Since the model's performance was not highly affected and was consistent on both train and test sets, we decided to ignore the volume-related variables and focus on the other categorical variables which were still reliable.

__Imbalanced Dataset__: The Target Variable, `Transition_Status` had 4 scenarios, with 3 being coded as zero and __UP__ being coded as one to make it a binary classification problem. The issue however was that the __UP__ class only comprised 4.13% of the entire dataset which made the dataset very imbalanced. This severely affected the performance of the decision trees which saw large drops (20-40%) from Train ROC-AUC to Test ROC-AUC.

  - __Solution__: SMOTE was utilized to create synthetic minority observations which helped improve model performance tremendously. For instance, when SMOTE was utilized, the XGBoost model saw a relatively modest decline between train and test of 10%. (Most of the XGBoost Models were at .99 Train ROC-AUC and .89 Test ROC-AUC which is a modest decline when compared to the decision trees. The decision trees had drops of 20-40% between the train and test sets as previously mentioned. The Ridge Logistic Regression Model also performed fairly well with a .73 ROC-AUC between the Train and Test Sets.

## Project Insights

- This project taught me several valuable skills such as the importance of Feature Engineering. One should always carefully inspect the data and analyze how various attributes may affect the model's ability to learn patterns. It is not sufficient to rely on the model alone to map relationships between any Target variable and the explanatory variables. For instance, with the `Transition_Status` variable, I learned how its design was creating a negative relationship which was leading to strange results like negative volume coefficients.

- It is also important to translate results into an easy to understand or quantifiable manner. For instance, when dealing with log-odds in logistic regression, it's important to quantify the predictors by trying different methods. For instance, the `Sales Rep Outreach` channel had a log-odd coefficient but this is not easily understandable in the context of the business. However by analyzing the conversion rate for this variable, we were able to quantify the effect of focusing on the `Sales Rep Outreach` Channel.

- Finally, it's important to focus on the main goals of the organization because there are often several different paths that can be explored. It however is not feasible to explore every path which is why the main goals of the business should always be kept in mind. This helps with determining which paths will yield more results and keeping the analysis relevant to the organization's needs.
