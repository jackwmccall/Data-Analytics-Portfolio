## 📚 Excel Heart Attack Risk Assessment Project

For the following project I will be looking at a dataset collected at Zheen Hospital in Erbil, Iraq from January to May 2019. I will go through the steps I took to clean the data, create pivot tables, and design a small example dashboard.

***

📌 **Getting Started**
* After initially loading our .csv into excel, we will start by creating the following three additional sheets.
  * "Heart Attack Project" - This sheet will contain our original dataset and will not be altered.
  * "Working Sheet" - This sheet will be where we clean our data
  * "Pivot Tables" - This sheet will be where we create our pivot tables and test out some graphs
  * "Dashbaord" - This sheet will be where create a small example dashboard containing a few charts and some slicers. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<kbd><img src="https://github.com/user-attachments/assets/220ac9bc-034b-4224-a1ae-ed890b45c4d2" width="400" />

***

📌 **Cleaning the Data**

* Next we will go ahead and copy all of our data over to our working sheet so we can start cleaning. We will apply filters to each column so we can check for typos or outliers.

* The first problem that we notice is the age column is filled with individual ages, i.e., "24", "50", "75" etc. Lets go ahead and create an additional column titled "Age Brackets" so that we can have some cleaner pivot tables later on.

* The following formula will allow us to group each individual into an age bracket.

             =IF(A2>=60,"Senior",IF(A2>=30,"Adult", IF(A2>=20,"Young Adult", IF(A2<20,"Adolescent","Invalid"))))

* The above formula takes anyone under the age of 20 and labels them as "Adolescent", anyone aged 20-29 as "Young Adult", 30-59 as "Adult", and >60 as "Senior" as seen below.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<kbd><img src="https://github.com/user-attachments/assets/0009a80a-11ea-4fa8-add5-558041f285a2" width="280" />

* We will then go ahead and insert similar bracket columns for systolic blood pressure, diastolic blood pressure, and blood sugar.

* We then notice that the gender column has the values "1" and "0" instead of "Male" and "Female" respectively. We will select the entire column and use find and replace to go ahead and change these values from 1s and 0s to "Male" and "female".

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<kbd><img src="https://github.com/user-attachments/assets/9b51a5a8-57f9-4de5-9f64-89a9205dc9c6" width="360" />


* The next issue we find is looking in the filter of the "Heart Rate" column. We see an expected range of values with three outliers of "1111". If we were working with the group that originally collected the data we would ideally be able to bring it to their attention and perhaps get corrected values. For the purpose of this project we will remove the three rows from our sheet however make note of it and leave the rows in the original sheet.

* We then look through the rest of our columns filters and see data within the expected ranges. No problems here, on to the next step. 

***

📌 **Creating our Pivot Tables**
* After cleaning up our data and adding a few additional columns, we can go over to our pivot table sheet and start inserting some tables. We will be creating a total of four total tables that will look at heart attack results (postive or negative) based on gender, systolic BP, diastolic BP, and blood sugar.

* The four pivot tables can be seen below.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<kbd><img src="https://github.com/user-attachments/assets/543283b7-d63b-4a40-8314-08916c7127e7" width="800" />

***

📌 **Dashboard Formatting**
* Now that we have our pivot tables created, we will go ahead and start formatting our dashboard. The first step will be creating charts for each pivot table along with titles, legends, and axis labels as necessary. We will then move over to our "Dashboard" sheet and remove the gridlines, create a nice title, and insert our charts.

* We will also add in three slicers on the left hand side of the dashboard that will allow us to filter the charts based on our desired parameters. We will add in slicers for "Gender", "Risk Level", and "Age Brackets".

* The final dashboard can be seen below. 


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<kbd><img src="https://github.com/user-attachments/assets/d4c53e8c-29ca-4b6e-a00e-2a2a10b29790" width="620" />




