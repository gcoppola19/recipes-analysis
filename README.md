# Statistical Analysis on Recipes and Nutrition's role in Ratings
This recipe analysis is a data science project, capturing the process of scraping data from a website and through steps of cleaning, and creating various models to answer our research question about our data. The primary focus of the project is to investigate the significance nutrition in the ratings of various recipes on food.com and furthermore if we can predict these ratings based on selected nutrition factors.

---
## Introduction

 Our data set used for this analysis is on various recipes and user interactions from food.com.  It contains two datasets: one with recipe data like preparation time, and nutrition, and the other with user ratings and reviews for a recipe. We merged these datasets based on recipe ID to have all the recipe information and it's associated ratings in one table. 

 We are investigating how nutrition plays a role in recipe ratings: do healthier (PDV of sugar and saturated fat are both <5%) recipes have higher ratings? We hope to find out if people rate healthier meals better than less healthy ones. Understanding if users appreciate healthier recipes provides valuable insights for recipe developers. It can help in prioritizing creating and promoting recipes that align with consumer preferences for health-conscious eating. 
 
 
 There are 234429 rows in our data set, and we focused mainly on the 'rating' and 'nutrition' columns. The rating column was the given rating for a recipe from a customer. From the nutrition column which was a list of all nutrition facts for a recipe, we extracted data about sugar and saturated fat daily value percentage to create new columns 'sugar_pdv' and 'satfat_pdv.' Then, we created a 'healthy' column which would consider a recipe healthy if the sugar and saturated fat percent daily value were both less than or equal to 20%. 

 
Here's a detailed breakdown of our columns in our dataset:

Relevant Columns:
name: Name of the recipe 
id: unqiue identifier given to each recipe
nutrition: Nutritional information (list of seven float values)
Includes calories, fat, sugar, protein, saturated fat, sodium, and fiber.
avg_rating: Average rating for the recipe (float)
Reflects the cumulative user feedback, ranging from 0 to 5 stars.
satfat_pdv: Saturated fat as a percentage of the daily value (float)
Derived from the nutrition column, indicating healthiness concerning saturated fat.
sugar_pdv: Sugar as a percentage of the daily value (float)
Derived from the nutrition column, indicating healthiness concerning sugar.
healthy: Indicator of recipe healthiness (integer, 1 or 0)
1 if both satfat_pdv and sugar_pdv are below 5%, 0 otherwise.
rating: Individual user ratings 
Rating provided by a user for a recipe, ranging from 0 to 5.

By exploring these columns, we aim to determine the relationship between recipe healthiness and user ratings, offering insights into consumer behavior and preferences.

---
## Data Cleaning and Exploratory Data Analysis

### Data Cleaning
Describe, in detail, the data cleaning steps you took and how they affected your analyses. The steps should be explained in reference to the data generating process. Show the head of your cleaned DataFrame (see Part 2: Report for instructions)

We merged the recipe dataset with the ratings dataset using a left join on the id and recipe_id columns. This step ensured that all recipes from the recipe data were retained, along with their associated ratings. Recipes without ratings were included with missing values. We started by filling in the recipes that didn't receive any rating from a customer with 0, and then proceeded to find the average rating for each recipe and added the average rating for a recipe to our dataframe.  

From our dataset, we wanted to get rid of columns or rows with missing values, so we found the columns which had missing data. This data was in 'name', 'description', and 'review' columns which wouldn't affect our research question, so we filled in the missing data with an empty string.

Next, we obtained our sugar and saturated fat percent daily value columns. We started with the nutrition column and extracted the sugar and saturated fat information and turned them into new columns.

Then, we needed to make a threshold for what would be considered a "healthy" recipe. Using our data, we chose 20% to be the threshold and created a column which would categorize a recipe as healthy or not healthy.  

<iframe
  src="assets/recipeshead.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>



### Univariate Analysis
Embed at least one plotly plot you created in your notebook that displays the distribution of a single column (see Part 2: Report for instructions). Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present, and how they answer your initial question. (Your notebook will likely have more visualizations than your website, and that’s fine. Feel free to embed more than one univariate visualization in your website if you’d like, but make sure that each embedded plot is accompanied by a description.)

### Bivariate Analysis
Embed at least one plotly plot that displays the relationship between two columns. Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present and how they answer your initial question. (Your notebook will likely have more visualizations than your website, and that’s fine. Feel free to embed more than one bivariate visualization in your website if you’d like, but make sure that each embedded plot is accompanied by a description.)

### Interesting Aggregates
Embed at least one grouped table or pivot table in your website and explain its significance.

### Imputation
If you imputed any missing values, visualize the distributions of the imputed columns before and after imputation. Describe which imputation technique you chose to use and why. If you didn’t fill in any missing values, discuss why not.

---
## Framing a Prediction Problem

---
## Baseline Model

---
## Final Model

<iframe
  src="assets/figure1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/figure2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/figure3.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>