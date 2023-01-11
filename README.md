
### Project description: 
 - A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.
 - They'd to create a Postgres database with tables designed to optimize queries on song play analysis.
 
--------------------------
### Database design:
# Fact Table: (the tables that has all the foreign keys of the dimension tables)

# songplays:

 - records in log data associated with song plays i.e. records with page NextSong
- with columns:
songplay_id as a primary key and type of serial, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

# Dimension Tables:

# 1)users:
- users in the app
- With columns:
user_id as a primary key and type of bigint, first_name, last_name, gender, level


# 2)songs: 
- songs in music database
- With columns:
song_id as a primary key and type varchar, title, artist_id, year, duration

# 3)artists:
- artists in music database
- With columns:
artist_id as a primary key and type of varchar, name, location, latitude, longitude

# 4)time:
- timestamps of records in songplays broken down into specific units
- With columns:
start_time as a primary key and type of bigint, hour, day, week, month, year, weekday
---------------------------

### ETL Process: 
- In function (def process_song_files):
create the song and artists data I loaded the json file then inserted the required columns in it.
- In function (process_log_files):
locate the log data and converted the timestamp into columns of time table.
Then loaded the data into users table.
Last Insert the data into song_plays table that has all the foregin keys of past tables.
- In function (process_data):
get all the files matching extension from directory.

---------------------------

### Project Repository files: 
- 1)test.ipynb: 
displays the first few rows of each table to check your database.

- 2)create_tables.py: 
drops and creates tables. this file to reset tables before each time to run ETL scripts.

- 3)etl.ipynb:
reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.

- 4)etl.py:
reads and processes files from song_data and log_data and loads them into tables. It's filled based on the ETL notebook.

- 5)sql_queries.py:
contains all your sql queries, and is imported into the last three files above.
-------------------------

### How To Run the Project:
First run python sql_queries.py, then run python create_tables.py to create tables, at least run python etl.py to successfully insert values on the tables.
