# floward_restaurants_take_home_case_study
Data science case study to extract insights for food delivery company.<br/>
This project uses a CatBoost learning algorithm.<br/><br/>
The project is broken into 4 stages:<br/>
1. Import<br/>
2. Clean<br/>
3. Feature Engineering<br/>
4. Model<br/>
---
## Requirements
Run "pip install -r requirements.txt" to install all the the reuired packages.<br/>

Tools Used:</br>
- Python
- Jupyter Notebooks

---

## Problem Foundation & Goal
**Problem Definition**<br/>
A food delivery company is committed to providing a delivery experience that delights their customers while still being incredibly efficient. Thus it is critical that they have the best possible model of how long it takes for a food order to be prepared. This allows them to ensure that a rider arrives at a restaurant to pick up an order exactly when the food is ready.<br/>

**Goal**<br/>
The goal is to reduce error measured through MAE, MAPE and RMSE. To do this I will follow the basic principals of investigation, cleaning, feature engineering and modelling.

---

## Import
Read in the data and do some preliminary analysis of the data.</br>
ProfileReport package was used to give a very deep breakdown of all the data.

---

## Clean
- The cleaning stage involved taking a closer look at each column and their relations to each other.<br/>
- The `order_acknowledged_at` column was useful to break down into individual columns, this was done at the feature engineering stage. <br/>
- The `order_ready_at` column can not be used as it will not be available when predicting prep time.<br/>
- The `order_value_gbp` column was clean, it did have high correlation with `number_of_items` but removing either column reduced accuracy. Their may be room for potential feature engineering using both of these in the future to capture the valuable information without overfitting.<br/>
- The target variable `prep_time_seconds` was viewed using a box plot which identified that there were some large outliers. These were filtered using the z-score method.<br/>
- The `country` column was removed due to the lack of valuable insight within it. There were only a few cities that were not in the UK. I did try to use this column as a binary `country_is_uk` but this did not prove useful.<br/>
- The `type_of_food` column is a column where there is clear opportunity for improvement. The values within this column which had very few entries were included in other categories. This was doen through investigating different types of cuisine and the similarities. This is open to experimentation and testing for improvement.

---

## Feature Engineering
- The year data was not useful due to all orders having the same year and the month was almost entirely a single value also. The day was originally used as a day of month value but this was later updated to day of the week which increased the importance of this feature and the hour also proved a useful feature.
- Minimum, maximum and mean `prep_time_seconds` for each resteaurant were all added as features which improved the accuracy.
---

## Model
- Linear regression was originally run to get a general idea of the accuracy that we can expect.
- CatBoost was chosen as the primary model predictor due to the ease with which it handles the categorical features.
- RMSE, MAE, MAPE and R2 were all used to analyze the results of the model.
- Hyperparameter tuning was attempted but ran into to some issues running it on the local machine, this could be used to improve the performance of the model in the future.
---

## Next Steps and Potential Applications
**Next Steps**

- The most obvious approach to improving this model would be collecting far more data. The data quality seems to be good but quantity is definitely a limitting factor.
- One feature which could be developed that I believe would improve accuracy is to capture how busy a restaurant is by checking how many orders they have had in the last hour or two.
- More experimentation and cleaning of the `type_of_food` column would be a priority as there is much room for improvement there.

**Potential Applications**

Using existing maps technology and geolocation information about the delivery drivers a system could be built to check how far away each delivery driver is. Depending on their distance away the orders could be re-organized in order of priority to avoid having drivers waiting for meals at the restaurant while other drivers' food delivery is ready and cooked while the driver is not ready. Joining these two systems so that they are aligned could deliver additional efficiency.<br/>

Delivery is a seperate problem and the driver is limited by external factors such as traffic and speed limits, therefore, I believe much of the efficiency improvement here can be garnered by improving the time between the order accepted and delivery driver departing. Most the this can be achieved by having two system in communication between the driver and restaurant.

---