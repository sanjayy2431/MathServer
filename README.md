# Ex.05 Design a Website for Server Side Processing

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
```
math.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lamp Filament Power Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        h1 {
            color: #4CAF50;
            text-align: center;
        }

        form {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
            max-width: 300px;
            width: 100%;
            text-align: left;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }

        input[type="number"] {
            width: calc(100% - 20px);
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 16px;
        }

        button {
            width: 100%;
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        h2 {
            text-align: center;
            color: #333;
        }

        p#result {
            font-size: 18px;
            text-align: center;
            color: #555;
     <script>
        function calculatePower(event) {
            event.preventDefault(); 
            let intensity = parseFloat(document.getElementById('intensity').value);
            let resistance = parseFloat(document.getElementById('resistance').value);
            let power = Math.pow(intensity, 2) * resistance;
            document.getElementById('result').textContent = `Power: ${power.toFixed(2)} watts`;
        }
    </script>
</head>
<body>
    <div>
        <h1>Lamp Filament Power Calculator</h1>
        <h2>MOHAMED RASHITH S 24001082</h2>
        <form id="powerForm" onsubmit="calculatePower(event)">
            <label for="intensity">Intensity (I in Amps):</label>
            <input type="number" id="intensity" name="intensity" step="any" required>

            <label for="resistance">Resistance (R in Ohms):</label>
            <input type="number" id="resistance" name="resistance" step="any" required>

            <button type="submit">Calculate Power</button>
        </form>

        <h2>Result:</h2>
        <p id="result">Please enter values and calculate power.</p>
    </div>
</body>
</html>           margin-top: 10px;
        }
    </style>


```
```
views.py
from django.shortcuts import render
def power_calculation(request):
    context = {
        'power': "0",
        'intensity': "0",
        'resistance': "0"
    }
    
    if request.method == 'POST':
        print("POST method is used")
        intensity = request.POST.get('intensity', '0')
        resistance = request.POST.get('resistance', '0')
        print('Intensity =', intensity)
        print('Resistance =', resistance)
        
        # Calculate power using the formula P = I^2 * R
        try:
            power = (float(intensity) ** 2) * float(resistance)
            context['power'] = f"{power:.2f}"
            context['intensity'] = intensity
            context['resistance'] = resistance
            print('Power =', power)
        except ValueError:
            context['error'] = "Invalid input. Please enter numerical values for both intensity and resistance."

    return render(request, 'yuviapp/math.html', context)
```
```
urls.py
from django.contrib import admin
from django.urls import path
from yuviapp import views  # Adjust 'yuviapp' to your app name

urlpatterns = [
    path('admin/', admin.site.urls),
    path('power-calculation/', views.power_calculation, name='power_calculation'),
    path('', views.power_calculation, name='home'),  # Set as the homepage
]
```
## SERVER SIDE PROCESSING:
![image](https://github.com/user-attachments/assets/af0eb6c9-9d2e-47eb-ba90-bac473fe7cd6)


## HOMEPAGE:

![WhatsApp Image 2024-11-04 at 15 54 56_b6606a89](https://github.com/user-attachments/assets/6b9ca910-e280-4f65-a0f1-0fc43c4ab296)



## RESULT:
The program for performing server side processing is completed successfully.
