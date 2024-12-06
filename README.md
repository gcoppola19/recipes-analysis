
# Statistical Analysis on Recipes and Nutrition's role in Ratings
This recipe analysis is a data science project, capturing the process of scraping data from a website and through steps of cleaning, and creating various models to answer our research question about our data. The primary focus of the project is to investigate the significance nutrition in the ratings of various recipes on food.com and furthermore if we can predict these ratings based on selected nutrition factors.

---
## Introduction

 Our data set used for this analysis is on various recipes and user interactions from food.com.  It contains two datasets: one with recipe data like preparation time, and nutrition, and the other with user ratings and reviews for a recipe. We merged these datasets based on recipe ID to have all the recipe information and it's associated ratings in one table. 

 We are investigating how nutrition plays a role in recipe ratings: do healthier (PDV of sugar and saturated fat are both <5%) recipes have higher ratings? We hope to find out if people rate healthier meals better than less healthy ones. Understanding if users appreciate healthier recipes provides valuable insights for recipe developers. It can help in prioritizing creating and promoting recipes that align with consumer preferences for health-conscious eating. 
 
 
 There are 234429 rows in our data set, and we focused mainly on the 'rating' and 'nutrition' columns. The rating column was the given rating for a recipe from a customer. From the nutrition column which was a list of all nutrition facts for a recipe, we extracted data about sugar and saturated fat daily value percentage to create new columns 'sugar_pdv' and 'satfat_pdv.' Then, we created a 'healthy' column which would consider a recipe healthy if the sugar and saturated fat percent daily value were both less than or equal to 20%. 

 
Here's a detailed breakdown of our columns in our dataset:

**Relevant Columns:**
- name: Name of the recipe 
- id: unqiue identifier given to each recipe
- nutrition: Nutritional information (list of seven float values)
Includes calories, fat, sugar, protein, saturated fat, sodium, and fiber.
- rating: Individual user ratings 
Rating provided by a user for a recipe, ranging from 0 to 5.
- avg_rating: Average rating for the recipe 
Reflects the cumulative user feedback, ranging from 0 to 5 stars.
- satfat_pdv: Saturated fat as a percentage of the daily value 
Derived from the nutrition column, indicating healthiness concerning saturated fat.
- sugar_pdv: Sugar as a percentage of the daily value 
Derived from the nutrition column, indicating healthiness concerning sugar.
- healthy: Indicator of recipe healthiness 
1 if both satfat_pdv and sugar_pdv are below 5%, 0 otherwise.

By exploring these columns, we aim to determine the relationship between recipe healthiness and user ratings, offering insights into consumer behavior and preferences.

---
## Data Cleaning and Exploratory Data Analysis

### Data Cleaning
Describe, in detail, the data cleaning steps you took and how they affected your analyses. The steps should be explained in reference to the data generating process. Show the head of your cleaned DataFrame (see Part 2: Report for instructions)

We merged the recipe dataset with the ratings dataset using a left join on the id and recipe_id columns. This step ensured that all recipes from the recipe data were retained, along with their associated ratings. Recipes without ratings were included with missing values. We started by filling in any rating of 0 with a missing value because we didn't want to include ratings that weren't given. Then, we filled in those missing values with the mean of the recipe, and dropped the columns with missing rating values. If a recipe had a 0, we can assume it wasn't given a rating or which we wouldn't want to include in our analysis. Then we proceeded to find the average rating for each recipe and added the average rating for a recipe to our dataframe

From our dataset, we wanted to get rid of columns or rows with missing values, as well as columns that weren't useful to our research. With this, we removed a lot of columns with irrelevant data to our research question, ultimately dropping the columns minutes, contributor_id, submitted, tags, n_steps, steps, description, ingredients, n_ingredients, user_id, date, and review.


Next, we obtained our sugar and saturated fat percent daily value columns. We started with the nutrition column and extracted the sugar and saturated fat information and turned them into new columns.

