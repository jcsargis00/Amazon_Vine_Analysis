## Amazon_Vine_Analysis
#
Using ETL to analyze Amazon Product Reviews
#
Using the AWS RDS database with tables in Postgres pgAdmin, the electronics dataset from Amazon reviews was extracted into a dataframe using Google Colab and PySpark.  The data matched the
schema from SQL_table_schema, creating 4 tables in Postgres.
#
### Overview of the analysis: 
The purpose of this project is to analyze Amazon reviews written by members of the paid Amazon Vine program to determine if there are biases between Vine member (paid) and Non Vine member (unpaid) reviews.
#
What is Amazon Vine?
#
From the Amazon Vine website:
"Amazon Vine invites the most trusted reviewers on Amazon to post opinions about new products to help their fellow customers make informed purchase decisions. Amazon invites buyers to become Vine reviewers, also known as Vine Voices, based on the insightfulness of the reviews they published on their Amazon purchases. If you participate, you can provide free units of your products for this selected group of Vine Voices to post customer reviews for the products you submit. You can build awareness of your product, boost the sales of your slow and cold start ASINs, and helps customers make informed decisions about new products you offer by participating in Vine.  We monitor the active participation of Vine Voices and their contribution to the program. Only the best reviewers will remain in Vine."
#
Free products for reviewers may be provided by brands seeking an Amazon review. In order to determine if there is any bias towards favorable reviews due to the free products received by Vine members vs. non-members, we need to identify the percentage of 5 star ratings to total rating in each category. 
#
#### Tools, Schema and Dataset Used
* AWS RDS
* PySpark 
* SQL
* Postgres
* Google Colab
* SQL table schema
* Amazon ETL starter code
* Electronics Amazon Review dataset
#
Schema used:
#
![schema](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/schema.PNG)

#
review_id_table schema
#
![r_id](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/review_id_schema.PNG)
#
customers_table schema
#
![c_id](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/customers_schema.PNG)
#
products_table schema
#
![p_id](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/products_schema.PNG)
#
vine_table schema
#
![v_id](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/vine_schema.PNG)
#
### The datasets were transformed into 4 DataFrames shown below
#
Customers Dataframe
#
![c_df](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/customerdf.PNG)
#
Products Dataframe
#
![p_df](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/productdf.PNG)
#
Review ID Dataframe
#
![r_df](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/reviewdf.PNG)
#
Vine Dataframe
#
![v_df](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/vinedf.PNG)
#
### DataFrames were loaded into Postgres pgAdmin
#
Customers Table in Postgres DB
#
![c_db](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/customers.PNG)
#
Products Table in Postgres DB
#
![p_db](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/products.PNG)
#
Review ID Table in Postgres DB
#
![r_db](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/review_id.PNG)
#
Vine Table in Postgres DB
#
![v_db](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/vine.PNG)
#
### Determine Bias of Vine Reviews
#
Using PySpark in Google Colab, the data was filtered to create a new DataFrame comprised of reviews
with a total count of greater than or equal to 20 votes in order to select reviews more likely to be helpful and to avoid division by zero errors in future calculations.
#
Total Votes Greater than or equal to 20 was stored in total_votes_df.
#
![totvotes20](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/totalvotes.PNG)
#
The data was further filtered into a new DataFrame where the number of helpful votes divided by the total number of votes was great than or equal to 50% called percent_votes_df.
#
![percent](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/percent.PNG)
#
A new dataframe that retrieved a review that was part of the Vine program (paid) was stored in paid_df.
#
![percent](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/paid.PNG)
#
A new dataframe that retrieved a review that was not part of the Vine program (unpaid) was stored in non_paid_df.
#
![percent](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/nonpaid.PNG)
#
The total number of reviews, the number of 5 star reviews and the % of 5-star reviews for the two types of reviews (paid and unpaid) were filtered into ratings_total_df
#
![percent](https://github.com/jcsargis00/Amazon_Vine_Analysis/blob/main/images/reviewratings.PNG)
#

### Results: 
The dataset had over 3 million reviews recorded. In order to focus on reviews that would be considered more likely to be helpful, first the data was filtered.
Filtering:
* Count of Total Votes equal or greater than 20.
* Percent of Helpful Votes to Total Votes equal thenor greater than 50%.
#
Next, data was reviewed for Vine and Non-Vine reviewers.
#
What percentage and number of reviews were made by Vine vs. Non-Vine reviewers?
* Vine  2.1% (1,080) 
* Non-Vine 97.9% (49,659)
#
How many Vine reviews were 5 stars? 
* 454 out of 1,080 
#
How many non-Vine reviews were 5 stars?
* 23,043 out of 49,673 
#
What percentage of Vine reviews were 5 stars? 
* 42.03403% 
#
What percentage of non-Vine reviews were 5 stars?
* 46.3893% 

### Summary:
The results show the percentage of Vine reviewers and the percentage of Non-Vine reviewers was very close (42% vs. 46%). The data finding implies the Vine reviewers are not showing bias for this dataset.  This finding only includes filtered data, with criteria of greater than or equal to 20 helpful votes, and only 5 star votes.  The analysis could be rerun for all data, after excluding zero data.  It would also be advantageous to see the analysis on several other datasets and compare the results before reaching a conclusion. 