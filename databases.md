# [Introduction to Databases](http://class2go.stanford.edu/db/Winter2013)
* [1.0 Intrudtuction](#1.0)
* [2.0 Relational Databases](#2.0)
* [3.0 XML Data](#3.0)
* [4.0 JSON Data](#4.0)
* [5.0 Relational Algebra](#5.0)
* [6.0 SQL](#6.0)

## <a id='1.0'></a>[1.0 Introduction](http://class2go.stanford.edu/db/Winter2013/materials/228)

### [Introduction](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2665/large/01-01-introduction.mp4?Signature=QXD4422zIeYtrPanBTEQGCsa%2BJk%3D&Expires=1675777162&AWSAccessKeyId=AKIAIINO3Q3NXKJA2PXQ&response-content-disposition=attachment)

#### Characteristics of successful DBMS (Database Management System)
* *Massive*: Able to store Terabytes of data
* *Persistent*: Data persists after program closes
* *Safe*: Data stays in consistent state after failures (hardware & software)
* *Multi-User*: manages concurrency
* *Convenience*: makes data access easy; abstracts data structure from structure teh program uses
* *Efficient*: most important feature; must do thousands of queries/second
* *Reliable*: 99.999999% uptime is required

#### What will not be covered
* Frameworks for accessing data such as RubyOnRails and Django
* middleware
* Keep in mind: Data applications may not use DBMS at all; ex:// excel

#### Key concepts
* Data Model - relational (set of records), xml, graph
* Schema vs. Data - Schema:type as Data:variable
* Data definition language (DDL) - Set up schema
* Data manipulation or query language (DML)

#### Key people
* DBMS Implementer
* DBMS designer - establishes schema
* DBMS application developer - writes programs that operate on data
* DBMS administrator - loads data and maintains day to day operation; tunes DBMS

## <a id='2.0'></a>[2.0 Relational Databases](http://class2go.stanford.edu/db/Winter2013/materials/230)
* [2.1 The Relational Model](#2.1)
* [2.2 Querying Relational Databases](#2.2)

### <a id='2.1'></a>[2.1 The Rational Model](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2667/large/02-01-relational-model.mp4?Signature=xJ%2FJ30Rm5z%2BDOznS6Q1dkc8FBBk%3D&Expires=1675777163&AWSAccessKeyId=AKIAIINO3Q3NXKJA2PXQ&response-content-disposition=attachment)
* used by all major DBMS
* simple
* Query with high level languages
* efficient implementations

Database = set of named *relations* (*tables*)
Each relation has named *attributes* (*columns*)
Each *tuple* (*row*) has a value for each attribute
Each attribute has a *type* (*domain*)

*schema*: structural description of relations in database
*instance*: actual data in the database at any one time

*key*: attribute of a relation where ever value is unique in each tuple OR set of attributes whose combined values are unique

#### Creating relations in SQL
    Create table Student(ID, name, GPA, photo)
    Create table College(name string, state char(2), enrollment integer)

### <a id='2.2'></a>[2.2 Querying Relational Databases](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2669/large/02-02-querying-relational-databases.mp4?Signature=22U00tmx83uj1K9NV0zzpB3ZHu0%3D&Expires=1675777163&AWSAccessKeyId=AKIAIINO3Q3NXKJA2PXQ&response-content-disposition=attachment)

#### Steps in creating and using a (relational) database
* Design schema; create using DDL
* "Bulk load" initial data
* Repeat: execute queries and modifications

#### Support for Ad-hoc queries in high-level language
Queries return relations

#### Relational Algebra
* formal language

#### SQL
* actual/implemented
* uses relational algbra

## <a id='3.0'></a>[3.0 XML Data](http://class2go.stanford.edu/db/Winter2013/materials/232)
* [3.1 Well Formed XML](#3.1)
* [3.2 DTDs,IDs and IDREFs](#3.2)
* [3.3 XML Schema](#3.3)

### <a id='3.1'></a>[3.1 Well Formed XML](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2671/large/03-01-well-formed-xml.mp4)
* ?No ordering in relational model?
NOTES NEEDED

### <a id='3.2'></a>[3.2 DTDs, IDs and IDREFs](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2673/large/03-02-dtds-ids-idrefs.mp4)
NOTES NEEDED

### <a id='3.3'></a>[3.3 XML Schema](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2675/large/03-03-xml-schema.mp4)
NOTES NEEDED

## <a id='4.0'></a>[4.0 JSON Data](http://class2go.stanford.edu/db/Winter2013/materials/234)
* [4.1 JSON Introduction](#4.1)
* [4.2 JSON Demo](#4.2)

### <a id='4.1'></a>[4.1 JSON Introduction](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2677/large/04-01-json-intro.mp4)
NOTES NEEDED

### <a id='4.2'></a>[4.1 JSON Demo](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2679/large/04-02-json-demo.mp4)
NOTES NEEDED

## <a id='5.0'></a>[5.0 Relational Algebra](http://class2go.stanford.edu/db/Winter2013/materials/236)

### [Relational Algebra part 1](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2681/large/05-01-relational-algebra-1.mp4)

#### Select Operator
* Returns rows that meet condition set
* denoted by a Sigma
* subscript of the Select condition;
* conditions are joined with logical and ('^')
* Operates on any expression of Relational Algebra

#### Project Operator
* Returns specific columns
* denoted by a Pi
* subscript is the list of columns to retrieve
* columns are separated by comma
* Operates on any expression of Relational Algebra

#### Duplicates
* Automatically eliminated in Relational Algebra

#### Cross-Product (Cartesian)
* Cartesian product of all attributes
* No data is combined
* Data of the same name is prefixed with the Table name i.e. Table1.name, Table2.name

#### Natural Join
* denoted by bowtie
* Cross product, but data of the same name is treated as the same data i.e. data of same column and value is only joined where data is the same
* Abbreviation

#### Theta Join
* denoted by bowtie with subscript theta
* Abbreviation

### [Relational Algebra part 2](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2683/large/05-02-relational-algebra-2.mp4)

#### Union Operator
* denoted by capital U
* Returns all unique values from 2 expressions
* Requires expressions have the same schema
* Operates on any expression of Relational Algebra

#### Difference Operator
* denoted by minus sign
* returns difference of 2 expressions
* Requires expressions have the same schema
* Operates on any expression of Relational Algebra

#### Intersection Operator
* denoted by upside-down Union
* returns values that are listed in 2 expressions
* Requires expressions have the same schema
* E1 <intersect> E2 = E1 - (E1 - E2)
* Operates on any expression of Relational Algebra
* Abbreviation

#### Rename Operator
* denoted by Rho
* Adjusts schema on any expresson of Relational Algebra
* Used to rename instances of data for self-joins
* <Rho>_c1(n1,s1,e1) (Expression)
* Operates on any expression of Relational Algebra

#### Alternate notation

##### Assignment statements
* c1:= <Rho>_c1,s,e1 College
* c2:= <Rho>_c2,s,e2 College

##### Expression Trees
* Similar to operation tree

##### Assignment
Given data

    Person(name, age, gender)       // name is a key
    Frequents(name, pizzeria)       // [name,pizzeria] is a key
    Eats(name, pizza)               // [name,pizza] is a key
    Serves(pizzeria, pizza, price)  // [pizzeria,pizza] is a key

Question 1

    \project_{pizza} (
        (\select_{gender='female' and age>'20'} Person) \join Eats
    )

Question 2

    #2 Find the names of all females who eat at least one pizza served by Straw Hat.
    \project_{name} (
        (\select_{gender='female'} Person) \join (\select_{pizzeria='Straw Hat'})
    )

Question 3

    \project_{pizzeria} (
        \select_{price<10} (
            Serves
        )
        \join (
            \project_{pizza} (
                \select_{(name='Amy' or name='Fay')} Eats
            )
        )
    )

## <a id='6.0'></a>[6.0 SQL](http://class2go.stanford.edu/db/Winter2013/materials/238)
* [6.1 Introduction to SQL](#6.1)
* [6.2 Basic Select Statement](#6.2)
* [6.3 Table Variables and Set Operators](#6.3)
* [6.4 Subqueries in WHERE](#6.4)
* [6.5 Subqueries in WHERE and SELECT](#6.5)
* [6.6 Aggregation](#6.6)
* [6.7 NULL Values](#6.7)
* [6.8 Data Modification Statements](#6.8)
* [6.9 Join Operators](#6.9)

### <a id='6.1'></a>[6.1 Introduction to SQL](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2685/large/06-01-introduction-to-SQL.mp4)
#### Data Definition Language (DDL)
Create table...
Drop table...

#### Data manipulation Language
select, insert, delete, update

#### SELECT statement
* **SELECT**: what to return
* **FROM**: identifies the relations to query over
* **WHERE**: condition filter

### <a id='6.2'></a>[6.2 basic Select Statement](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2687/large/06-02-basic-select-statement.mp4)
#### FROM
* separate relations by a comma

#### WHERE
* joins queried by setting proper attributes equal to each other in the WHERE clause

#### SELECT distinct
* returns only unique values

#### Attribute names that exist in multiple relations in the query
* Define common attribute names by Relation.Attribute

#### ORDER BY
* order by {attribute} ASC/DESC**; //DESC is default

#### LIKE
* single quote string
* % is wildcard

#### AS
* changes label for schema in the queried result

### <a id='6.3'></a>[6.3 Table variables and Set Operators](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2689/large/06-03-table-variables-set-operators.mp4)

#### Table variables
defined in FROM clause used in rest of query

    SELECT S.sID, sname, GPA, A.cname, enrollment
    FROM Student S, College C, Apply A
    WHERE A.sID = S.sID and A.cName = C.cname;

Used to define instances of relations

    SELECT S1.sID, S1.sName, S1.GPA, S2.sID, S2.sName, S2.GPA
    FROM Student S1, Student S2
    WHERE S1.GPA = S2.GPA and S1.sID < S2.sID;

#### Set operators

##### Union
    select cname as name from College
    union 
    select sName as name from Student;

* Eliminates duplicates by default
* **UNION ALL**: keeps the duplicates

##### Intersect
    select sID from Apply where major = 'CS'
    intersect
    select sID from Apply where major = 'EE';

Eliminates duplicates

Can be written as:

    SELECT DISTINCT A1.sID
    FROM Apply A1, Apply A2
    WHERE A1.sID = A2.sID and A1.major = 'CS' and A2.major = 'EE';

##### Except
    SELECT sID FROM Apply WHERE major = 'CS'
    EXCEPT
    SELECT sID FROM Apply WHERE major = 'EE';

Not possible to be rewritten with operators so far available to us

### <a id='6.4'></a>[6.4 Subqueries in WHERE](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2691/large/06-04-subqueries-in-where.mp4)

#### Subqueries
Nested SELECT statements in the WHERE clause encapsulated in parenthesis
    
    SELECT sID, sName
    FROM student
    WHERE sID IN (SELECT sID FROM Apply WHERE major = 'CS');

Cannot be re-written without subquery

##### Except re-written with subqueries
    SELECT sID, sName
    FROM Student
    WHERE sID in (SELECT sID from Apply WHERE major = 'CS')
      and sID not in (SELECT sID FROM Apply WHERE major = 'EE');

##### EXISTS
    SELECT cname, state
    FROM College C1
    WHERE exists (Select * from College C2 where C2.state = C1.state and C1.cName <> c2.cName);

* Checks for existance of data instead of returning values

##### ALL
    SELECT sName
    FROM Student
    WHERE GPA >= all (SELECT GPA FROM Student);

* Returns name of students with MAX GPA

##### ANY
    SELECT cName
    FROM College S1
    WHERE not enrollment <= any (select enrollment from College S2 where S2.cname <> S1.cName);

* returns largest enrollment

### <a id='6.5'></a>[6.5 Subqueries in WHERE and SELECT](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2693/large/06-05-subqueries-in-from-select.mp4)

#### Subquery in FROM
    select *
    from
        (select sID, sName, GPA, GPA*(sizeHS/1000.0) as scaledGPA
        from Student) G
    where abs(G.scaledGPA -GPA > 1.0);

* Can be assigned names to be referred to later

#### Subquery in SELECT
    select cName, state,
        (select distinct GPA
        from Apply, Student
        where College.cname = Apply.cName
            and Apply.sID = Student.SID
            and GPA >= all
                (select GPA from Student, Apply
                where Student.SID = Apply.sID
                and Apply.cName = College.cname)) as GPA
    from College;

* Returns the College Name, State and highest GPA
* Important to ensure that only one value is returned from the nested select

#### as
* used to assign labels to values i.e. variable names

#### abs()
* returns absolute value of parameter

### <a id='6.6'></a>[6.6 Aggregation](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2695/large/06-06-aggregation.mp4)

#### Aggregation functions
##### min
    select min(GPA)
    from Student, Apply
    where Student.sID = Apply.sID and major='cs';
* returns lowest value of data returned

##### max
select avg(GPA)
    from Student
    where sID in (select sID = Apply and major='cs');
##### sum

##### avg
    select avg(GPA)
    from Student
    where sID in (select sID = Apply and major='cs');
* returns average value of data returned

##### count
    select count(distinct sID)
    from Apply
    where cname='Cornell';
* returns the number of distinct applications to College
* returns the number of tuples in result

#### New Clauses
##### Group by columns
##### Having






### <a id='6.7'></a>[6.7 NULL Values](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2697/large/06-07-null-values.mp4)
### <a id='6.8'></a>[6.8 Data Modification Statements](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2699/large/06-08-data-modification-statements.mp4)
### <a id='6.9'></a>[6.9 Join Operators](https://prod-c2g.s3.amazonaws.com/db/Winter2013/videos/2701/large/06-055-join-operators.mp4)

### Homework 2

#### Question 1:
##### Find the names of all students who are friends with someone named Gabriel. 

    select distinct Friend.ID1
    from Highschooler, Friend
    where Friend.ID1 in (
            select ID
            from Highschooler
            where name='Gabriel'
        )
