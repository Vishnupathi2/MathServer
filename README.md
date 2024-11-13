# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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

## PROGRAM :
MATHS.HTML :
```
math.html 

<html>
<head>
    <meta charset='utf-8'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <title>Surface Area</title>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <style type="text/css">
        body {
            background-color: rgb(205, 92, 164);
        }
        .edge {
            width: 100%;
            padding-top: 250px;
            text-align: center;
        }
        .box {
            display: inline-block;
            border: thick dashed rgb(246, 255, 192);
            width: 500px;
            min-height: 300px;
            font-size: 20px;
            background-color: rgb(179, 233, 245);
            box-sizing: border-box;
        }
        .formelt {
            color: black;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
        }
        h1 {
            color: black;
            text-align: center;
            padding-top: 20px;
        }
    </style>
</head>
<body>
    <center>
    <div class="edge">
        <div class="box">
        
            <h1>Surface Area of Right Cylinder</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Radius: <input type="text" name="radius" value="{{r}}">m<br/>
                </div>
                <div class="formelt">
                    Height: <input type="text" name="height" value="{{h}}">m<br/>
                </div>
                <div class="formelt">
                    <input type="submit" value="Calculate"><br/>
                </div>
                <div class="formelt">
                    Area: <input type="text" name="area" value="{{area}}">m<sup>2</sup><br/>
                </div>
            </form>
        </div>
    </div>
</center>
</body>
</html>
```
views.py :
```
views.py

from django.shortcuts import render
def surfacearea(request):
    context = {}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        print('request.POST:', request.POST)
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        area = 2 * 3.14 * int(r) * int(h) + 2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('SurfaceArea =', area)
    
    return render(request, 'mathapp/math.html',context)
```
urls.py :
```
urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="surfacearea")
]
```

## SERVER SIDE PROCESSING:
![ooo](https://github.com/user-attachments/assets/2ddc2698-8587-4617-b85d-1beb17f2e483)
## HOMEPAGE:
![oooo](https://github.com/user-attachments/assets/4987701c-11c6-46ee-9927-94146fa3d67e)
## RESULT:
The program for performing server side processing is completed successfully.
