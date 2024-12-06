---
layout: default
title: Data Cleaning and Exploratory Data Analysis
nav_order: 2
---

# Cleaning
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



### Univariate Analysis
 Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present, and how they answer your initial question.

 ### Figure 1 
<iframe
  src="assets/figure3.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

We wanted to explore the distribution amongst recipes of ratings, and then splitting it into the categories of healthy versus unhealthy ratings. When we created our threshold, there were significantly more unhealthy recipes, so when looking at figure 3, there's significantly more ratings of 5, however, the unhealthy recipes with a rating of 5, of all unhealthy recipes its 74% where healthy recipes with a rating of 5 of all healthy recipes is 75%. So, although the plot depicts more ratings of 5 to unhealthy as opposed to healthy, there's a larger group of unhealthy than healthy, and because the plot is a count of all recipes, it doesn't properly reflect the ratio. The plot is right scewed with less values receiving lower ratings, and most recipes receiving 4 or 5 ratings. 


### Bivariate Analysis
Embed at least one plotly plot that displays the relationship between two columns. Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present and how they answer your initial question.

### Figure 2
<iframe
  src="assets/figure1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Out of the recipe dataframe, our figures represent a small random sample of the data. This plot shows the distribution of sugar percent daily value amongst ratings. There isn't a significant trend in the data, however, it is noticeable that the recipes with higher ratings tend to have more sugar percent value in them, which informs us that less healthy recipes may have higher ratings.

### Figure 3
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

##TO FIX TO FIX

If you imputed any missing values, visualize the distributions of the imputed columns before and after imputation. Describe which imputation technique you chose to use and why. If you didn’t fill in any missing values, discuss why not.

The values we imputed were all related to text involving descriptions or reviews, so we filled them in with an empty string as it didn't have an affect on the data we were looking at and done for completeness. All nutrition information was provided which was what we were mainly looking at. In terms of ratings, we filled in any column that had a rating of 0, meaning it didn't recieve a rating as NaN because we didn't want it to affect our average rating number.

---