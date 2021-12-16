<b>Introduction</b>

A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

Task is to build an ETL Pipeline that extracts their data from S3, staging it in Redshift and then transforming data into a set of Dimensional and Fact Tables for their Analytics Team to continue finding Insights to what songs their users are listening to.

<b>Project Description</b>

Application of Data warehouse and AWS to build an ETL Pipeline for a database hosted on Redshift Will need to load data from S3 to staging tables on Redshift and execute SQL Statements that create fact and dimension tables from these staging tables to create analytics

<b>Project Datasets</b>

Song Data Path     -->     s3://udacity-dend/song_data
Log Data Path      -->     s3://udacity-dend/log_data
Log Data JSON Path -->     s3://udacity-dend/log_json_path.json

<b>Song Dataset</b>

The first dataset is a subset of real data from the Million Song Dataset(https://labrosa.ee.columbia.edu/millionsong/). Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. 
For example:

song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json



<b>Log Dataset</b>

The second dataset consists of log files in JSON format. The log files in the dataset with are partitioned by year and month.
For example:

log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json


<b>Schema for Song Play Analysis</b>

A Star Schema would be required for optimized queries on song play queries

<b>Fact Table</b>

<b>songplays</b> - records in event data associated with song plays i.e. records with page NextSong
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

<b>Dimension Tables</b>

<b>users</b> - users in the app
user_id, first_name, last_name, gender, level

<b>songs</b> - songs in music database
song_id, title, artist_id, year, duration

<b>artists</b> - artists in music database
artist_id, name, location, lattitude, longitude

<b>time</b> - timestamps of records in songplays broken down into specific units
start_time, hour, day, week, month, year, weekday

<b>Project Template</b>

Project Template include four files:

<b>1. create_table.py</b> is where I create fact and dimension tables for the star schema in Redshift.

<b>2. etl.py</b> is where I load data from S3 into staging tables on Redshift and then process that data into  analytics tables on Redshift.

<b>3. sql_queries.py</b> is where I define SQL statements, which will be imported into the two other files above.



<b>Steps</b>

1. Write  SQL CREATE statement for each of these tables in sql_queries.py
2. Complete the logic in create_tables.py to connect to the database and create these tables
3. Write SQL DROP statements to drop tables in the beginning of create_tables.py if the tables already exist. 
4. Launch a redshift cluster and create an IAM role that has read access to S3.
5. Add redshift database and IAM role info to dwh.cfg.
6. Test by running create_tables.py and checking the table schemas in redshift database.

<b>Build ETL Pipeline</b>

1. Implement the logic in etl.py to load data from S3 to staging tables on Redshift.
2. Implement the logic in etl.py to load data from staging tables to analytics tables on Redshift.
3. Test by running etl.py after running create_tables.py and running the analytic queries on Redshift database to compare results with the expected results.



