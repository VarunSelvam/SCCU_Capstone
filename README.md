# Swire Coca Cola Capstone Project
This is a group project that I completed for my final Capstone with 3 other colleagues. Swire Coca Cola (SCCU) is a bottling company that has partnered with the Coca-Cola Company to manufacture Coke and distribute it. Coca-Cola produces a unique concentrate which Swire mixes with water and sweetners to produce the actual drink. Afterwards, Swire will deliver the finished product to customers in the United States.

## Business Problem

This project will mainly focus on SCCU's logistics within their delivery operations. SCCU has two delivery methods:

- Red Trucks, which are directly controlled by Swire and used for direct deliveries and are ideal for high-volume customers. This enables SCCU to maintain direct relationship with them. 
- Alternate Route to Market (ARTM) - White Trucks, are operated by third-party companies, resulting in less direct contact between Swire and the customer. These trucks are better suited for customers with lower volume needs.

SCCU is seeking a **cost-efficient** strategy to optimize logistics to drive operational efficiencies and increases revenue. To achieve this, SCCU is currently using a threshold of **400** gallons to determine if a customer should be on Red Trucks or sent to an ARTM. Customers who **annually order more** than 400 gallons should remain on the Red Trucks while the rest of the customers should be placed on White Trucks. Misclassification with the existing threshold risks missed opportunities for revenue growth and weakens customer relationships by miscalssifying customers who have the potential to grow.

### Project Objectives
- Leverage advanced analytics to ensure that high-growth accounts remain on direct delivery routes. This will optimize **cost-efficiency** by switching low-growth accounts to ARTM. Additionally, explore what characteristics enable a customer to grow beyond 400 gallons.
  
- The analysis will focus on two key customer segments requested by SCCU:
  - Local Market Partners (fountain-only buyers): Customers who purchase only fountain drinks, with no CO2, cans, or bottles.
  - All Customers: The broader customer base, including all buyers of CO2, cans, bottles, and fountain drinks, regardless of partnership status.
 
- SCCU has also requested that alternative considerations for the threshold be considered such as 100 gallons, etc for determining if a customer should be on the Red Truck or White Truck.

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

## Business Value

The Business Value of this solution is that it enables SCCU to identify potential threshold exceeding customers in a **targeted** approach. For instance, instead of analyzing **all** the customers to identify potential threshold exceeding customers, SCCU can focus marketing and sales resources on Mid-Volume Customers. These Mid-Volume Customers also have a 22% higher converstion rate of becoming permanent threshold exceeding customers compared to their 450+gallon/year cohort who may occasionally order large volumes but not frequently. 

Furthermore, this targeted approach can be be further drilled down by also focusing on the specific Sales Channels. (Sales Channels are how the customer places an order.) For instance, customers who place orders through a Sales Representative have a 38% increase in converting customers into threshold exceeding customers. This solution when combined with the previous recomendation of targeting the Mid-Volume customers creates a distinct segment that SCCU could potentially target. Moreover, when integrated with the Geographic Focus recommendation, a comprehensive understanding of the target customer profile becomes evident.

- For instance, SCCU could target Mid-Volume Customers who order through Sales Representatives and are located in Massachussets. Afterwards Account Managers and Sales Representatives would collaborate to create personalized replenishment plans via MY_COKE360 portal and provide dynamic discounting for incremental volume commitments. This consequently would help with converting the customer to a threshold exceeding customer.
- SCCU could similarily do this for other customers as well.

Finally, the Geographic Focus Recommendation shows where most of SCCU's customers are located. This is very valuable for SCCU since they can ensure that any deliveries for potential high growth customers occur in states with pre-existing customers. This will ensure that SCCU does not spend resources delivering to a few customers when those resources sould be better optimized for delivering to several customers who are located close together. As previously mentioned, the geographic location can be combined with the other recommendations to allow for more preciste targeting. (I.e the example of targeting Mid-Volume customers in MA and having the customer work with a Sales Rep and Account Manager.)

## My Contribution

I contributed to this project by creating several models to see what characteristics contribute to a customer exceeding the threshold. I achieved this with the use of Decision Trees, XGBoost Models and Logistic Regression. After I was done cleaning the data and making adjustements to ensure proper model performance, we checked what the common predictors were in all of these models. Afterwards, we picked the top most common predictors in these models which were some of the channels in the `Sales_Channel`. (The `Sales_Channel` is how customers place orders.)

Additionally, I also did a segmentation utilizing a Ridge Logistic Regression model to segment customers by their probability of converting 

Finally, I contributed to this project by converting the `Zip_Code` column into states to make the column more useful. Afterwards, I created visualizations to show the relationships between the customers by states, volume delivered by state along with local market partner numbers for each state. These initial visualizations were then used by my colleague for clustering analysis to help with deciding the high priority states.

## Difficulties Encountered


## Project Insights
