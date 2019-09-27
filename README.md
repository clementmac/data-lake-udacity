In this project, we try to help Sparkify, to move their date warehouse to a data lake. Specifically, I built an ETL pipline to extract their data from S3 and processes them using Spark, and load the data into a new S3 as a set of dimensional tables. This will allow their analytics team to easily query what songs their users are listening to.

Dataset
Datasets used in this project are provided in two S3 buckets. One bucket contains information about songs and artists, the second bucket has information regarding actions done by users. The objects contained in both buckets are in JSON file format.

Database Schema
I created a star schema optimized for queries on song play analysis as follows:
you can view the star schema in the Star_Schema.JPG file

TABLES:

Fact Table:

songplays - records in event data associated with song plays i.e. records with page NextSong

Dimension Tables:
users - users in the app
songs - songs in music database
artists - artists in music database
time - timestamps of records in songplays broken down into specific units


Spark Process
The ETL job processes the song files and then the log files. The song files are listed and repeated to insert the relevant data in the artists and the song folders in parquet format. The log files are filtered by the NextSong action. The other dataset is then processed to extract the date, time, year etc. fields and records are then properly entered into the time, users and songplays folders in parquet format for analysis which will be useful for the sparkify data science team.

Project Structure
RUN_ME.ipynb - code to run the etl.py file is in this file
etl.py - The ETL to reads data from S3, processes that data using Spark, and writes them to a new S3
dl.cfg - Configuration file that contains information about AWS credentials
