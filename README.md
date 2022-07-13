# Instacart Market Basket Analysis
Author: **Brandon Menendez**

![Instacart, Market Basket Analysis](./images/market_basket.jpg)

## Business Problem 
>"*Online grocery shopping in the U.S. trails that of other e-commerce categories in large part because our grocery shopping habits are so deeply ingrained, and online grocery retailers haven't yet convinced customers that grocery shopping online can be a better experience*" <br> <br>
> -Stephen Caine, Bain & Company


When the COVID-19 pandemic hit, many Americans opted to stay in their homes and order groceries online rather than go in person to their local grocery store. A [nationally representative survey](https://academic.oup.com/cdn/article/5/Supplement_2/231/6293076?login=false) found that **34%** of households reported grocery shopping online more since the beginning of the pandemic and **60%** of these households planned to continue shopping online after the pandemic ends. 

This sudden increase in customer's shopping online was a major tailwind for online grocers. But just as important as customer acquisition is for these companies, so is customer retention. Like the classic saying goes, "Old habits die hard" and online grocers need to ensure they are utilizing their technology to provide a more convenient shopping experience in order to hold on to those customers deciding to shop online rather than in-store. There are three major tools that all online grocers can utilize in an attempt to retain customers gained during the pandemic:

1. **Merchandising:** (blurb about Merchandising)
2. **Recommendations:** (blurb about recommendation)
3. **Coupons & Promotios:** (blurb about coupons and promotions)

Instacart is a grocery ordering and delivery app, which has over 500 million products available across 40,000 grocery stores in the United States & Canada. Instacart provides a convenient customer experience, which is largely focused around product recommendations based on past purchases. In addition to recommendaiton widgets  (Add to Cart, Frequently bought together etc), Instacart also works with retailers to provide targeted promotions and coupons to its customers. 

**Objective:** <br>
Using over 3M rows of customer order data provided by Instacart, I will be performing a market basket analysis and implement predictive modeling  to:

1. Identify frequent items sets and association rules to better inform merchandising, customer recommendations and promotional stategies for Instacart <br>
2. Predict ahead of time which items will be re-ordered by a particular customer

Using the insights gained from this analysis, I will provide recommendations for how Instacart can improve their merchandising, recommendation and promotional strategy in an effort to maintain customers for the long-term.

## Data Understanding 
The data for this project was released by Instacart in 2017 as part of their [3 Million Instacart Order Competition](https://tech.instacart.com/3-million-instacart-orders-open-sourced-d40d29ead6f2).

The provided anonymized dataset contains a sample of over 3 million customer orders, inclusive of over 49 thousand unique products and 200 thousand unique customers. For each user, Instacart provided between 4 and 100 of their orders, with the sequence of products purchased in each order. They also provide the week and hour of day the order was placed, a relative measure of time between orders and product attributes.

For this analysis I will be utilizing the following tables:
   - **orders** - Indicates which evaluation set an order belongs too  
   - **orders_prior** - Contains previous order contents for all customers. 'reordered' indicates that the customer has a previous order that contains the product
   - **products** - Provides additional information about the products ordered, including product name, department, and aisle
   - **aisles** - Contains attributes about aisles
   - **departments** - Contains attributes about departments 

## Methods 
1. Apriori Algorithm - Association rule mining & frequent item sets.
2. Logistic Regression - Binary classification model for predicting whether or not a customer will reorder a product.
3. XBoost Model - Classification model to identify future re-orders from existing customers. 

## Results 
Confidence - 


Lift - 


Support - 


Model Results - 

# Conclusion 
## Results
#### Logistic Regression:
- The best model I ran had 90% Precision and 88% Recall scores. 

![Confusion Matrix](./images/confusion_matrix.png)

#### XGBoost:
- Using XGBoost, I was able to identify the most important features in prediciting customer reorders. In older notebooks, I fit the model onto the train data, but was not getting results better than the LogReg model. The top three important features for this model were:
   1. user_reorder_ratio
   2. add_to_cart_order
   3. prd_reorder_ratio
   
#### Apriori:
- The Apriori Algorithm analysis was successful in identifying frequent item sets. Some observations:
   - Produce and/or Dairy items are included in all of the top item sets
   - Banana's are the number one basket builder for customers 
   - Top Item Combinations by Association Rule:
       - **Lift:** Organic Raspberries & Organic Strawberries
       - **Support:** Bag of Organic Bananas & Organic Haas Avocados
       - **Confidence:** Organic Fuji Apple & Banana

## Recommendations
From this analysis I have generated the following recommendations that Instacart can utilize:

1. **Banana's are important.** Since Bananas are the number one basket building item, offering promotions on these products is a good way to get people in the door<br><br>

2. **Merchandising:** Using the reorder prediction model and frequent item sets, Instacart can better inform  merchandising decisions to answer questions like, What 'aisles' or products should be displayed near each other? Understanding the answer to questions like these are important in targeting merchandising placements & display ads to individual users could help Instacart maximize each user's basket. <br><br>

3. **Recommendations**: Understanding what a customer is going to order in the future is important for product recommendations. Using the predictive LogReg model, Instacart can optimize recommendation widgets like 'Add to Cart' with the likely items that customer will order. <br><br>

4. **Promotional Strategy:** Online grocers are in a unique position to cross merchandise products that wouldn't normally live together in a traditional grocery store, for example, ice cream and hot dogs for the Fourth of July. Using the Apriori results, Instacart can understand what items are commonly (or uncommonly) ordered together in order to implement targeted promotions to customers. 
    

## Future Steps 
There are a number of steps I would like to take in the future to improve results of this analysis. These include the following:

1. **Display Ad Opportunity Cost** - With additional data regarding average product costs and average sales price, this analysis can be updated to identify the opportunity cost of showing one product to a customer over another. For example, if we know that Customer X orders Corn Flakes every week, we can use the model to identify frequently bundled items and display the item to Customer X that generates the most profit for Instacart while also keeping the customer happy <br><br>
2. **Datetime Considerations** - While this analysis largely focused on user behavior as it pertained to order history and products, implementing additional features around when a user orders certain items, how often customers are making "stock up" baskets versus "everyday" baskets and more could improve the overall results of the model. <br><br>
3. **Reviews & Ratings** - With more data around product reviews and ratings on a customer level, I would like to implement a Collaborative Item-Based Filtering recommender system to see how it compares to the binary classificaiton model implemented in this notebook. 

# For More Information
Please refer to the [EDA](https://github.com/brandmend/Instacart_Basket_Prediction_Analysis/blob/main/Instacart_Basket_Analysis_EDA_LogReg.ipynb) & [Apriori](https://github.com/brandmend/Instacart_Basket_Prediction_Analysis/blob/main/Instacart_Basket_Analysis_Apriori.ipynb) Jupyter Notebooks or the presentation.

For additional information, please contact Brandon Menendez at [bmenendez94@gmail.com](bmenendez94@gmail.com) or on [LinkedIn](http://linkedin.com/in/brandon-menendez/) 


## Repository Structure 
> - images
> - Instacart_Basket_Analysis_EDA_LogReg.ipynb
> - presentation
> - README.md
