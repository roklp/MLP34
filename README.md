# Multi-Class Prediction of Obesity Risk
- Goal: use various factors to predict obesity risk in individuals, which is related to cardiovascular disease.
- Evaluation: evaluated using the accuracy score
- Timeline : February 1, 2024 ~ February 29, 2024
- Dataset: generated from a deep learning model trained on the Obesity or CVD risk dataset
- Link: https://www.kaggle.com/competitions/playground-series-s4e2/overview

**Analysis Period** : 2024.02.23 ~ 2024.02.29
<br/>
<br/>


>#  Variable description 
| Column | Full Form | Description| 
|---|---|---|
| 'id'| id | Unique for each person(row)|
|'Gender'| Gender| person's Gender|
| 'Age' | Age| Dtype is float. Age is between 14 years to 61 years |
|'Height'| Height | Height is in meter it's between 1.45m to 1.98m|
| 'Weight' | Weight| Weight is between 39 to 165. I think it's in KG.|
|'family_history_with_overweight'| family history <br> with overweight| yes or no question|
| 'FAVC'| Frequent consumption <br> of high calorie food| it's yes or no question. i think question they asked is <br>do you consume high calorie food|
|'FCVC'|  Frequency of <br>consumption of vegetables| Similar to FAVC. this is also `yes or no` question|
|'NCP'| Number of main meals| dtype is float, NCP is between 1 & 4. I think it should be 1,2,3,4 <br>but our data is synthetic so it's taking float values|
|'CAEC'| Consumption of <br>food between meals| takes 4 values `Sometimes`, `Frequently`, `no` & `Always` <br>|
| 'SMOKE'| Smoke | yes or no question. i think the question is "Do you smoke?" |
|'CH2O'| Consumption of <br>water daily| CH2O takes values between 1 & 3. again it's given as <br>float may be because of synthetic data. it's values should be 1,2 or 3|
|'SCC'|  Calories consumption <br>monitoring| yes or no question|
|'FAF'| Physical activity <br>frequency| FAF is between 0 to 3, 0 means no physical activity<br> and 3 means high workout. and again, in our data it's given as float|
|'TUE'| Time using <br>technology devices| TUE is between 0 to 2. I think question will be "How long you have <br>been using technology devices to track your health." in our data it's given as float |
|'CALC'| Consumption of alcohol | Takes 3 values: `Sometimes`, `no`, `Frequently`|
| 'MTRANS' | Transportation used| MTRANS takes 5 values `Public_Transportation`, `Automobile`, <br>`Walking`, `Motorbike`, & `Bike`|
|'NObeyesdad'| TARGET | This is our target, takes 7 values, and in this comp. we have to give <br>the class name (Not the Probability, which is the case in most comp.)


<div style="font-size:100%"> 
    <b>NObeyesdad (Target Variable):</b>
</div>

* Insufficient_Weight : Less than 18.5
* Normal_Weight       : 18.5 to 24.9
* Obesity_Type_I      : 30.0 to 34.9
* Obesity_Type_II     : 35.0 to 39.9
* Obesity_Type_III   : Higher than 40
* Overweight_Level_I, Overweight_Level_II takes values between 25 to 29  <br/>
<br/><br/>
># Key Point 
In this kaggle project, We explored the task of predicting obesity risk using a multi-class classification approach.

This report outlines the key steps taken in feature engineering, ensemble modeling, and encoding techniques to achieve accurate predictions.

## feature engineering
In this section, various transformations are applied to preprocess the data and derive new features that could potentially enhance the predictive performance of machine learning models.

#### **Age and Height Rounding**  <br>
To facilitate model learning, the 'Age' and 'Height' columns undergo rounding transformations. <br>The 'Age' values are multiplied by 100 and converted to uint16, effectively rounding them to the nearest whole number. Similarly, the 'Height' values are also multiplied by 100 and converted to uint16 to achieve rounding.

####  **Feature Extraction** <br>
New features are extracted to provide additional insights into the dataset. Specifically, the 'BMI' (Body Mass Index) feature is computed by dividing the weight by the square of the height. <br>This metric is commonly used to assess an individual's body composition. Additionally, a 'PseudoTarget' feature is created based on the BMI values. The BMI values are segmented into predefined bins, and each observation is assigned a categorical label corresponding to its BMI category.

####  **Column Rounding** <br>
Certain columns in the dataset have their values rounded to integers for simplification and standardization. This operation is performed on columns such as 'FCVC', 'NCP', 'CH2O', 'FAF', and 'TUE'. <br>By rounding these numerical values, the model can focus on broader patterns and trends within the data.

####  **Feature Dropping** <br>
A custom transformer, known as FeatureDropper, is employed to remove specified columns from the dataset. This allows for the elimination of redundant or irrelevant features that may hinder model performance. <br>The FeatureDropper class is initialized with a list of columns to be dropped, and during the transform process, these columns are excluded from the dataset.
## encoding 
In this code, we primarily used OneHotEncoder and MEstimateEncoder.
Looking at the train data, we have a mixture of numerical and categorical columns.
Furthermore, the dependent variable we need to predict is categorical, not numerical.
Therefore, we encoded the ['Gender', 'family_history_with_overweight', 'FAVC', 'CAEC', 'SMOKE', 'SCC', 'CALC', 'MTRANS'] columns in the train data,
and the 'NObeyesdad' column in the test data.

MEstimateEncoder is one method for encoding categorical variables. This method encodes each category of the categorical variable using the mean of the target variable for each category. Instead of using the mean of the target variable for each category, MEstimateEncoder calculates the mean of the category with a pre-specified M value. This allows for consistent calculation of the mean for all categories. This method is useful when the number of samples in a category is small or when categories are peculiar.

## ensemble
We employ an ensemble model consisting of Random Forest Model, LGBM Model, XGB Model, and CatBoost Model. For each model, we utilize Optuna to find the optimal hyperparameters, followed by cross-validation. Additionally, we assign weights to each model and create the final ensemble model. Finally, we compute the accuracy. <br/>
<br/>

># Accuracy & Ranking
**Accuracy** - 0.91040 <br/>
**Ranking**  - 171/3589 <br/>
  
># Presentation
피피티 자리
<br/>
<br/>

># Member
- Carolyne Jung : https://github.com/GOOKOC
- Ju-Yeong Jung : https://github.com/Ju0s
- Jin-Hyeok Choi : https://github.com/j2nhyeok
- Dae-Hee Han : https://github.com/roklp

   

