### What Drives the Price of a Car?
**Professional Certificate in Machine Learning and Artificial Intelligence**  
**Practical Application Assignment 11.1**

---

#### **Overview**

The objective of this project is to analyze the factors that contribute to the pricing of used cars. The primary goal is to develop a predictive model that accurately estimates the prices of used cars. This analysis will inform recommendations to a used car dealership, helping them understand what consumers value most in a vehicle and how various factors influence the final sale price.

---

#### **Data**

The dataset for this project was sourced from Kaggle and originally contained information on 3 million used cars. To enhance processing speed and efficiency, a subset of the data containing information on 426,000 cars was used for the analysis. This dataset includes features such as the year, manufacturer, condition, cylinders, fuel type, odometer reading, transmission type, and drive type, among others.

---

#### **Business Understanding**

The key task is to identify the factors that most significantly impact the price of used cars. By understanding these factors, we aim to provide actionable insights to the used car dealership. The dealership can use these insights to fine-tune their inventory, pricing strategies, and marketing efforts to align with consumer preferences and market trends.

---

#### **Data Understanding**

The first step involved examining the dataset to gain an initial understanding of the features and their distributions. This was followed by a detailed visualization of the data, which helped in identifying patterns, outliers, and relationships between different features and the target variable (car price).

---

#### **Data Preparation**

Data preparation involved several steps to ensure the dataset was ready for modeling:

1. **Data Type Conversion:** Converted data types to their most appropriate forms to optimize memory usage and processing speed.
  
2. **Dropping Columns:** Columns with a high number of unique entries that were unlikely to contribute to the model’s accuracy were removed.

3. **Title Status:** Rows where the `title_status` was not "clean" were dropped, as 405,000 entries had a "clean" title, which is a strong indicator of a car's value.

4. **Handling Missing Values:** Instead of dropping rows with missing values, which would have resulted in a significant data loss, a Simple Imputer was used to fill in missing values with strategies like mean or median.

5. **Encoding Categorical Variables:** Both Label Encoding and One-Hot Encoding were tested to transform categorical variables into numerical values suitable for machine learning models.

---

#### **Modeling**

The modeling process involved several steps to determine the optimal model complexity and identify the best-performing model:

1. **Model Complexity with One-Hot Encoding:** Polynomial features of degree 4 were used to explore the best model complexity when using One-Hot Encoding.

2. **Model Complexity with Label Encoder:** Polynomial features of degree 3 were employed to determine the best model complexity with Label Encoding.

3. **Grid Search CV with One-Hot Encoding:** GridSearchCV was used to search for the optimal number of features when using One-Hot Encoding.

4. **Grid Search CV with Label Encoder:** GridSearchCV identified that selecting 4 features provided the best model performance when using Label Encoding.

5. **Ridge Regression with GridSearch CV:** Ridge Regression, with hyperparameter tuning via GridSearchCV, was used to find the optimal alpha value for both One-Hot Encoding and Label Encoding. The optimal alpha value found was 449.84 when using Label Encoding.

6. **Model Evaluation:** The performance of the models was evaluated using Mean Squared Error (MSE). Ridge Regression and RandomForestRegressor were used with both One-Hot Encoding and Label Encoding to calculate MSE and compare the models.

---

#### **Evaluation**

**Best Model:**
- **Ridge Regression with Label Encoding** had the lowest Test MSE of 19842900.97, indicating it performed the best on unseen data.
- **Important Features:** The features that most significantly influenced the car prices included:
  - **Year:** Newer cars tend to have higher prices.
  - **Fuel Type:** The type of fuel (e.g., gas, diesel) impacts pricing.
  - **Odometer:** Higher mileage generally leads to a lower price.
  - **Transmission:** Automatic vs. manual transmission can affect the car's value.
  - **Manufacturer:** The brand of the car plays a significant role in determining its price.

---

#### **Conclusion**

Based on the data and the selected optimal models, the following key findings were identified regarding what drives the price of a used car:

1. **Car Title Status:** A clean title is essential for maintaining a higher resale value. Cars without a clean title were removed from the dataset as they significantly impacted the accuracy of the price predictions.

2. **Year of Manufacture:** Each additional year in the vehicle's age leads to a decrease in price by approximately $38.19.

3. **Manufacturer:** The price decreases by about $1.67 for each unit increase in the manufacturer index (as encoded by the Categorical encoder).

4. **Condition:** Each unit increase in the condition index results in a decrease in price of about $11.68, indicating that vehicles in poorer condition are valued less.

5. **Cylinders:** The number of cylinders has a positive effect on the price, with each additional cylinder increasing the price by approximately $1.05.

6. **Fuel Type:** The fuel type also influences the price, with most of the cars in the dataset using gasoline. This suggests that alternative fuel types might impact pricing differently.

7. **Odometer Reading:** For every mile increase in the odometer reading, the price decreases by about $0.02, reflecting the general wear and tear associated with higher mileage.

8. **Transmission Type:** The majority of cars in the dataset had automatic transmissions, which tends to be more desirable and, therefore, commands a higher price.

9. **Drive Type:** Vehicles with rear-wheel drive (RWD) see a decrease in price of approximately $16.47, possibly due to consumer preferences for other drive types like front-wheel drive (FWD) or all-wheel drive (AWD).

---

This report provides valuable insights into the factors that influence used car prices, enabling the dealership to make informed decisions about their inventory and pricing strategies. By focusing on cars with clean titles, lower mileage, and desirable features such as automatic transmissions and specific drive types, the dealership can better meet consumer demand and maximize their profitability.
