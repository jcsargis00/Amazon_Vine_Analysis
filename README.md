## Amazon_Vine_Analysis
#
ETL on Amazon Product Reviews
#
Using the AWS RDS database with tables in Postgres pgAdmin, the electronics dataset from Amazon reviews was extracted into a dataframe using Google Colab and PySpark.  The data matched the
schema from SQL_table_schema, creating 4 tables in Postgres.
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

