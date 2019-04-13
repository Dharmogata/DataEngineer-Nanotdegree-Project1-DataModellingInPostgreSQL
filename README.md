Data Modeling with PostgresSQL
==========================================
## Table of contents
1.Goal
2.Setup
3.File Description
4.Schema for Song Play Analysis
5.Instructions

## Goal
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

In this project, you'll apply what you've learned on data modeling with Postgres and build an ETL pipeline using Python. To complete the project, you will need to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

## Setup
In my case, I have run the steps below in own machine (ubuntu)
For local install, perform the following steps before running the code:

- Install PostgreSQL ($sudo apt update
$sudo apt install postgresql postgresql-contrib).
- Create "studentdb" (createdb 'studentdb').
- Add "student" user with password "student" and grant createdb role.
- Test login (psql -U student -d studentdb -W)

## File Description

- create_tables.py: helper functions script for dropping and creating tables 

- sql_queries.py: helper functions to drop/create tables, insert/query tables.

- etl.ipynb: jupyter notebook for building the initial ETL code.

- etl.py: actual ETL code for working with the data.

- test.ipynb: notebook for running test queries against the loaded database.

- data: Song dateset->The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset. Log dataset ->The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate app activity logs from a music streaming app based on specified configurations.

## Schema for Song Play Analysis


Using the song and log datasets, you'll need to create a star schema optimized for queries on song play analysis. This includes the following tables.

Fact Table
1.songplays - records in log data associated with song plays i.e. records with page NextSong
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
Dimension Tables
2.users - users in the app
user_id, first_name, last_name, gender, level
3.songs - songs in music database
song_id, title, artist_id, year, duration
4.artists - artists in music database
artist_id, name, location, lattitude, longitude
5.time - timestamps of records in songplays broken down into specific units
start_time, hour, day, week, month, year, weekday

## Instructions


- python create_tables.py: helper functions to drop any existing tables and create them
- python etl.py: helper functions to load and process all the log files
- jupyter notebook test.ipynb:  notebook which is checking the data is loaded properly in the database

Remember to run create_tables.py before running the cell in the ETL pipeline to ensure you've created/resetted the time,songs, artist, users,and songplays table in the sparkify database.