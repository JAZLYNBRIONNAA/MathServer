# Ex.03 Design a Website for Server Side Processing
## Date:13.11.2026

## AIM:
To create a web page to calculate Churn Rate using server-side scripts.

## FORMULA:
Churn Rate = (CustLost / InitCust) * 100
<br> InitCust --> Initial Customers Count
<br> CustLost --> Customers Lost Count

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create a HTML file to implement form based input and output.

### Step 5:
Create python programs for views and urls to perform server side processing.

### Step 6:
Receive input values from the form using request.POST.get().

### Step 7:
Calculate the Result using the given formula.

### Step 8:
Display the calculated result in the server console.

### Step 9:
Render the result to the HTML template.

### Step 10:
Publish the website in Localhost.

## PROGRAM:
```
views.py

from django.shortcuts import render

def calculate_churnrate(request):     
        initialcust=int(request.POST.get('initialcust', '0'))
        presentcust=int(request.POST.get('presentcust', '0'))
        churnrate=((initialcust-presentcust)/initialcust)*100 if request.method=='POST' else 0
        print(f"Initial Customers: {initialcust} \n Present Customers: {presentcust} \n churn rate: {churnrate}")
        return render(request, 'myapp3/ex3page.html', {'initialcust':  initialcust, 'presentcust': presentcust, 'churnrate': churnrate})

urls.py

from django.contrib import admin
from django.urls import path
from myapp3 import views

urlpatterns=[
    path('',views.calculate_churnrate, name='calculate_churnrate'),
]

ex3page.html

<html>
    <head>
        <title>form</title>
    </head>
    <body bgcolor="beige">
        <h1 align="center">CHURN RATE CALCULATION</h1>
        <h3 align="center">JAZLYNBRIONNA A<br>26016009</h3>
        <form method="POST">
        {%csrf_token%}
            <br><br><br><label>NUMBER OF INITIAL CUSTOMERS:</label>
            <input type="number" name="initialcust" value={{initialcust}}><br><br>
            <label>NUMBER OF PRESENT CUSTOMERS:</label>
            <input type="number" name="presentcust" value={{presentcust}}><br><br>
            <input type="submit" value="calculate now"><br><br>
            <label>CHURN RATE:</label>
            <input type="number" name="churnrate" value={{churnrate}}>
        </form>           
    </body>
</html>

```

## OUTPUT - SERVER SIDE:

<img width="1920" height="1080" alt="Screenshot (25)" src="https://github.com/user-attachments/assets/c2d6e769-d635-4bb6-b0d6-04585436e495" />

## OUTPUT - WEBPAGE:

<img width="1920" height="1080" alt="Screenshot (24)" src="https://github.com/user-attachments/assets/165affef-de32-46a8-8189-aadaedd6db46" />

## RESULT:
The the web page to calculate Churn Rate using server-side scripts is created successfully.
