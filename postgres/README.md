# ETL for a Music Streaming App

### 1. Project Description
This project containts a few ETL scripts to create a Postgres database and to load streaming app data into it. 

### 2. Database design
The database contains the following tables:
 - *users*: dimension table containing users information, primary key: user_id
 - *songs*: dimension table containing songs information, primary key: song_id
 - *artists*: dimension table containing artists information, primary key: artist_id
 - *time*: dimension table containing play-action timestamp information, primary key: start_time
 - *songplays*: fact table that stores all the play events signed as "NextSong", primary_key: songplay_id

### 3. ETL Process
The ETL process is composed by 8 sequential steps:
 
 1. Creating the database (sparkifydb) and the database tables, dropping them if they already exist.
 3. Reading the song data from the json files stored in /data/song_data
 4. Parsing the song data to retrieve songs and artists information, storing the information in the *songs* and *artists* tables
 5. Reading the activity log data from the json files stored in /data/log_data
 6. Filtering only activity type "NextSong"
 7. Parsing the log data to retrieve times and users storing the information in the *time* and *users* tables
 8. Creating the *songplays* table by aggregating the parsed log data, song_id (from songs) and artist_id (from artists).

### 4. Project Repository files
    .
    ├── README.md
    ├── create_tables.py
    ├── data
    │   ├── log_data
    │   │   └── 2018
    │   │       └── 11
    │   │           ├── 2018-11-01-events.json
    │   │           ├── ..
    │   └── song_data
    │       └── A
    │           ├── A
    │           │   ├── A
    │           │   │   ├── TRAAAAW128F429D538.json
    │           │   │   ├── ...
    │           └── ...
    ├── etl.ipynb
    ├── etl.py
    ├── sql_queries.py
    └── test.ipynb
### 5. How To Run the Project
1. move to the project folder in your commind line and run "python create_tables.py". This command will set up the database and tables (assuming you have postgres installed and the right user permissions)
2. run "python sql_queries.py". This command will parse the json files and will populate the database tables accordingly. 




