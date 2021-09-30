# Amazon Vine Analysis with AWS

## I. Overview

### Background

The Amazon Vine program is a service that allows manufacturers and publisher to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

In this project, I picked 1 out of 50 datasets that each contains reviews of a specific product. The one I picked contains 3,093,869 reviews on electronic products. 

### Purpose

The purpose of this project is to determine if there is any bias toward favorable reviews (5-star reviews) from the Vine members in the dataset.

-	I used PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS, and loaded the transformed data into pgAdmin. 
-	Then I used PySpark to determine if there is bias.
-	The last section includes a summary of the analysis.

## II. Results

**Sufficient Reviews:**

In order to get sufficient result, I did the following steps to filter the dataset.

1.	Filter the data to retrieve all the rows where the review receives more than 20 votes.

2.	Filter the data again to retrieve all the rows where more than 50% votes are “helpful votes”.

3.	Filter the data to retrieve paid reviews by Vine and unpaid reviews.

**Vine Paid Reviews:**

<img width="589" alt="Screen Shot 2021-09-29 at 10 02 53 PM" src="https://user-images.githubusercontent.com/84211948/135414300-de58a9bb-48db-46a8-8cf4-8991185d9206.png">

-	Among the sufficient reviews for electronics, there are 1080 reviews marked as paid by Vine.
-	Among the 1080 Vine reviews, there are 454 favorable reviews (5-star reviews)
-	Overall, 42% paid reviews are 5-star reviews.

**Unpaid Reviews:**

<img width="654" alt="Screen Shot 2021-09-29 at 10 03 14 PM" src="https://user-images.githubusercontent.com/84211948/135414332-fd9b4975-6396-4433-b786-252167c9d011.png">

-	Among the sufficient reviews for electronics, there are 49673 reviews marked as unpaid.
-	Among the 49673 unpaid reviews, there are 23043 favorable reviews (5-star reviews)
-	Overall, 46% unpaid reviews are 5-star reviews.

## III. Summary

- From the dataset I chose, 42% paid customers provided 5-star reviews, 4% less compared to the 46% unpaid users who provide 5-star reviews. Therefore, we cannot conclude there’s a positivity bias that paid users tend to provide favorable reviews. 
- However, it is insufficient to determine whether there’s any bias based on one set of analysis. As recommendations, we can conduct the following analysis to further investigate:
  1. The percentage of 1- and 2-star reviews (low reviews) of paid and unpaid reviews. To determine wether paid customers tend to avoid leaving low reviews.
  2. The statistical distribution of the reviews: mean, median, mode of paid and unpaid reviews, to analysis the review distributions by each type of customer.



