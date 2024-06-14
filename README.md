# Hive Data Warehouse Project 

I have done it in cooperation with <a href="https://www.github.com/Azirral">Adam Sobczuk</a>

## Task Description
Please choose a subject and implement a data warehouse for it. Your solution must contain:

- at least three types of data storing,

- internal and external tables,

- partitioning (static and dynamic),

- at least two different complex types,

- bucketing.

Define in natural language 10 competency questions and scenarios, which explain why the specific design decisions were made.

Prepare 10 HQL queries corresponding to the competency questions.

You should upload:

1. HQL script creating the data warehouse.

2. Exemplary data and a script loading this data.

3. HQL script with 10 competency questions.

4. Short text file containing scenarios and explanation of the decisions made.

## Project Description

This warehouse is based on previous worked we had done on Data Warehouse subject.  

The Data warehouse is designed for Feeding kids business process. The process of feeding kids in the school canteen is as follows:  

The day before cantina workers assess how much food they need to prepare for the next day. The kids each day can go to the school canteen and eat lunch there. 
The canteen workers prepare a list of students in excel who eat lunch every day. At the end of the day the remaining food is summed up and then if necessary thrown out.

### Decisions Made:
#### Structured and Nested Data
Utilizing structured and nested data types like STRUCT and MAP in the meal table allows for a flexible representation of meal information. This approach enables the storage of courses as a structured entity and additional information as key-value pairs in a map.
#### Partitioning for Date, Country and Age Category
Partitioning the date_dim table by season, the kindergarten table by country and the student by age_category supports efficient data retrieval based on these key attributes. Partitioning is beneficial for optimizing query performance, especially when filtering on commonly used dimension
#### Bucketing for Eating Age Meal Serving ID
Using bucketing on the student table by meal_serving_id distributes the data evenly across the specified number of buckets. This can improve query performance for analytics that involve filtering or joining based on age categories.
#### Storage Formats for Data Files
Choosing different file formats ( SEQUENCE, PARQUET, ORC, TEXTFILE) for the tables is based on the trade-offs between storage efficiency, query performance, and compatibility with specific tools. For example TEXTFILE allows data modification as it’s not a binary format.
#### External Table for Date Dimension
Creating an external table for date_dim allows flexibility in managing data storage locations. External tables are useful when the data is stored outside the Hive warehouse directory, and the schema can be projected onto the data stored in a different location.

### Competency questions:
1. Retrieve the total amount of money invested in meals for each kindergarten in the year 2023.  
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/0d414991-cf13-4e51-852e-d755cb30d073)

2. List the top 3 kindergartens with the highest average food wastage per meal.  
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/38b73a5a-ac70-4928-bda2-5bb3431b3722)

3. Retrieve the names and addresses of kindergartens in Poland.  
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/65ad8d4d-46e2-481a-9319-0cadc3e203f7)

4. Find the total number of meals served on each day of the week during the Summer season.  
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/687d7473-5709-492d-8740-0e5534afda28)

5. Retrieve the meals with their respective calorie content and protein amounts, filtering for meals with more than 25 grams of protein.  
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/f3ec1e26-b0ac-4d9a-a984-19c39524d6c2)


6. Retrieve the age category with the highest number of current students.  
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/22b4418c-3898-4a21-8393-cc20366b68af)

7. Calculate the average amount of food bought per month for each kindergarten.  
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/f702cd75-7703-4599-8007-e09d6c5149cb)

8. Find the total number of meals served in each season.    
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/04734aec-ff67-4fa8-9fd2-4cb5d7f1be54)

9. Find the total amount of money invested in meals for each age category of students.    
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/2ec69204-84db-4748-9c3a-c208d2e0cac6)


10. Retrieve information about students who attended meals, including their names, the date of the meal, and the amount of food wasted for each meal.  
![image](https://github.com/janekludwicki/Hive_Data_Warehouse_Project/assets/132893147/d121a66a-9581-4e55-b11e-0dc6b613290e)
<i>(Only part shown)</i>

