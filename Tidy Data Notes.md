---
output: word_document
---
#**BIOSTATSTICS**

##**Why tidy data?**
###_**The tidy data concept:**_
* provides a standardized layout/organization for data values.

##_**Standardized aids:**_
* data exploration and analysis
* data sharing
* the develoopment of data cleaning and analysis tools

##**Core principles of tidy data**
###_**The language of datasets:**_
* datasets consist of *values* (usually numbers or strings)
* every _value_ belongs to a _variable_ and an _observation_

###_**Structure of a tidy dataset:**_
* _variables_ are arranged in _columns_
* _observations_ are arranged in _rows_
* each type of observational unit forms a table

##**Common causes of messiness**
* column headers are values, not variable names
* multiple variables are stored in one column
* variables are stored in both rows and columns
* multiple types of experimental unit stored in the same table
* on type of experimental unit stored in multiple tables

###_**Single document type is stored in multiple tables:**_
Data values about a single type of observational unit mau be spread out over multiple tables or files.  These tables and files are often split up by another variable (e.g., each table represents a singles year, person, or location).  As long as the format for individual records is consistent, this is an easy problem to fix by merging tables.

##**Tools to tidy and manipulate data**
###_**The _grammar_ of data cleaning**_
Primary _tidyr_ package verbs:
* gather(): gathers multiple columns into key-value pair
* spread(): spreads 2 columns (key-value pair) in to multiple columns

##**Tools to tidy and manipulate data**
###_**The grammar of manipulating data**_
* Primary _dplyr_ package verbs:
  + select(): focus on a subset of variables (columns). This function has the inherent ability to arrange columns in any order I please.
  + filter(): focus on a subset of rows
  + mutate():add new columns
  + summarize(): produce summary statistics of variables. This function is most powerful when applied to **grouped data**. The main idea behind grouping data is that I want to break up my dataset into groups of rows based on the values of one or more variables. The *group_by()* function is responsible for doing this. 
  + arrange(): re-order rows



