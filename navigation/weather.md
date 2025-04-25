---
layout: page
title: Weather
search_exclude: true
permalink: /weather/
---

<h1>7-Day Weather Forecast</h1>

<!-- Search input section -->
<div id="search-container">
    <input type="text" id="city-input" placeholder="Enter city" />
    <button onclick="getWeather(document.getElementById('city-input').value)">Get Weather</button>
</div>

<!-- Container to display weather data -->
<div id="weather-container" class="weather-container"></div>
<div id="error-message" class="error"></div>

<style>
    /* Basic styling for the weather display */
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        background-color: #f4f4f9;
        text-align: center;
    }

    h1 {
        background-color: #4CAF50;
        color: white;
        padding: 20px;
        margin: 0;
    }

    #search-container {
        margin-top: 20px;
    }

    input[type="text"] {
        padding: 10px;
        width: 300px;
        font-size: 16px;
        border-radius: 5px;
        border: 1px solid #ddd;
        margin-right: 10px;
    }

    button {
        padding: 10px 20px;
        background-color: #4CAF50;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        font-size: 16px;
    }

    button:hover {
        background-color: #45a049;
    }

    .weather-container {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        margin-top: 20px;
    }

    .weather-card {
        background-color: white;
        margin: 10px;
        padding: 15px;
        border-radius: 10px;
        width: 200px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        text-align: center;
    }

    .weather-card img {
        width: 50px;
        height: 50px;
    }

    .weather-card h3 {
        margin: 0;
        font-size: 20px;
        color: #333;
    }

    .weather-card p {
        font-size: 14px;
        color: #555;
    }

    .error {
        color: red;
        font-size: 18px;
    }
</style>

<script>
    // Fetch weather data for a given city
    async function getWeather(city) {
        // Reset error message and weather container
        document.getElementById('error-message').innerHTML = '';
        document.getElementById('weather-container').innerHTML = '';

        try {
            // Send a GET request to your backend API
            const response = await fetch(`http://127.0.0.1:8887/api/weather?city=${city}`);
            
            if (!response.ok) {
                throw new Error('Failed to fetch weather data');
            }

            // Parse the response JSON
            const data = await response.json();

            if (data.error) {
                document.getElementById('error-message').innerHTML = `Error: ${data.error}`;
                return;
            }

            // Display the weather data
            displayWeather(data.forecast);
        } catch (error) {
            console.error('Error:', error);
            document.getElementById('error-message').innerHTML = 'Error fetching weather data';
        }
    }

    // Function to display weather data on the page
    function displayWeather(forecast) {
        const weatherContainer = document.getElementById('weather-container');
        
        forecast.forEach(day => {
            const card = document.createElement('div');
            card.classList.add('weather-card');
            
            card.innerHTML = `
                <h3>${day.date}</h3>
                <img src="https:${day.icon}" alt="Weather Icon" />
                <p>High: ${day.temperature.high}°F</p>
                <p>Low: ${day.temperature.low}°F</p>
                <p>${day.condition}</p>
            `;
            weatherContainer.appendChild(card);
        });
    }
</script>