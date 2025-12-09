# Ex.04 Design a Website for Server Side Processing
## Date:09/12/2025

## AIM:
To create a web page to calculate vehicle mileage and fuel efficiency using server-side scripts.

## FORMULA:
M = D / F
<br> M --> Mileage (in km/l)
<br> D --> Distance Travelled (in km)
<br> F --> Fuel Consumed (in l)

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM:
```
math.html

<html>
    <head>
        <title>mileage calculator</title>
        <style>

            body
            {
               background: linear-gradient(rgb(6, 6, 71),rgb(168, 120, 190));
               font-size: 25;
               color: rgb(7, 7, 83);
            }

            .calculate
            {
                text-align: center;
                width:450;
                height:350;
                background: rgb(160, 160, 198);
                position:fixed;
                border:outset 15px rgb(57, 37, 124);
                padding:7px;
                margin-top:300px;
                margin-left:775px;
            }
                        footer
            {
                left:0;
                bottom:0;
                position:fixed;
                background:rgb(6, 6, 71);
                color:rgb(168, 120, 190);
                width:100%;
                text-align: center;
            }

        </style>
    </head>
    <body>
        <div class="calculate">
            <h1>Mileage calculator</h1>
            <h3>Tanushree G (25012099)</h3>
            <form method="POST">

                {% csrf_token %}
                <label>Distance Travelled(in km):</label>
                <input type="number" value="{{D}}" name="distance_travelled">
                <br>

                <label>Fuel Consumed(in l):</label>
                <input type="number" name="fuel_consumed" value="{{f}}">
                <br><br>

                <input type="submit" value="Calculate">
                <br>

                <label>Mileage:</label>
                <input type="number" name="m" value="{{m}}"> km/l

            </form>
        </div>
        <footer>
            Developed by Tanushree G
        </footer>
    </body>
</html>

```
```
views.py

from django.shortcuts import render

def efficiency(request):
    D=int(request.POST.get('distance_travelled',0))
    f=int(request.POST.get('fuel_consumed',0))
    m=D/f if request.method=='POST' else 0
    print("Distance travelled=",D)    
    print("Fuel consumed=",f)
    print("Mileage=",m)
    return render(request,'mathapp/math.html',{'D':D,'f':f,'m':m})


urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns= [path('admin/', admin.site.urls),
path('',views.efficiency,name='efficiency'),]


```


## OUTPUT - SERVER SIDE:
![alt text](<Screenshot (138).png>)

## OUTPUT - WEBPAGE:
![alt text](<Screenshot (140).png>)

## RESULT:
The a web page to calculate vehicle mileage and fuel efficiency using server-side scripts is created successfully.