Then, we needed to make a threshold for what would be considered a "healthy" recipe. Using our data, we chose 20% to be the threshold and created a column which would categorize a recipe as healthy or not healthy.  

<iframe
  src="assets/table.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


| name                                 | nutrition                                    |   recipe_id |          user_id |   rating |   avg_rating |   satfat_pdv |   sugar_pdv |   healthy |
|:-------------------------------------|:---------------------------------------------|------------:|-----------------:|---------:|-------------:|-------------:|------------:|----------:|
| 1 brownies in the world    best ever | [138.4, 10.0, 50.0, 3.0, 3.0, 19.0, 6.0]     |      333281 | 386585           |        4 |            4 |           19 |          50 |         0 |
| 1 in canada chocolate chip cookies   | [595.1, 46.0, 211.0, 22.0, 13.0, 51.0, 26.0] |      453467 | 424680           |        5 |            5 |           51 |         211 |         0 |
| 412 broccoli casserole               | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0]    |      306168 |  29782           |        5 |            5 |           36 |           6 |         0 |
| 412 broccoli casserole               | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0]    |      306168 |      1.19628e+06 |        5 |            5 |           36 |           6 |         0 |
| 412 broccoli casserole               | [194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0]    |      306168 | 768828           |        5 |            5 |           36 |           6 |         0 |


### Univariate Analysis
 Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present, and how they answer your initial question.

 **Figure 1** 
<iframe
  src="assets/figure3.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

We wanted to explore the distribution amongst recipes of ratings, and then splitting it into the categories of healthy versus unhealthy ratings. When we created our threshold, there were significantly more unhealthy recipes, so when looking at figure 3, there's significantly more ratings of 5, however, the unhealthy recipes with a rating of 5, of all unhealthy recipes its 74% where healthy recipes with a rating of 5 of all healthy recipes is 75%. So, although the plot depicts more ratings of 5 to unhealthy as opposed to healthy, there's a larger group of unhealthy than healthy, and because the plot is a count of all recipes, it doesn't properly reflect the ratio. The plot is right scewed with less values receiving lower ratings, and most recipes receiving 4 or 5 ratings. 


### Bivariate Analysis
Embed at least one plotly plot that displays the relationship between two columns. Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present and how they answer your initial question.

**Figure 2**
<iframe
  src="assets/figure1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Out of the recipe dataframe, our figures represent a small random sample of the data. This plot shows the distribution of sugar percent daily value amongst ratings. There isn't a significant trend in the data, however, it is noticeable that the recipes with higher ratings tend to have more sugar percent value in them, which informs us that less healthy recipes may have higher ratings.

**Figure 3**
<iframe
  src="assets/figure2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

This figure shows the distribution of saturated fat percent daily value amongst ratings. In this figure, there's even less of a trend in the data, but the recipes with higher ratings tend to have more saturated fat percent value in them, which further solidifies that less healthy recipes may have higher ratings.

### Interesting Aggregates
##TO DO
Embed at least one grouped table or pivot table in your website and explain its significance.

When splitting up our data into healthy vs unhealthy recipes, we found that there were significantly more unhealthy recipes based on our criteria of healthy. 176,135 recipes were unhealthy while 58,293 were considered healthy
Embed at least one grouped table or pivot table in your website and explain its significance.

### Imputation

If you imputed any missing values, visualize the distributions of the imputed columns before and after imputation. Describe which imputation technique you chose to use and why. If you didn’t fill in any missing values, discuss why not.

The one column of missing values that we imputed was the rating column for each recipe. Some recipes had a rating of 0, which we changed to a missing value, because 0 implies a rating was not given and we didn't want the 0 value to scew the average rating. From this we found all the ratings of that recipe got the mean of them and assigned each missing value of that recipe with the mean. We chose mean imputation because filling them in with 0 wouldn't make sense and we felt the mean was most representative of a rating of a recipe. In figure 4 and 5 below, the distributions are provided of ratings before dropping the 0 ratings and after.

**Figure 4 Unimputed Ratings**
<iframe
  src="assets/notdroppedcount.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

