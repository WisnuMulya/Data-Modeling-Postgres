# Data Modeling with Postgres Project #

-------------------------------------------------------------------------------
## Summary ##
This project is a training project in data modeling using Postgres, with  a mock
startup called Sparkify, and utilizing real data from [Million Song Dataset](https://labrosa.ee.columbia.edu/millionsong/)
provided by Udacity, which also provided the skeleton code and structure to this
project.

### Potential Purpose ###
The resulting Postgres relations of this project provides an analytical foundation
for Sparkify to run their analysis on users' behavior regarding songs and artist
that they are listening to.

### Schema ###
The schema of the resulting relations of this project is a snowflake one:
  * Fact Table: `songplays`
  * Dimension Tables:
    * `users`
	* `songs`
	* `artists`
	* `time`
	
This schema provides a denormalized table, `songplays`, in which some OLAP could
be run on efficiently: minimizing the `JOIN` in the queries. Nevertheless, we
could also access more detailed informations provided by the dimension tables,
especially when doing OLTP.

### ETL Pipeline ###
The ETL pipeline in this project extracts JSON files of songs and logs from the
dataset, transforms them into fact and dimension tables, and then loads them into
the Postgres tables.

## Usage ##
  * Requirements:
    * postgres 13.3
	* python 3.9.5
	* jupyter 1.0.0
	* psycopg2 2.8.6
	* pandas 1.2.4
	* ipython-sql 0.4.0
  * Make sure to create a role with the username of `student` and the password of `student`
    in the Postgres daemon connected to your localhost.
  * Run `python create_tables.py` from the CLI and this repository location to initialize
    the database and the tables.
  * Run `python etl.py` from the CLI and this repository location to execute the whole ETL
    process.
  * **NOTE: You will not be able to run `test.ipynb`, `etl.ipynb`, or `etl.py` until you have
    run `create_tables.py` at least once to create the sparkifydb database, which these
	other files connect to.**
  * **NOTE: When running any of the notebook, make sure to click "Restart kernel" to close
    the connection to the database after running it.**

## File Descriptions ##
  * `data` folder contains JSON files of songs and logs to load the Postgres tables.
  * The `*.ipynb` notebooks are used to experiment with the code, data, and the database.
  * `create_tables.py` restarts sparkifydb database, resulting in empty tables.
  * `sql_queries.py` contains all the SQL queries used in the `create_tables.py` and `etl.py`.
  * `etl.py` runs the ETL process from the JSONs in the `data` folder into Postgres relations.

## Contribution ##
If you want to contribute to this project and make it beter, your help is very
welcome.

The following is the general guide on how to contribute to this project:
   1. Fork this project & clone it on your local machine
   2. Create an *upstream* remote and sync your local copy before you branch
   3. Branch for each piece of work
   4. Do the work
   5. Push to your origin repository
   6. Create a new pull request on GitHub

## License ##
The content of this app is coverend under the [MIT License](./license.txt).
