# SC1015-Mini-Project
<h2> Introduction </h2> 
  <p align='justify'> Hi Everyone! This is a mini-project for our SC1015 Introduction to Data Science and Machine Learning module at NTU. Our team consists of Eugene Wee, Clare Yeo and Guo Zhiqi. For this project, our team identified the rising trend of phishing attacks and we sought to create a machine learning model to effectively identify which URLs are phishing in nature. We tested out different machine learning models, evaluated them based on classification accuracy, and tried to improve each model's performance.
  </p> 
<b> Our Dataset: </b> https://www.kaggle.com/shashwatwork/web-page-phishing-detection-dataset?select=dataset_phishing.csv

<h2> Overview of Project </h2> 
  <ol>
    <li> Define Problem Statement </li> 
    <li> Data Preparation and Exploratory Data Analysis (EDA) </li> 
    <li> Machine Learning Model Training & Evaluation </li> 
    <li> Model Improvements - Feature Selection & Hyperparameter Tuning </li> 
    <li> Model Comparison </li>
    <li> Model Ensembling </li>
    <li> Presentation of Insights/ Recommendation </li> 
    <li> Learning Outcome :D </li> 
  </ol>

## 1. Problem Statement 
  <p align='justify'>  Phishing is a form of fraud in which the attacker learns sensitive information of users by sending as a reputable entity or person in email or other communication channels. URL phishing can lead to usernames, passwords, credit cards, and other personal information being stolen. In fact, the number of phishing scams in Singapore jumped from 16 cases in 2017 to 5,020 in 2022. In light of the growing concern, our group aims to identify important features of phishing URLs and detect phishing URLs using Machine Learning techniques. 
  </p>

## 2. Data Preparation and Exploratory Data Analysis (EDA)
  <p align='justify'> Firstly, we checked the distribution of our dataset and found that there was an equal number of non-phishing and phishing URLs of 5715. We also noticed that there were certain columns with NaN values for phishing URLs, and we deemed these columns as irrelevant. We then removed  these relevant columns which does not contribute to phishing URLs. </p>

> Purpose of Data Preparation: Removing columns which do not contribute to Phishing URLs (Irrelevant)

< insert heatmap & cols with 0 >

<h4> Principle Component Analysis (PCA) </h4>
  <p align='justify'>  Upon analysing our datasets, we realized that the columns represented the clean breakdown of each aspect of URL. We realized that there was a large dimension (87 columns) for the variables. Therefore, we sought to implement Principal Component Analysis (PCA) to reduce the dimensionality of the variables. We used a 95% explained variance for our PCA which reduces the dimensions to 60 components. We plotted the explained variance plot below. </p>

> Purpose of PCA: Outputs variables ordered by greatest influence on our target variable, Phishing (1 or 0). 

## 3. Machine Learning Model Training & Evaluation 
  <p> We decided to run the following ML models and evaluate their respective performances:
      <ul> 
        <li> Decision Tree Classifier </li>
        <li> Random Forest Classifier </li>
        <li> Logistic Regression Classifier </li> 
      </ul>
  </p> 
  
  <p> During Model Building, we will be running 2 rounds with the following model inputs:
      <ol>
        <li> PCA components (95% explained variance) </li>
        <li> PCA components (95% explained variance)  + Selected variables from Feature Selection </li>
      </ol>

## Round 1

### 1. Decision Tree Classifier  
  <p align='justify'> We used trained test split, with a test size of 0.3. Afterwards, we trained the model using a max depth of 3, and plotted its confusion matrix. We evaluated the model's accuracy, precision and F1 score. </p>
 
  <b> - Decision Tree Diagram </b> 
  
  insert diagram
  
  <b> - Model Evaluations </b> 
  
  insert diagram
  
### - Improving the Decision Tree (DT) 
  <p align='justify'> We check if pruning the tree using 2 parameters: Criterion and max_depth, can lead to better accuracy. We run our model using different values for max_depth (from 1 to 30) and visualize its accuracy for each max_depth. </p>
  
> We deem the best parameters to be Criterion = entropy and Max_depth = 7.

  < insert graph >

### 2. Random Forest Classifier
  <p align='justify'> However, we realised that DecisionTreeClassifier has poor classification accuracy and high False Negative results, therefore we applied RandomForestClassifer which ensembles the majority votes of a multitude of Decision Trees to improve model performance and robustness. </p>
 
  <b> - Model Evaluations </b> 
  
   < insert diagram > 
     
### 3. Logistic Regression Classifier
  <p align='justify'> We conducted Logistics Regression to model the probability of the discrete dependent variable (Phishing) based on the given variables. Logistic Regression assumes a linear relationship between dependent and independent variables, and constructs linear boundaries within the dataset to segment the data. </p>
        
  <b> - Model Evaluations </b> 
  
   < insert diagram >      
     
## 4. Model Improvements - Feature Selection & Hyperparameter Tuning 
  <p align='justify'>
    <ul> 
      <li> We achieved good results from using PCA components as our model inputs, but there was still inaccuracies in the model's performance.</li>
      <li> We noticed that certain variables (i.e. google_index, page_rank) were correlated to phishing emails, therefore we sought to use Feature Selection from our original dataset and include them into our model inputs. </li>
    </ul> 
    
  <p align='justify'> From our RandomForestClassifier model, we performed Feature Selection to rank variables based on feature importance, and we decided to add the top 5 features into our model inputs. We hypothesized that by adding these weights, we could achieve a better overall prediction accuracy and precision. </p>
    <p>This is a horizontal barchart of the top features </p>


### Exploratory Data Analysis for Feature Importance 
  <p>Looking at the chart for Feature Importance, we conducted EDA on the top 8 variables (Highest Influence on target variable). </p>
  
  <p> The violin plots of top 8 variables are as shown. (TBC) </p>
  
### Round 2

  <p align='justify'> For our second model building, we included the variables from Feature Selection to test if we can obtain a better performance for our models.   
    </p>      
### 1. Decision Tree (DT)
### 2. Random Forest 
### 3. Logistic Regression

## 5. Model Comparison 
  <p align='justify'> After running both rounds of model training for all 3 models, we consolidated our metrics into a dataframe for analysis.  
  
    <b>Deductions from consolidating results:</b>
  </p> 
  
  <ul> 
  <li>Generally across all 3 models, the 2nd round of model training produced better model performances and prediction results</li>
  <li>Support Vector Machine model produced the best result.</li>
        </ul> 

## 6. Model Improvements - Ensembling
  <p align='justify'> We also decided to conduct ensembling across the 3 different models to obtain better prediction and performance. </p> 

        
### Ensembling ML models </h4>
<p> We then seek to ensemble the 3 ML models using bagging method, where each model learns the error produced by the previous model using a slightly different subset of the training dataset. Bagging reduces variance and minimizes overfitting. </p>

--- 

## 7. Presentation of Insights/ Recommendation 

## 8. Learning Outcome :D 

<h2> THANK YOU! </h2>

# References: 
<ol> 
  <li> Phishing scams in Singapore rose to 5,020 cases in 2021 from 16 in 2017, https://sg.news.yahoo.com/phishing-scams-singapore-5020-cases-2021-from-16-in-2017-desmond-tan-084615863.html </li>
</ol>
