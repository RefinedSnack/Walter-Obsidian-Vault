---  
share: "true"  
---  
# Understanding the Datalog Programming Language: A Comprehensive Overview for CS 236 Discrete Mathematics Course at BYU  
  
For easy viewing the file is hosted at the following link: https://tinyurl.com/316-DeGering  
## Table of Contents  
---  
- [Introduction](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Introduction)  
- [The Datalog Programming Language](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##The-Datalog-Programming-Language)  
- [Syntax](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Syntax)  
	- [Schemes](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Schemes)  
		- [snap](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##snap)  
		- [csg](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##csg)  
		- [cn](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##cn)  
		- [ncg](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##ncg)  
	- [Facts](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Facts)  
		- [snap](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##snap)  
		- [csg](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##csg)  
		- [cn](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##cn)  
		- [ncg](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##ncg)  
	- [Rules](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Rules)  
		- [Head](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Head)  
		- [Body](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Body)  
		- [snap](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##snap)  
		- [csg](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##csg)  
		- [cn](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##cn)  
	- [Queries](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Queries)  
	- [Summary](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Summary)  
	- [Conclusion](Understanding%2520the%2520Datalog%2520Programming%2520Language%2520A%2520Comprehensive%2520Overview%2520for%2520CS%2520236%2520Discrete%2520Mathematics%2520Course%2520at%2520BYU.md##Conclusion)  
  
  
## Introduction  
---  
  
The programming assignment for this course is the creation of a Datalog Interpreter. This was chosen because it will require the application of many of the discrete principles that the lecture will focus on. The aim is to show an application of the abstract concepts covered in the course.    
    
This description will provide a high-level overview of the structure and application of the Datalog Programming Language. Second, an in-depth exploration of the internal components of the Datalog Interpreter.  
  
    
## The Datalog Programming Language    
---  
  
Definition:   
  
>Datalog is a declarative logic programming language that is commonly used in computer science to represent and manipulate data. Datalog uses relation algebra (a branch of discrete mathematics that will be covered later in the course) to represent, generate, and evaluate data.  
  
  
Datalog can be thought as creating distinct tables like an excel spreadsheet. These tables (sometimes called relations) have three parts:  
1. A distinct name  
2. A header row with column labels  
3. 0 or more rows of data (sometimes called a tuple)  
  
  
## Syntax  
---  
  
Example:  
```c++  
Schemes:  
  snap(StudentID,Name,Address,PhoneNumber)  
  csg(Course,StudentID,Grade)  
  cn(Course,Name)  
  ncg(Name,Course,Grade)  
  
Facts:  
  snap('12345','C. Brown','12 Apple St.','555-1234').  
  snap('22222','P. Patty','56 Grape Blvd','555-9999').  
  snap('33333','Snoopy','12 Apple St.','555-1234').  
  csg('CS101','12345','A').  
  csg('CS101','22222','B').  
  csg('CS101','33333','C').  
  csg('EE200','12345','B+').  
  csg('EE200','22222','B').  
  
Rules:  
  cn(Course,Name) :-   
		snap(StudentID,Name,Address,PhoneNumber),  
		csg(Course,StudentID,Grade).  
  
Queries:  
  cn('CS101',Name)?  
  ncg('Snoopy',Course,Grade)?  
```  
    
The above code contains several relevant patterns. It is first divided up into 4 distinct sections. `Schemes`, `Facts`, `Rules`, and `Queries`. Each section has it's own significance. Each of these four sections is composed of Predicates.  
  
A Predicate is a syntactic form common in mathematics and computer science. It is composed of a name which is written first then a list of parameters. `snap(StudentID,Name,Address,PhoneNumber)` is a predicate the name is `snap` and the parameters are `StudentID`, `Name`, `Address`, and `PhoneNumber`  
  
### Schemes  
---  
  
The `Schemes` section of the code is comprised of 1 or more predicates. Each predicate defines the structure or the `schema` of a table. The name of the predicate defines the name of the table and each parameter becomes a column label.  
  
Example:  
```c++  
Schemes:  
  snap(StudentID,Name,Address,PhoneNUmber)  
  csg(Course,StudentID,Grade)  
  cn(Course,Name)  
  ncg(Name,Course,Grade)  
```  
  
The above code snippet will produce the following tables:  
  
#### snap  
  
 | StudentID | Name | Address | PhoneNumber |  
 | --------- | ---- | ------- | ----------- |  
 |           |      |         |             |  
  
#### csg  
  
 | Course | StudentID | Grade |  
 | ------ | --------- | ----- |  
 |        |           |       |  
  
#### cn  
  
 | Course | Name |  
 | ------ | ---- |  
 |        |      |  
  
#### ncg  
  
 | Name | Course | Grade |  
 | ---- | ------ | ----- |  
 |      |        |       |  
  
*Every valid datalog program __must__ contain 1 or more `Schemes`.*  
  
### Facts  
---  
  
The `Facts` section of the code is comprised of 0 or more predicates. Each predicate defines an individual row of a table. The name of the predicate defines which of the tables the row belongs to and each parameter becomes the value of that cell. The below code segment will add 3 rows to the `snap` table and 5 to the `csg` table. Duplicate rows will only be added once to each table.  
  
Example:  
```c++  
Facts:  
  snap('12345','C. Brown','12 Apple St.','555-1234').  
  snap('22222','P. Patty','56 Grape Blvd','555-9999').  
  snap('33333','Snoopy','12 Apple St.','555-1234').  
  csg('CS101','12345','A').  
  csg('CS101','22222','B').  
  csg('CS101','33333','C').  
  csg('EE200','12345','B+').  
  csg('EE200','22222','B').  
```  
  
#### snap  
  
 | StudentID | Name       | Address         | PhoneNumber |  
 | --------- | ---------- | --------------- | ----------- |  
 | '12345'   | 'C. Brown' | '12 Apple St.'  | '555-1234'  |  
 | '22222'   | 'P. Patty' | '56 Grape Blvd' | '555-9999'  |  
 | '33333'   | 'Snoopy'   | '12 Apple St.'  | '555-1234'  |  
  
#### csg  
  
 | Course  | StudentID | Grade |  
 | ------- | --------- | ----- |  
 | 'CS101' | '12345'   | 'A'   |  
 | 'CS101' | '22222'   | 'B'   |  
 | 'CS101' | '33333'   | 'C'   |  
 | 'EE200' | '12345'   | 'B+'  |  
 | 'EE200' | '22222'   | 'B'   |  
  
#### cn  
 | Course | Name |  
 | ------ | ---- |  
 |        |      |  
  
#### ncg  
  
 | Name | Course | Grade |  
 | ---- | ------ | ----- |  
 |      |        |       |  
  
*Every valid datalog program can contain 0 or more `Facts`.*  
  
### Rules  
---  
  
`Rules` are used to generate new facts or relationships from existing facts. A rule consists of a head and a body, separated by a colon and dash (`:-`). The head of the rule defines the new relationship being generated, while the body contains the conditions that must be satisfied in order for the new relationship to hold true.  
  
Example:  
  
```c++  
Rules:  
  cn(Course,Name) :-   
	snap(StudentID,Name,Address,PhoneNumber),  
	csg(Course,StudentID,Grade).  
```  
  
The above code snippet defines 1 rule which is broken up into 2 parts  
  
#### Head  
```c++  
cn(Course,Name)  
```  
#### Body  
```c++  
	snap(StudentID,Name,Address,PhoneNumber),  
	csg(Course,StudentID,Grade).  
```  
  
The head is a predicate, and the body is a list of predicates. The target table for this rule to generate facts for is `cn`. This is given by the name of the head predicate. It will generate values using the following rule:  
  
>Add every possible row to the cn table where the first value of the row is defined by the Course column of the csg table and the second value of the row is defined by the Name column of the snap table.   
>  
>Only consider pairs of rows from snap and csg where the StudentID column in each table is the same  
  
The result of interpreting this rule is:  
  
#### snap  
  
 | StudentID | Name       | Address         | PhoneNumber |  
 | --------- | ---------- | --------------- | ----------- |  
 | '12345'   | 'C. Brown' | '12 Apple St.'  | '555-1234'  |  
 | '22222'   | 'P. Patty' | '56 Grape Blvd' | '555-9999'  |  
 | '33333'   | 'Snoopy'   | '12 Apple St.'  | '555-1234'  |  
  
#### csg  
  
 | Course  | StudentID | Grade |  
 | ------- | --------- | ----- |  
 | 'CS101' | '12345'   | 'A'   |  
 | 'CS101' | '22222'   | 'B'   |  
 | 'CS101' | '33333'   | 'C'   |  
 | 'EE200' | '12345'   | 'B+'  |  
 | 'EE200' | '22222'   | 'B'   |  
  
#### cn  
  
 | Course  | Name       |  
 | ------- | ---------- |  
 | 'CS101' | 'C. Brown' |  
 | 'EE200' | 'C. Brown' |  
 | 'CS101' | 'P. Patty' |  
 | 'EE200' | 'P. Patty' |  
 | 'CS101' | 'Snoopy'   |  
  
*Every valid datalog program can contain 0 or more `Rules`.*  
  
### Queries  
---  
`Queries` are used to retrieve information about the relationships that hold true in the current database. A query consists of a predicate. The name of which is the table that is being queried and the list of arguments define parameters.   
  
Each parameter is one of the following:  
It is either a variable or a constant. Constants are surrounded by single quotes and variables are not.   
  
As a useful example lets break down the following code:  
```c++  
Queries:  
  cn('CS101',Name)?  
  ncg('Snoopy',Course,Grade)?  
```  
  
The first query `cn('CS101',Name)?` is looking at the `cn` table. It will return all rows from the table cn where the first item is 'CS101'. In other words this query will return the names of all students who are currently enrolled in the 'CS101' class.  
  
The first query `ncg('Snoopy',Course,Grade)?` is looking at the `ncg` table. It will return all rows from the table `ncg` where the first item is 'Snoopy'. In other words this query will return the Course code and Grade of all classes the student with the name Snoopy is enrolled in.  
  
*Every valid datalog program must contain 1 or more `Queries`.*  
  
  
### Summary  
---  
  
Datalog is a declarative logic programming language that is commonly used in computer science to represent and manipulate data. It uses relation algebra, which is a branch of discrete mathematics, to represent, generate, and evaluate data.  
  
The Datalog programming language represents data in the form of distinct tables or relations. Each relation has a unique name, a header row with column labels, and zero or more rows of data, sometimes called a tuple.  
  
A valid Datalog program must contain one or more `Schemes`, which define the structure or schema of a table. The `Facts` section of the code is optional and comprises zero or more predicates that define individual rows of a table. The name of the predicate defines which of the tables the row belongs to, and each parameter becomes the value of that cell.  
  
`Rules` are also optional and allow the definition of new relations based on existing ones. Each rule has a head, which is a single predicate that defines the schema of a new table, and a body, which is a list of one or more predicates that define the conditions under which the rule's predicate is true.  
  
The `Queries` section of the code is also optional and comprises one or more predicates that define the information that the interpreter should extract from the program's tables. Queries are typically questions about the data in the tables, and they return a list of tuples that satisfy the query's conditions.  
  
A Datalog program contains one or more `Schemes` that define the structure of the tables, optional `Facts` that define the data in the tables, optional `Rules` that define new relations based on existing ones, and optional `Queries` that extract information from the tables.  
  
  
### Conclusion  
---  
I hope you are all excited about the upcoming programming project we have planned! This project is designed to help you solidify the course concepts you have learned so far and will be your first exposure to creating a large program.  
  
You will be working on this project in 5 parts, called projects, which will progressively build on each other. By the end of the project, you will have created a comprehensive program that will showcase your programming skills and creativity.  
  
I want to encourage each and every one of you to put in your best effort and embrace this opportunity to learn and grow as programmers. Remember that mistakes are a natural part of the learning process, so don't be afraid to make them. Stay focused, stay motivated, and most importantly, have fun!  
  
Good luck and happy programming!