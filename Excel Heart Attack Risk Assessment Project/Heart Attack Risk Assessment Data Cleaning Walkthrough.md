# -Excel- Heart Attack Risk Assessment Data Cleaning

For the following project I will be looking at a dataset collected at Zheen Hospital in Erbil, Iraq from January to May 2019. I will go through the steps I took to clean the data, create pivot tables, and a small example dashboard.

***

1. After initially loading our .csv into excel, we will start by creating three additional sheets. Our first original sheet will contain our raw data and will not be altered. Our second sheet will be titled "Working Sheet" and will be where we clean our data. The third sheet will be labled "Pivot Tables" and will be where we create our pivot tables and test out some graphs. Our final sheet will be labeld "Dashboard" and will be where we create a small example dashboard containing our charts and a few slicers.

    <kdb><img src="https://github.com/user-attachments/assets/220ac9bc-034b-4224-a1ae-ed890b45c4d2" width="400" />

***

2. Next we will go ahead and copy all of our data over to our working sheet so we can start cleaning. We will apply filters to each column so we can check for typos or outliers. The first problem that we notice is the age column is filled with individual ages, i.e., "24", "50", "75" etc. Lets go ahead and create an additional column titled "Age Brackets" so that we can have some cleaner pivot tables later on. The following formula will allow us to group each individual into an age bracket.

 =IF(A2>=60,"Senior",IF(A2>=30,"Adult", IF(A2>=20,"Young Adult", IF(A2<20,"Adolescent","Invalid"))))

 The above formula takes anyone under the age of 20 and labels them as "Adolescent", anyone aged 20-29 as "Young Adult", 30-59 as "Adult", and >60 as "Senior" as seen below.

 <kbd><img style="float: right;" src="https://github.com/user-attachments/assets/0009a80a-11ea-4fa8-add5-558041f285a2" width="200" />

 We will then go ahead and insert similar bracket columns for systolic blood pressure, diastolic blood pressure, and blood sugar.

 ***

 3. We then notice that the gender column has the values "1" and "0" instead of "Male" and "Female" respectively. We will select the entire column and use find and replace to go ahead and change these values from 1s and 0s to "Male" and "female".

<kbd><img src="https://github.com/user-attachments/assets/9b51a5a8-57f9-4de5-9f64-89a9205dc9c6" width="360" />

***

4. The next issue we find is looking in the filter of the "Heart Rate" column. We see an expected range of values with three outliers of "1111". If we were working with the group that originally collected the data we would ideally be able to bring it to their attention and perhaps get corrected values. For the purpose of this project we will remove the three rows from our sheet however make note of it and leave the rows in the original sheet. We then look through the rest of our columns filters and see data within the expected ranges.

***

5. After cleaning up our data and adding a few additional columns, we can go over to our pivot table sheet and start inserting some tables. We will be creating four total tables that will look at heart attack results (postive or negative) based on gender, systolic BP, diastolic BP, and blood sugar. The four pivot tables can be seen below.








