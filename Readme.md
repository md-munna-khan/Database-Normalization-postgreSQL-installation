Slide Link: https://drive.google.com/file/d/1Sp_11zUXL8u6lKK7cJ4s4an8cjJ-JNU7/view?usp=sharing



In this module, we will explore data anomalies and the different types of anomalies in DBMS.

You’ll learn normalization step by step – from 1NF to 3NF – with clear examples.

We will also cover resolving many-to-many relationships and updating ER diagrams using junction tables.

## 43-1 Data Anomalies and Types of Anomalies in DBMS
#### Anomalies
- Imbalance in database is called anomalies
- Anomalies in databases refer to inconsistencies or unexpected issues that can occur during data manipulation or retrieval
#### Types Of Anomalies
- Update Anomalies
- Delete Anomalies
- Insert Anomalies
![alt text](image.png)
- Here Branch Dhaka and address Rampura came multiple times which is data duplication. suppose the branch name changes to Khilgao we have to update each Dhaka manually
- If there is data duplications in a table we will say there is any of the anomalies
![alt text](image-2.png)
- Hassan works in barisal bagher bazar. If we delete hasan barisal branch information will be gone This is called delete anomalies
![alt text](image-1.png)
- Suppose new person came and we have gave wrong address. Dhaka branch address will be different. we need some validations like it should be Rampura.
- This kind of table separations are called Normalizations

## 43-2 Normalization and Functional Dependency
- Normalization is a step by step process by using which we can remove any anomalies in our database
## Functional Dependency
- Functional dependency in simple terms means that the value of one attribute (or set of attributes) uniquely determines the value of another attribute(s) in a table        
![alt text](image-3.png)
![alt text](image-5.png)
![alt text](image-4.png)
## 43-3 1NF Explained | First Normal Form with Easy Example
#### Normal Forms
- A set of rules applied to a database table to reduce redundancy and avoid anomalies in data by organizing it properly
#### Type of normal forms
- 0NF
- 1NF
- 2NF
- 3NF

 #### 1NF
 Rules :
- Atomic Values (like address Broken in small pieces like house, road, sector)
- Unique Column Names
- Can not have Positional dependency of data
- Column should contain data that are of the same type
- Determine Primary key
![alt text](image-6.png)
- all rules followed

- lets see the table where is the problem and how to convert in 1NF
- So far we have unique column names it ok
- we have no positional dependency of data
- In title we have to keep title not number
- and in course the atomicity is not maintained here is multiple course in one field
- lets fix this
![alt text](image-7.png)
- here comes the 1NF conversion
- Still data duplication came in serial number and title
- here we have to consider composite primary key for determining uniquely
- These will be fixed in 2NF
## 43-4 2NF Explained | Second Normal Form in DBMS 
 #### 2NF
- Rules :
- 1 Must be 1NF
- 2 No non-key attribute should functionally depend on part of a candidate key
![alt text](image-8.png)
![alt text](image-9.png)
- Here we can see the table is in 1NF and has a composite primary key is combination of std_id, c_id. whose are also primary key

- but here is a problem with table that using the partial primary key attribute c_id we can determine c_name(non key attribute). and this is not following the 2NF 2nd rule.here c_id is functionally dependent on c_name. That means c_id can determine c_name

- If we want to convert in 2NF we have to separate the table because according to rule no non key attribute can not depend on the part of a candidate_key

- Here comes another problem ❌lossy decomposition that means there is no relation with stud_id right now. we have to make relation.
![alt text](image-10.png)
✅Loss less decomposition
## 43-5 3NF Explained | Third Normal Form with Examples
#### transitive dependency
#### 3NF
- Rules :
- 1 Must be 2NF
- 2 Must not contain transitive dependency
x=>determine y and y===>z its y === determine z 
![alt text](image-11.png)
\![alt text](image-12.png)
- Suppose X can determine Y and Y can determine Z. Technically we can determine Z indirectly using Y. Thi is Transitive Dependency.
- In this table there is transitive dependency. because using stud_id we can determine each and every field uniquely. In this way using stud_id we can determine state. But here the problem comes state can also determine the country. This is transitive dependency. We have to mange this separating the tables.

![alt text](image-13.png)
❌lossy decomposition because you now not say which student come from which country
✅ remove transitive dependency  the solution is add state attribute
![alt text](image-14.png)
#### Database design
![alt text](image-15.png)
## 43-6 Resolving Many-to-Many Relationship
- We don't want two tables has many to many relationship because handling it becomes tough
![alt text](image-16.png)
- The table will look like this. this will not work because atomicity is not maintained
![alt text](image-17.png)
- We have to solve this. We will simply divide in rows
![alt text](image-18.png)
- Here Another problem arose Partial dependency came i mean using the id we cen identify the name. According to the rule of 2 NF we can not let this happen
![alt text](image-20.png)
- here another problem arose like too many empty fields came we can not keep anything that takes space without any reason
- we have to make Junction Table / bridge table to make the table
![alt text](image-21.png)
- one ti many relation
![alt text](image-22.png)