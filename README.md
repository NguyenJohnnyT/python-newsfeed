# python-newsfeed
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
#
## [Deployed Link](https://jtn-python-newsfeed.herokuapp.com)
![Example gif](#)

## Table of Contents
* [Description](#Description)
* [Installation](#Installation)
* [Usage](#Usage)
* [Credits](#Credits)
* [License](#License)

## Description

A blog/reddit-esque Python application that utilizes Flask and a MySQL database that allows users to create posts consisting of a title and an interesting link of choice.  Posts can be upvoted or commented on by other users.

## Installation

Clone the repository onto your local machine.

### Deploying on Heroku:

* Create a new app on Heroku and give it a unique name.
* In the resources tab, install JawsDB MySQL as an add-on
* In the settings tab, scroll down to config vars and reveal them.  A `JAWSDB_URL` environment variable should exist.  It should start with something like `mysql://fpnbvq ...`.  Copy this value.
* Create a new config var called `DB_URL` and paste the value that was copied in the step before.  Add a `+pymysql` after the `mysql` but before the `://fpnbvq` so we end up with something like `mysql+pymysql://fpnbvq ...`and add this variable.
* In your local CLI, connect the project to Heroku using 
```
heroku login
heroku git:remote -a <your-app-name>
```
*  Replace the `<your-app-name>` with the name chosen earlier.
* Commit the changes to Heroku:
```
git add -A
git commit -m "heroku dependencies"
git push heroku main
```
* Visit your application at `https://<your-app-name>.herokuapp.com/` !

### Running on the local machine

* Simply clone the repository into your local machine
* Access the MySQL shell and run `CREATE DATABASE python_news_db`
* With python installed, create a virtual environment and run the following commands at the root folder:
```python
python -m venv venv
.\venv\Scripts\activate #if on windows
. venv/bin/activate #if on macOS
```

* Modify the `.env.EXAMPLE` to include your mysql password and rename it to `.env`
* When inside the virtual environment, run 
```python
pip install flask pymysql python-dotenv sqlalchemy bcrypt cryptography #installs dependencies
```
* Activate flask and create the server (default address is `127.0.0.1:5000`)
```python
python -m flask run #starts the flask server
```
*Optional: Run the following in the virtual environment at the root folder to seed the database
```python
python seeds.py #seed the database
```
