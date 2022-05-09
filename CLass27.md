# **Class 27: Django Models**

## **Model definition**

Models are usually defined in an application's *models.py* file. They are implemented as subclasses of django.db.models.Model, and can include fields, methods and metadata. Here's an example:
```
from django.db import models


class Person(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)
    age = models.IntegerField()
    bio = models.TextField()
    photo = models.ImageField(upload_to='clients_photos')
    is_active = models.BooleanField(default=True)

    def __str__(self):
        return self.my_field_name
```

### **Fields** 
A model can have any number of fields of any type, each of which represents a column of data to be stored in one of our database tables.


The field types are:

    - CharField: Stores a string of up to a certain length.
    - IntegerField Stores an integer.
    - TextField Stores a string of unlimited length.
    - ImageField: Stores an image file.
    - BooleanField: Stores a boolean value.
    - DateField: Stores a date.
    - DateTimeField: Stores a date and time.
    - TimeField: Stores a time.


<br>

### **Methods**

Minimally, in every model you should define the standard Python class method __str__() to return a human-readable string for each object. This string is used to represent individual records in the administration site. Often this will return a title or name field from the model.
```
def __str__(self):
    return self.field_name
```


    
<br>

## **Registering models**

Before you can use the models in your application, you need to register them with Django. This is done by opening *admin.py*.
 
It would look like this before registering your models:
```
from django.contrib import admin

# Register your models here.
```
After registering your models, you can use them in your application.
Whereas you have to import the models and then calls admin.site.register to register each of them.
```
from .models import Author, Genre, Book, BookInstance

admin.site.register(Book)
admin.site.register(Author)
admin.site.register(Genre)
admin.site.register(BookInstance)
```

<br>

## **Creating a superuser**

We'll need a user account to access the admin site. This user must also have permissions to control all of our objects in order to see and create data. Using *manage.py*, you can establish a "superuser" account with complete access to the site and all necessary permissions.

This is done by running the following command:
```
    python manage.py createsuperuser
```
You'll then be prompted to enter a username, email address, and strong password.


Once this command completes a new superuser will have been added to the database. Now you can log in to the site and access the administration site, by running the following command to run the server:
```
    python manage.py runserver
```

## **Logging in and using the site**

To login to the site, open the /admin URL (e.g. http://127.0.0.1:8000/admin) and enter your new superuser username and password credentials 

you'll then be redirected to the login page, and then back to the /admin URL after you've entered your details