---
layout: default
title: Introduction
nav_order: 1
---

# Introduction

# Statistical Analysis on Recipes and Nutrition's role in Ratings
This recipe analysis is a data science project, capturing the process of scraping data from a website and through steps of cleaning, and creating various models to answer our research question about our data. The primary focus of the project is to investigate the significance nutrition in the ratings of various recipes on food.com and furthermore if we can predict these ratings based on selected nutrition factors.

## Introduction

 Our data set used for this analysis is on various recipes and user interactions from food.com.  It contains two datasets: one with recipe data like preparation time, and nutrition, and the other with user ratings and reviews for a recipe. We merged these datasets based on recipe ID to have all the recipe information and it's associated ratings in one table. 

 We are investigating how nutrition plays a role in recipe ratings: do healthier (PDV of sugar and saturated fat are both <5%) recipes have higher ratings? We hope to find out if people rate healthier meals better than less healthy ones. Understanding if users appreciate healthier recipes provides valuable insights for recipe developers. It can help in prioritizing creating and promoting recipes that align with consumer preferences for health-conscious eating. 
 
 
 There are 234429 rows in our data set, and we focused mainly on the 'rating' and 'nutrition' columns. The rating column was the given rating for a recipe from a customer. From the nutrition column which was a list of all nutrition facts for a recipe, we extracted data about sugar and saturated fat daily value percentage to create new columns 'sugar_pdv' and 'satfat_pdv.' Then, we created a 'healthy' column which would consider a recipe healthy if the sugar and saturated fat percent daily value were both less than or equal to 20%. 

 
Here's a detailed breakdown of our columns in our dataset:

### Relevant Columns:
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




