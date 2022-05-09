# **Class 26: Intro to Django**


## **Django at a glance**

Django is a high-level Python web framework for building secure and maintainable websites quickly. Django is a web framework built by experienced developers that takes care of a lot of the legwork so you can focus on developing your app instead of reinventing the wheel. It's free and open source, with a vibrant and active community, excellent documentation, and a variety of free and paid support options.

Because Django was developed in a fast-paced newsroom environment, it was designed to make common Web-development tasks fast and easy. It is a powerful framework that can be used to create dynamic web applications that can be easily updated and maintained.

<br>

## **Creating a project**

You’ll need to auto-generate some code that establishes a Django project – a collection of settings for an instance of Django, including database configuration, Django-specific options and application-specific settings.

by running this command:
```
django-admin startproject <project_name>
```

- manage.py: A command-line utility that lets you interact with this Django project in various ways. 


<br>

## **Creating an App**

```
django-admin startapp <app_name>
```

<br>

## **Design Your Model**

## **Models**
A Model is the sole, authentic source of data information. It includes all of the necessary fields and actions for the data you're keeping. In most cases, each model represents a single database table.

The basics:

- Each model is a Python class that subclasses django.db.models.Model.
- Each attribute of the model represents a database field.
- With all of this, Django gives you an automatically-generated database-access API.

Example:

```
from django.db import models

class Person(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)
```

*first_name* and *last_name* are fields of the model. Each field is specified as a class attribute, and each attribute represents a database column.


<br>

## **Using models**

After defining your models, you need to tell Django you’re going to use those models. 

This is done by editing your settings file *settings.py* and changing the INSTALLED_APPS setting to add the name of the module that contains your models.py, as a string.
```
INSTALLED_APPS = [
    #...
    'myapp',
    #...
]
```
<br>

## **Install it**

Next, run the Django commands to create the database tables automatically:

```
$ python manage.py makemigrations
$ python manage.py migrate
```

- The makemigrations command looks at all your available models and creates migrations for whichever tables don’t already exist. 
- migrate runs the migrations and creates tables in your database, as well as optionally providing much richer schema control.


<br>

## **Templates**


The template language in Django is designed to find a balance between power and simplicity. It's intended for folks who are familiar with HTML, such as designers and front-end developers, to feel at ease and learn quickly. However, it is also adaptable and expandable, allowing developers to customize the template language as needed.