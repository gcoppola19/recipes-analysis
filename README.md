# Correlation between calories in a recipe and it's rating
---
## Introduction

This recipe analysis is a data science project, capturing the process of scraping data from a website and through steps of cleaning, and creating various models to answer our research question about our data. Our data set is on various recipes and ratings from food.com. There are 234429 rows in our data set, and we focused mainly on the 'rating' and 'nutrition' columns. The rating column was the given rating for a recipe from a customer. From the nutrition column which was a list of all nutrition facts for a recipe, we extracted data about sugar and saturated fat daily value percentage to create new columns 'sugar_pdv' and 'satfat_pdv.' Then, we created a 'healthy' column which would consider a recipe healthy if the sugar and saturated fat percent daily value were both less than or equal to 20%. We are investigating how nutrition plays a role in recipe ratings: do healthier (PDV of sugar and saturated fat are both <5%) recipes have higher ratings? We hope to find out if people rate healthier meals better than less healthy ones.

---
## Data Cleaning and Exploratory Data Analysis

### Data Cleaning
Describe, in detail, the data cleaning steps you took and how they affected your analyses. The steps should be explained in reference to the data generating process. Show the head of your cleaned DataFrame (see Part 2: Report for instructions)

We obtained data sets for the recipe information from food.com as well as interactions of customers with these receipes i.e. ratings, and reviews. We merged these datasets based on recipe ID to have all the recipe information and it's associated ratings in one table, which was the associated 234429 rows. We started by filling in the recipes that didn't receive any rating from a customer with 0, and then proceeded to find the average rating for each recipe and added the average rating for a recipe to our dataframe. 

Next, we obtained our sugar and saturated fat percent daily value columns. We started with the nutrition column and extracted the sugar and saturated fat information and turned them into new columns. 

From our dataset, we wanted to get rid of columns or rows with missing values, so we found the columns which had missing data. This data was in 'name', 'description', and 'review' columns which wasn't relevant to our research question, so we filled in the missing data with an empty string.

Then, we calculated



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