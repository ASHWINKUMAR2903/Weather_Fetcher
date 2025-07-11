# Weather_Fetcher
## Date:11.07.25
## Objective:
To demonstrate how to use Promises and async/await in JavaScript by fetching and displaying live weather data from an API. This activity reinforces real-world async data handling in web applications.

## Tasks:

#### 1. Create the HTML Structure:
Add a heading like ```<h1>WeatherNow</h1>```

Create an ```<input>``` for the city name

Add a ```<button>``` to trigger the fetch

Create a <div> to display the weather information

#### 2. Style with CSS:
Center the layout and style input and button

Style the weather output box with borders, padding, and a background color

Add hover effects for the button

#### 3. JavaScript with Promises and Async/Await:
Use fetch() to get weather data from a free API like https://api.weatherapi.com or a mock API

Wrap the fetch in an async function

Use await to wait for the response and parse it as JSON

Use .catch() to handle any errors in the promise

Display the temperature, description, and location in the output div
## HTML Code:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Weather Fetcher</title>
  <link rel="stylesheet" href="style.css" />
  <script src="script.js"></script>
</head>
<body>
  <div class="weather-container">
    <h1>Weather Fetcher</h1>
    <input type="text" id="cityInput" placeholder="Enter city name" />
    <button onclick="getWeather()">Get Weather</button>
    <div id="weatherOutput"></div>
  </div>
</body>
</html>
```
## CSS Code:
```
body {
  font-family: Arial, sans-serif;
  background-color: #f0f8ff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.weather-container {
  background-color: #fff;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  text-align: center;
  width: 300px;
}

h1 {
  color: #333;
}

input {
  padding: 10px;
  width: 100%;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 8px;
}

button {
  padding: 10px 20px;
  background-color: #007acc;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
}

button:hover {
  background-color: #005f99;
}

#weatherOutput {
  margin-top: 20px;
  font-size: 1rem;
  background-color: #e0f7fa;
  padding: 15px;
  border-radius: 10px;
}
```
## JavaScript Code:
```
async function getWeather() {
  const city = document.getElementById("cityInput").value.trim();
  const output = document.getElementById("weatherOutput");

    if (!city) 
    {
        output.innerText = "Enter the city name.";
        return;
    }

  output.innerText = "Fetching weather...";

  let url = `https://api.weatherapi.com/v1/current.json?key=fa2090f83d5e4bd4925164631251107&q=${city}`

  try 
  {
    const response = await fetch(url);

    if (!response.ok) {
      throw new Error("City not found or API limit exceeded.");
    }

    const data = await response.json();

    const location = `${data.location.name}, ${data.location.country}`;
    const temperature = `${data.current.temp_c} °C`;
    const condition = data.current.condition.text;
    const icon = data.current.condition.icon;

    output.innerHTML = 
    `
      <strong>Location:</strong> ${location}<br>
      <strong>Temperature:</strong> ${temperature}<br>
      <strong>Condition:</strong> ${condition}<br>
      <img src="https:${icon}" alt="${condition}" />
    `;
  } 
  catch (error) 
  {
    output.innerText = `Error: ${error.message}`;
    console.error(error);
  }
}
```
## Output:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dd4b9947-8b7a-4f5a-9362-368e2c93db6e" />

## Result:
A mini module that successfully uses Promises and async/await to handle real-time API data, reinforcing asynchronous JavaScript patterns in a practical context.
