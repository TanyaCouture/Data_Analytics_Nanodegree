# Song Play Analysis for Sparkify

The purpose of this database for Sparkify is to analyze the characteristics of their users and song choices. Sparkify offers a music streaming app, and analyzing song choices as well as characteristics about time of use, the artists and songs chosen, technologies used and the level of service can help Sparkify make decisions about what types of services to offer and to whom.

For the Sparkify database, we are using a star schema. There is a central fact table, the songplay table, and 4 dimensional tables that include users, artists, songs, and time. The relationships between tables are one-to-one relationships. The star schema makes sense because Sparkify is mostly interested in one type of question, what song are users choosing and the characteristics that are related to the song choice. This means there is not a need for more complex or flexible queries and denormalized tables are fine for our directed purposes.

### To run the scripts, open a console in the Project Workspace.

###### Run the following commands:

    1. %run create_tables.py
    2. %run etl.py
    3. %run test.py
    
    If successful, the first 5 SELECT statements will state that 5 rows were affected. The last SELECT statement will state that 1 row was affected.
    
### The following files are contained in this database.

**sql_queries.py:** Contains all the SQL statements to DROP tables if they already exist, CREATE tables, INSERT records into the tables, to SELECT songs by artist_id and song_id, and a python list of the CREATE TABLE statements and another list of DROP TABLE statements.

**create_tables.py:** Contains the functions that execute the SQL statements. The create_database function connects to the sparkifydb, creates the database as well as drops and disconnects at the end. drop_tables executes the DROP table statements, and create_tables executes the CREATE table statements. The final function is the main function that calls the other functions in order.

**etl.py:** The purpose of this file is to process the data from the log and song json files into a form that can be inserted into the Sparkify database. All the methods in this file extract necessary columns and/or attributes from the json files, make the necessary transformations to datatypes, then load the data into the database by executing the INSERT statements made in the sql_queries.py file.

**test.ipynb:** This file tests the connection to sparkifydb. It also runs a SQL SELECT statement for each of the 5 tables to test whether records have been inserted into a database.