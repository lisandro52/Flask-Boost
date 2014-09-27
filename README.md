Flask-Boost
===============

Flask sample project for boosting your development.

###Development Guide

####Init project files

Copy all files inside `proj` folder to your project root path.

Rename folder `proj` to your real project name.

Rename all the `proj` in codes to your real project name.

Copy `config/development_sample.py` to `config/development.py` and update config as needed.

####Install requirements

`cd` to project root path, run:
 
```py
virtualenv venv
. venv/bin/active
pip install -r requirements.txt
bower install
```

####Init database

Create database via console or other GUI/Web tools.

Then init tables:

```py
python manage.py createdb
```

####Livereload support

Install livereload brower extension from [here](http://feedback.livereload.com/knowledgebase/articles/86242-how-do-i-install-and-use-the-browser-extensions-).

Run livereload server in another console:

```py
python manage.py live
```

####Run app

Run local server:

```py
python manage.py run
```

###Production Deploy

####Config server

* [Ubuntu](http://wiki.hustlzp.com/post/ubuntu-server-config)
* [CentOS 6.5](http://wiki.hustlzp.com/post/linux/centos)

####Install requirements

```
git clone ***/proj.git
cd proj
virtualenv venv
. venv/bin/activate
pip install -r requirements.txt
bower install
```

####Config app

Create database first.

Copy `config/production_sample.py` to `config/production.py` and update config as needed.

Then transfer `config/production.py` to server.

####Init database

Create tables:

```py
export MODE=PRODUCTION
cd proj
. venv/bin/activate
python manage.py createdb
```

####Start app

```
cp deploy/nginx.conf /etc/nginx/conf.d/proj.conf
cp deploy/supervisor.conf /etc/supervisord.d/proj.conf
service nginx restart
service supervisord restart
```
