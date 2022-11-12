# Data Analysis Exercise - Meal-Prep-Time

## Problem Definition
A food delivery company is committed to providing a delivery experience that delights their customers while still being incredibly efficient. Thus it is critical that they have the best possible model of how long it takes for a food order to be prepared. This allows them to ensure that a rider arrives at a restaurant to pick up an order exactly when the food is ready.

The aim of this exercise is to use historical data, clean it, manipulate it to extract insights, then finally predict the food preparation time for each order.

## Modelling Exercise
1. Use any tool or language you would prefer.
2. Perform any cleaning, exploration and/or visualisation on the provided data (orders.csv and restaurants.csv)
3. Build a model that estimates the time it takes for a restaurant to prepare the food for an order.
4. Evaluate the performance of this model. If you were a data scientist working on this (i.e. if this was your day job and not just part of an interview process!), explain your next steps with this model considering its potential applications within the production systems.

Feel free to include a list of additional ideas you would explore if you had more time to work on this problem. You will have the opportunity to explain your approach and answer further questions on it in another interview. We are looking for sensible approach that does the basics well, particularly on data preparation and storytelling through visualisation, not a showcase of novel techniques.

Note: All timestamps are given to you in the local timezone. You have no need to try any timezone conversions.

Please send us your code and explanation of your approach (separate report or Notebook) via Github. Please include any required instructions for how to run your code.


## Appendix: Data Schema and Description

Filename : **orders.csv**

| Column Name       | Type    | Description                   |
|-------------------|---------|-------------------------------|
| order_acknowledged_at | String (timestamp) | Timestamp (local timezone) indicating when the order is acknowledged by the restaurant. |
| order_ready_at    | String (timestamp) | Timestamp (local timezone) indicating when the food is ready. |
| order_value_gbp       | Float   | Value of the order in GBP.|
| restaurant_id     | Integer | Unique restaurant identifier. |
| number_of_items   | Integer | Number of items in the order. |
| prep_time_seconds   | Integer | (order_ready_at - order_acknowledged_at) in seconds. This is the food preparation time and what you should model. |

Filename : **restaurants.csv**

| Column Name       | Type    | Description                   |
|-------------------|---------|-------------------------------|
| restaurant_id     | Integer | Unique restaurant identifier  |
| country           | String  | Country where the restaurant is |
| city              | String  | City where the restaurant is |
| type_of_food      | String  | Type of food prepared by the restaurant |
