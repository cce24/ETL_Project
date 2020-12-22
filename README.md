# ETL_Project

###ETL_Project

Extract: Two CSV files were pulled from Kaggle where the user did some web scraping on Glassdoor to find job listings for 1) Data Analysts (https://www.kaggle.com/andrewmvd/data-analyst-jobs) and 2) Data Scientists (https://www.kaggle.com/andrewmvd/data-scientist-jobs). These two datasets were chosen to further our analysis of Project 1 into Project 2 in discovering what skillsets are looked for, what the salary ranges, and what the company revenue is currently as the new datasets are from 2020 while our previous analysis used datasets from 2018. Columns for both datasets were the same which help facilitated the merging. The files were then imported into Pandas using Jupyter Notebook and transformation was done. Transform: To transform the dataset, the following was done: csv1 = DataAnalyst.csv csv2 = DataScientist.csv

 The csv files was read into pandas and loaded into Jupyter Notebook.
 An unnamed column was removed from both csv1 and csv2 so we have clean columns to work with.
 In csv2, an extra index column was removed.
 An outer merge was done to merge the two csv files together.
 More unnecessary columns are then dropped such as “Rating”, “Competitors”, “Easy Apply”, and “Founded”.
 Since the column we want to work with consists of strings that needed to be split and converted into integers so calculations can be done, the following steps were applied:
a. Salary i. Removing the “Glassdoor est.’, “Employer est.”, “$”, “K”, and “()” from the Salary column so we are left with just numbers. ii. Removing the “Per Hour” listing entirely so we can work with annual salary iii. The value ranges left were then split on the character “-“ with new column names called “Salary Bottom” and “Salary Top”.

 Example: “37-66” was split into two columns with 37 being “Salary Bottom” and 66 being “Salary Top”.
b. Revenue i. Replacing “Unknown/Non-Applicable” values with 0. ii. Removing the “USD”, “$”, and “()” from the Revenue column so we are left with just numbers. iii. Copying the unit values (millions/billions) into a new column called “Revenue – Units” and removing it from the parent column so there are only value ranges. iv. The Revenue value ranges are then split on the character “-“ with the starting range called “Revenue Bottom” and the end range called “Revenue Top”. 7. The salary and revenue columns were then converted into integers so the mean can be calculated. 8. New columns (“Revenue Midpoint” and “Salary Midpoint”) were created to store the mean between the “Revenue Bottom”/“Revenue Top” AND “Salary Bottom”/“Salary Top”, respectively. 9. New column “Salary Unit” was added to show the salary units. 10. The columns were reorganized in the order we wanted and exported as CSV. Load:

 A database was created in PgAdmin called “ETL_Project”
 A server connection was created in Jupyter Notebook
 The final CSV file was uploaded into the ETL_Project database
