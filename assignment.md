# Assignment

## Brief

Write the SQL DML statements for the following questions.

## Instructions

Paste the answer as SQL in the answer code section below each question.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql
SELECT rfp.flat_type , MAX(rfp.floor_area_sqm), MIN(rfp.floor_area_sqm) 
FROM main.resale_flat_prices_2017 rfp
GROUP BY flat_type;
```
Please refer to *[PictureQ1](https://github.com/pinghar/5m-data-1.4-sql-basic-dml/blob/main/PictureforQ1(1.4).png)* for the answer.
### Question 2

Select the average price per sqm for flats in each town.

```sql
SELECT town,AVG(rfp.floor_area_sqm) 
FROM main.resale_flat_prices_2017 rfp
GROUP BY rfp.town;
```
Please refer to *[PictureQ2](https://github.com/pinghar/5m-data-1.4-sql-basic-dml/blob/main/PictureforQ2(1.4).png)* for the answer.
### Question 3

Categorize flats into price ranges and count how many flats fall into each category:

- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'
  Show the counts in descending order.

```sql
SELECT
CASE 
	WHEN resale_price < 400000 THEN 'Budget' 
	WHEN resale_price BETWEEN 400000 AND 700000 THEN 'Mid-Range' WHEN resale_price > 700000 THEN 'Premium'
END AS p_r_category,
COUNT(*) AS total_flat
FROM main.resale_flat_prices_2017 rfp
GROUP BY p_r_category
ORDER BY total_flat DESC;
```
Please refer to *[PictureQ3](https://github.com/pinghar/5m-data-1.4-sql-basic-dml/blob/main/PictureforQ3(1.4).png)* for the answer.
### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql
SELECT rfp.town  , rfp."month" ,
COUNT(*) AS total_flat
FROM main.resale_flat_prices_2017 rfp
GROUP BY rfp.town , rfp."month"
HAVING rfp."month" IN ('2017-01','2017-02','2017-03');
```
Please refer to *[PictureQ3](https://github.com/pinghar/5m-data-1.4-sql-basic-dml/blob/main/PictureforQ3(1.4).png)* for the answer.
## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
