# **Readings: Django CRUD and Forms**

## **Django: Working with forms**

An **HTML Form** is a collection of one or more fields on a web page that can be used to collect data from users and send it to a server. These fields are,  text boxes, checkboxes, radio buttons, date pickers, and others. Forms are a flexible technique for gathering user input, and they're also a safe way to share data with the server because they allow us to transmit data through POST requests.

It's not easy to work with forms! Developers must write HTML for the form, validate and sanitize entered data on the server, repost the form with error messages to notify users of any invalid fields, handle the data once it has been successfully submitted, and finally respond to the user in some way to indicate success. 

But the cool thing about Django Forms is that they automates many of these steps by offering a framework that allows you to programmatically build forms and their fields, then utilize these objects to generate form HTML code and handle most of the validation and user interaction.

<br>

### **HTML Forms**

The form is defined in HTML as a collection of elements inside ```<form>...</form>``` tags, containing at least one input element of ```type="submit"```.

for example:
```
<form action="/team_name_url/" method="post">
    <label for="team_name">Enter name: </label>
    <input id="team_name" type="text" name="name_field" value="Default name for team.">
    <input type="submit" value="OK">
</form>
```

The form has a number of other input elements and their associated labels. The field's type attribute defines what sort of widget will be displayed. 
- The name and id of the field are used to identify the field in JavaScript/CSS/HTML.
- The value defines the initial value for the field when it is first displayed. 
- The matching team label is specified using the label.
- The submit input will be displayed as a button by default. This can be pressed to upload the data in all the other input elements in the form to the server.

- The form attributes define the HTTP method used to send the data and the destination of the data on the server (action):

    - action: The resource/URL where data is to be sent for processing when the form is submitted. If this is not set, then the form will be submitted back to the current page URL.
    - method: The HTTP method used to send the data: post or get.
        - The POST method should always be used if the data is going to result in a change to the server's database.
        - The GET method should only be used for forms that don't change user data. It is recommended for when you want to be able to bookmark or share the URL.

<br>

## **Django Form Handling Process**

Django's form handling employs the approach of: the view receives a request, Django does any necessary actions (including reading data from the models), and finally builds and delivers an HTML page (from a template, into which we pass a context containing the data to be displayed). What complicates things further is that the server must be able to process data provided by the user and redisplay the page if any problems occur.


A process flowchart of how Django handles form requests:

![Django Form Handling](imgs/django-form-handling.png)

And to explain more, the main things that Django's form handling does are:

1. Display the default form the first time it is requested by the user.
    - The form may contain blank fields if you're creating a new record, or it may be pre-populated with initial values.
    - The form is referred to as unbound at this point, because it isn't associated with any user-entered data.
2. Receive data from a submit request and bind it to the form.
    - Binding data to the form means that the user-entered data and any errors are available when we need to redisplay the form.
3. Clean and validate the data.
    - Cleaning the data performs sanitization of the input fields, such as removing invalid characters that might be used to send malicious content to the server, and converts them into consistent Python types.
    - Validation checks that the values are appropriate for the field.
4. If any data is invalid, re-display the form, this time with any user populated values and error messages for the problem fields.
5. If all data is valid, perform required actions (such as save the data, send an email, return the result of a search, upload a file, and so on).
6. Once all actions are complete, redirect the user to another page.

<br>

## **Form and Function View**

### **Form**

The Form class is the heart of Django's form handling system. It specifies the fields in the form, their layout, display widgets, labels, initial values, valid values, and (once validated) the error messages associated with invalid fields. The class also provides methods for rendering itself in templates using predefined formats (tables, lists, etc.) or for getting the value of any element (enabling fine-grained manual rendering).

<br>

### **Declaring a Form**
```
from django import forms

class RenewBookForm(forms.Form):
    renewal_date = forms.DateField(help_text="Enter a date between now and 4 weeks (default 3).")
```

<br>

### **Form Fields**

- BooleanField
- CharField
- ChoiceField
- TypedChoiceField
- DateField
- DateTimeField
- DecimalField
- DurationField
- EmailField
- FileField
- FilePathField
- FloatField
- ImageField
- IntegerField
- GenericIPAddressField
- MultipleChoiceField
- TypedMultipleChoiceField
- NullBooleanField
- RegexField
- SlugField
- TimeField
- URLField
- UUIDField
- ComboField
- MultiValueField
- SplitDateTimeField
- ModelMultipleChoiceField
- ModelChoiceField.

<br>

### **Validation**

Update the forms.py file so it looks like this:

```
import datetime

from django import forms

from django.core.exceptions import ValidationError
from django.utils.translation import gettext_lazy as _

class RenewBookForm(forms.Form):
    renewal_date = forms.DateField(help_text="Enter a date between now and 4 weeks (default 3).")

    def clean_renewal_date(self):
        data = self.cleaned_data['renewal_date']

        # Check if a date is not in the past.
        if data < datetime.date.today():
            raise ValidationError(_('Invalid date - renewal in past'))

        # Check if a date is in the allowed range (+4 weeks from today).
        if data > datetime.date.today() + datetime.timedelta(weeks=4):
            raise ValidationError(_('Invalid date - renewal more than 4 weeks ahead'))

        # Remember to always return the cleaned data.
        return data
```

<br>

### **URL configuration**

```
urlpatterns += [
    path('book/<uuid:pk>/renew/', views.renew_book_librarian, name='renew-book-librarian'),
]
```
<br>

### **View**

Here we use the POST request approach:

```
import datetime

from django.shortcuts import render, get_object_or_404
from django.http import HttpResponseRedirect
from django.urls import reverse

from catalog.forms import RenewBookForm

def renew_book_librarian(request, pk):
    book_instance = get_object_or_404(BookInstance, pk=pk)

    # If this is a POST request then process the Form data
    if request.method == 'POST':

        # Create a form instance and populate it with data from the request (binding):
        form = RenewBookForm(request.POST)

        # Check if the form is valid:
        if form.is_valid():
            # process the data in form.cleaned_data as required (here we just write it to the model due_back field)
            book_instance.due_back = form.cleaned_data['renewal_date']
            book_instance.save()

            # redirect to a new URL:
            return HttpResponseRedirect(reverse('all-borrowed') )

    # If this is a GET (or any other method) create the default form.
    else:
        proposed_renewal_date = datetime.date.today() + datetime.timedelta(weeks=3)
        form = RenewBookForm(initial={'renewal_date': proposed_renewal_date})

    context = {
        'form': form,
        'book_instance': book_instance,
    }

    return render(request, 'catalog/book_renew_librarian.html', context)
```