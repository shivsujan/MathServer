# Ex.05 Design a Website for Server Side Processing
## Date:04/04/2024

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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
sujan.html
```
<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Surface Area of Right cylinder</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body
{
    background-color: red(159, 223, 255);
}
.edge {
    width: 100%;
    padding-top: 250px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick dashed darksalmon;
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: purple;
}
.formelt {
    color: black;
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h1 {
    color: grey;
    padding-top: 20px;
}
</style>
</head>
<body style="background-color: blue;">
<div class="edge">
    <div class="box">
        <h1>Surface Area of Right cylinder</h1>
        <h3>SHIV SUJAN S R (212223040194)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Radius: <input type="text" name="Radius" value="{{R}}">m<br/>
            </div>
            <div class="formelt">
                Height: <input type="text" name="Height" value="{{H}}">m<br/>
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
</body>
</html>
```
views.py
```
from django.shortcuts import render
def cylarea(request):
    context={}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        r = request.POST.get('Radius','0')
        h = request.POST.get('Height','0')
        print('request=',request)
        print('Radius=',r)
        print('Height=',h)
        area = 2*3.14*int(r) + 2*3.14*int(h)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area=',area)
    return render(request,'mathapp/sujan.html',context)
```
urls.py
```
from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.cylarea,name="surfacearea"),
    path('',views.cylarea,name="surfacearearoot")
]
```
## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2024-04-04 141310.png>)

## HOMEPAGE:
![alt text](<Screenshot 2024-04-04 141223.png>)
## RESULT:
The program for performing server side processing is completed successfully.
