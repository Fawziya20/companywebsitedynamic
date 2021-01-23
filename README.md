# Dynamic Website Design for a Manufacturing Company
## AIM:
To design a dynamic website for a chip manufacturing company.

## DESIGN STEPS:
### Step 1: 
Requirement collection.
### Step 2:
Creating the layout using HTML and CSS.
### Step 3:
Updating the sample content.
### Step 4:
Choose the appropriate style and color scheme.
### Step 5:
Validate the layout in various browsers.
### Step 6:
Validate the HTML code.
### Step 6:
Publish the website in the given URL.

## PROGRAM:

### base.html

```
{% load static %}
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Cisco Private Limited</title>
    <link rel="stylesheet" href="{% static 'css/layout.css' %}">
    <link rel = "icon" href ="{% static 'img/titleicon.png' %}" type = "image/x-icon"> 
              
</head>

<body>
    <div class="container">
    <div class="banner">
    Cisco Private Limited.
    </div>
    <div class="menu">
        <div class="menuitem"><a href="/home">Home</a></div> 
        <div class="menuitem"><a href="/products">Products</a></div> 
        <div class="menuitem"><a href="/people">People</a></div>
        <div class="menuitem"><a href="/contactus">Contact us</a></div>
    </div><div class="content">
    {% block content %}    
    {% endblock  %}
    </div>
    <div class="footer">
        Copyright © 2020 Cisco Private Limited, Developed by A.Fawziya.
    </div>
    </div>
</body>

</html>
```

### home.html

```
{% extends "website/base.html" %}

{% block content %}
    <div class="homecontent">    
   <h1><u>About Us</u></h1>
    <img src="/static/img/building.jpg" alt="Building">
    <div class="contenttext">
    Cisco Pvt Ltd, provides a broad range of semiconductor and infrastructure software applications that serve the data center, networking, software, broadband, wireless, and storage and industrial markets. Common applications for its products include: data center networking, home connectivity, broadband access, telecommunications equipment, smartphones, base stations, data center servers and storage, factory automation, power generation and alternative energy systems, displays, and mainframe operations and management, and application software development. Some of Silicon's core technologies and products include:
    <ul>
        <li>Memory Chips</li>
        <li>SATA HDD</li>
        <li>SATA SSD </li>
        <li>Broadband Modems</li>
        <li>Wifi Devices</li>
        <li>Switching Devices</li>
        <li>Optical Sensors</li>
    </ul> 
    </div>
    </div>
{% endblock  %}
```

### products.html

```
{% extends "website/base.html" %}

{% block content %}
<div class="productcontent">
    <h1>Our Premium Products</h1>
    <div class="productitems">
        {% for products in productss %}
        <div class="productitem">
            <div class="itemimage">
                <img src="{{ products.photo.url }}" alt="product image" height="200" width="200">
            </div>
            <div class="productsname">{{ products.name }}</div>
            <div class="productsprice">Rs:{{ products.price }}</div>
        </div>
        {% endfor %}
    </div>
</div>
{% endblock  %}
```

### people.html

```
{% extends "website/base.html" %}

{% block content %}
    <div class="peoplecontent">
        <h1>Chief Officer's</h1>
    </div>
    <div class="peoplelists">
        {% for people in peoples %}
        <div class="peoplelist">
            <div class="peopleimage">
                <img src="{{ people.photo.url }}" alt="peopleimage" width="180" height="250">
            </div>
            <div class="peoplename"><h2>{{ people.name }}</h2></div>
            <div class="peoplepost"><h3>({{ people.designation }})</h3></div>
        </div>
        {% endfor %}
    </div>
{% endblock  %}
```

### contactus.html

```
{% extends "website/base.html" %}

{% block content %}
    <h1 class="contactcenter">
        CONTACT
    </h1>
    <h2 class="contactcenter">
    CONTACT ADDRESS: 85 Cowcross St, Farringdon, London EC1M 6PF, United Kingdom<br>
      
    EMAIL ID:ciscocorp@gmail.com<br>
            
       CONTACT NO:9865477236
    </h2>
{% endblock  %}
```

### admin.py

```
from django.contrib import admin
from .models import people,peopleAdmin
from .models import products,productsAdmin


# Register your models here.

admin.site.register(people,peopleAdmin)

admin.site.register(products,productsAdmin)
```
### models.py

```
from django.db import models
from django.contrib import admin
# Create your models here.
class people(models.Model):
    name = models.CharField(max_length=100)
    designation = models.CharField(max_length=100)
    photo = models.ImageField(upload_to='photos/', blank=True)

class peopleAdmin(admin.ModelAdmin):
    list_display = ('name', 'designation', 'photo')

class products(models.Model):
    name = models.CharField(max_length=100)
    price = models.IntegerField()
    photo = models.ImageField(upload_to='photos/', blank=True)
class productsAdmin(admin.ModelAdmin):
    list_display = ('name', 'price', 'photo')
```

## OUTPUT:

![output](./static/img/home.png)

![output](./static/img/product.png)

![output](./static/img/people.png)

![output](./static/img/contactus.png)

## Admin page:

![output](./static/img/productadmin.png)

![output](./static/img/peopleadmin.png)


## CODE VALIDATION REPORT:

![output](./static/img/homevalid.png)

![output](./static/img/productvalid.png)

![output](./static/img/peoplevalid.png )

![output](./static/img/contactusvalid.png)

## RESULT:
Thus a website is designed for the chip manufacturing company and is hosted in the URL http://fawziya.student.saveetha.in:8000/. HTML code is validated.