**Figure 5 Imputed Ratings**
<iframe
  src="assets/droppedcount.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

---
## Framing a Prediction Problem
Clearly state your prediction problem and type (classification or regression). Report the response variable (i.e. the variable you are predicting) and why you chose it, the metric you are using to evaluate your model and why you chose it over other suitable metrics (e.g. accuracy vs. F1-score). Make sure to justify what information you would know at the “time of prediction” and to only train your model using those features. For instance, if we wanted to predict your Final Exam grade, we couldn’t use your Portfolio Homework grade, because we (probably) won’t have the Portfolio Homework graded before the Final Exam! Feel free to ask questions if you’re not sure. 

###  Prediction Problem
We are looking to predict the rating of recipes based on their nutrition, more specifically, the percent daily values of saturated fat and sugar. If we are given the nutritional information (PDV of saturated fat and sugar), can we accurately predict a user rating of a recipe? This prediction problem will be answered through a linear regression model, as the response variable is the recipe's rating which is a continuous numerical variable.

### Response Variable:
The response variable is the rating of a recipe. Food.com gathers customer's ratings for a recipe which is representative of if consumers liked a recipe; we found this to be a critical indicator of a recipe's success and can provide insights into how nutrition affects both consumer's preferences and ratings.

### Predictor Variables:
The predictor variables we chose are percent daily value of saturated fat and percent daily value of sugar. These features are quantifiable and can tell us how healthy or unhealthy a recipe is which could influence the rating of a recipe. At the time of prediction, we know the nutritional information of a recipe e.g., percent daily values of saturated fat and sugar. These values are known before the recipe is rated, because they are based on the recipe's ingredients.

### Metric to Evaluate our Model

##TO FIX 

We will use the Mean Squared Error (MSE) as the primary evaluation We chose MSE over other metrics because MSE provides a direct measure of prediction error by averaging the squared differences between predicted and actual values, making it straightforward to interpret in the context of ratings. Furthermore, squaring the residuals ensures that larger prediction errors have a disproportionately higher impact on the metric, which is crucial for maintaining prediction quality. MSE is one of the most commonly used metrics for regression tasks and aligns well with the linear regression model we are using.

---
## Baseline Model

Describe your model and state the features in your model, including how many are quantitative, ordinal, and nominal, and how you performed any necessary encodings. Report the performance of your model and whether or not you believe your current model is “good” and why.

**Model**
We used a linear regression model which predicts a recipe's average rating based on the percent daily values of saturated fat and sugar. We chose linear regression because it's easy to interpret and gives us a straightforward relationship between predictors and the response variable.

**Features in the Model**
Saturated Fat PDV (satfat_pdv): Quantitative feature representing the percent daily value of saturated fat in the recipe.
Sugar PDV (sugar_pdv): Quantitative feature representing the percent daily value of sugar in the recipe.
So, total number of quantitative features is 2. There are no ordinal or nominal features and no encoding was necessary for this model and features.


**Performance**
##TO FIX
The baseline model achieved a Root Mean Squared Error (RMSE) of 0.9118. RMSE measures the average magnitude of error between predicted and actual ratings, and lower values indicate better model performance. The baseline model's RMSE of 0.9118 suggests that the predictions are approximately ±0.91 ratings away from the actual ratings on average. This model is "good" because  it's straightforward and interpretable. Also, the RMSE is fairly low based on our 2 features. However, user ratings are influenced by numerous other factors like taste, and personal preferences, which makes it more difficult to predict a rating.

---
## Final Model

State the features you added and why they are good for the data and prediction task. Note that you can’t simply state “these features improved my accuracy”, since you’d need to choose these features and fit a model before noticing that – instead, talk about why you believe these features improved your model’s performance from the perspective of the data generating process.

Describe the modeling algorithm you chose, the hyperparameters that ended up performing the best, and the method you used to select hyperparameters and your overall model. Describe how your Final Model’s performance is an improvement over your Baseline Model’s performance

---
