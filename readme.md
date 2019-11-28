#Microblog tut
https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world

#Hello World!
## virtual environment

create:
`$ python3 -m venv venv` - second venv is the name of the virtual environment

activate:
`$ source venv/bin/activate`

Some git stuff:
from in venv?
`$ git init` - initalize folder as git repo
`$ git add -A` - add all files
Push local code to github (new repo):
Create a new repo with github webinterface (no license, readme, etc)

HTTPS:(can do with ssh too)
`git remote add origin https://github.com/jersear/microblog.git`
`git push -u origin master`


## install flask
`pip install flask`

## Hello world - 1st flask app
`$ mkdir app`

create `__init__.py` in app/

create `app/routes.py`

create top-level script to define the flask application instance:
create: `/microblog.py`

instead of manually setting the `FLASK_APP` environment variable with `export`
let us creat a dotenv so setting this var is auto:

`(venv) $ pip install python-dotenv`

the create `\.flaskenv` with `FLASK_APP=microblog.py` inside it.

Run it:
`(venv) $ flask run`

#Templates

`(venv) $ mkdir /app/templates`
Put yer template in there. Render it from `routes.py`

Conditional statements in flask with jinja2, inside {% ... %} blocks.

Loops in templates, cycle through vars passed on from routes.py:
{% if title %}
html stuff
{% else %}
html stuff otherwise
{% end if %}

## template inheritance
in `index.html` use `{% extends "base.html" %}`  with `{% block content %}` / `{% endblock %}`

in `base.html` use `{% block content %}{% endblock %}` for where the stuff from index.html will go.

#Web Forms

Flask-WTF extension for forms
`(venv) $ pip flask-wtf`

## configuration
time to mind flask configuration (different than environment configuration)

We could put config stuff in __init__.py. Better to make a config.py file.

create a `config.py` file, then pull config setting into `__init__.py`

SECRET_KEY (WTF uses to prevent against CSRF attacks)

## user login forms

create `app/forms.py`

## form template

create `app/templates/login.html`

## form views

add a route to login.html in `routes.py`

## Recieving Form Data

in `app/routes.py`

`flash` functionality is introduced and incorperated into the `base.html` template

## Improving Field Validation

Modify `login.html` to add field validation


#Database

`(venv) $ pip install flask-sqlalchemy`

*note* this tut uses flask-migrate. Other tuts dont. Maybe good to stick with a migration manager?

`(venv) $ pip install flask-migrate`

## falsk-SQLalchemy config:
*using sqlite*

edit `config.py` SQLALCHEMY_DATABASE_URI

In `app/__init__.py` create objects for database and migration engine (db and migrate)

## database models

create `app/models.py` put yer db model in there. 

## create the migration repository

`(venv) $ flask db` sub command is added by flask-migrate to manage db migrations.

Create the migration repo with `(venv) $ flask db init`

## 1st database migration

`(venv) $ flask db migrate -m "users table"`
$ .. - m "blah blah" is a comment on this migration
This does not change the db, only creates the migration script. 


`flask db upgrade` - applys changes to the db. 

## Database relationships
created a post table in `app/models.py`


#User Logins

#Profile page and avatars

#Error Handling

#Followers

#Pagination

#Email Support

#FaceLift

#Dates and TImes

#I18n and L10n

#Ajax

#A better application Sturcture

#Full text search

#Deployment - skipped for now

#Some javascript magic

#User Notification

#Background jobs

#api

