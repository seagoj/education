# 1.Introduction
## Characteristics of successful DBMS (Database Management System)
* *Massive*: Able to store Terabytes of data
* *Persistent*: Data persists after program closes
* *Safe*: Data stays in consistent state after failures (hardware & software)
* *Multi-User*: manages concurrency
* *Convenience*: makes data access easy; abstracts data structure from structure teh program uses
* *Efficient*: most important feature; must do thousands of queries/second
* *Reliable*: 99.999999% uptime is required

## What will not be covered
* Frameworks for accessing data such as RubyOnRails and Django
* middleware
* Keep in mind: Data applications may not use DBMS at all; ex:// excel

## Key concepts
* Data Model - relational (set of records), xml, graph
* Schema vs. Data - Schema:type as Data:variable
* Data definition language (DDL) - Set up schema
* Data manipulation or query language (DML)

## Key people
* DBMS Implementer
* DBMS designer - establishes schema
* DBMS application developer - writes programs that operate on data
* DBMS administrator - loads data and maintains day to day operation; tunes DBMS
