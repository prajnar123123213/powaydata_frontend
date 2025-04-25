---
layout: page
title: Weather
search_exclude: true
permalink: /weather/
---


<h1>7-Day Weather Forecast</h1>

<!-- Input section with both dropdowns and text fields -->
<div id="search-container">
    <div>
        <label>Choose or Type a State:</label><br />
        <select id="state-select">
            <option value="">Select a state</option>
        </select>
        <input type="text" id="state-input" placeholder="Or type a state" />
    </div>
    <div style="margin-top: 10px;">
        <label>Choose or Type a City:</label><br />
        <select id="city-select" disabled>
            <option value="">Select a city</option>
        </select>
        <input type="text" id="city-input" placeholder="Or type a city" />
    </div>
    <div style="margin-top: 15px;">
        <button onclick="handleWeatherSearch()">Get Weather</button>
    </div>
</div>

<div id="weather-container" class="weather-container"></div>
<div id="error-message" class="error"></div>

<style>
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        background-color: #333; /* Dark background */
        color: white; /* Text color adjusted for contrast */
        text-align: center;
    }

    h1 {
        background-color: #1976d2;
        color: white;
        padding: 20px;
        margin: 0;
    }

    #search-container {
        margin: 20px auto;
        max-width: 600px;
        padding: 20px;
        background: white;
        border-radius: 10px;
        box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }

    select, input[type="text"] {
        padding: 8px;
        width: 250px;
        font-size: 16px;
        border-radius: 5px;
        border: 1px solid #ccc;
        margin: 5px;
    }

    button {
        padding: 10px 20px;
        background-color: #1976d2;
        color: white;
        border: none;
        border-radius: 5px;
        font-size: 16px;
        cursor: pointer;
    }

    button:hover {
        background-color: #125ca1;
    }

    .weather-container {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        margin-top: 30px;
        gap: 20px;
    }

    .weather-card {
        background-color: white;
        border-radius: 12px;
        padding: 15px;
        width: 200px;
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        transition: transform 0.2s ease;
    }

    .weather-card:hover {
        transform: scale(1.03);
    }

    .weather-card img {
        width: 50px;
        height: 50px;
    }

    .weather-card h3 {
        margin: 0;
        font-size: 18px;
        color: #333;
    }

    .weather-card p {
        font-size: 14px;
        color: #555;
    }

    .error {
        color: red;
        font-size: 18px;
        margin-top: 20px;
    }
</style>

<script>
    const statesAndCities = {
        "CA": ["Los Angeles", "San Francisco", "San Diego"],
        "TX": ["Austin", "Dallas", "Houston"],
        "NY": ["New York", "Buffalo", "Albany"],
        "FL": ["Miami", "Tampa", "Orlando"],
        "IL": ["Chicago", "Springfield", "Naperville"]
        // Add all 50 states and their major cities here
    };

    // Populate state dropdown
    window.onload = function () {
        const stateSelect = document.getElementById('state-select');
        const citySelect = document.getElementById('city-select');

        for (const state in statesAndCities) {
            const option = document.createElement('option');
            option.value = state;
            option.textContent = state;
            stateSelect.appendChild(option);
        }

        // When state changes, load cities
        stateSelect.addEventListener('change', () => {
            const selectedState = stateSelect.value;
            citySelect.innerHTML = '<option value="">Select a city</option>';
            citySelect.disabled = true;

            if (statesAndCities[selectedState]) {
                statesAndCities[selectedState].forEach(city => {
                    const option = document.createElement('option');
                    option.value = city;
                    option.textContent = city;
                    citySelect.appendChild(option);
                });
                citySelect.disabled = false;
            }
        });
    };

    async function handleWeatherSearch() {
        const state = document.getElementById('state-select').value || document.getElementById('state-input').value;
        const city = document.getElementById('city-select').value || document.getElementById('city-input').value;
        const errorDiv = document.getElementById('error-message');
        const weatherContainer = document.getElementById('weather-container');

        errorDiv.innerHTML = '';
        weatherContainer.innerHTML = '';

        if (!state || !city) {
            errorDiv.innerHTML = 'Please select or type both a state and a city.';
            return;
        }

        const cityState = `${city},${state}`;

        try {
            const response = await fetch(`http://127.0.0.1:8887/api/weather?city=${encodeURIComponent(cityState)}`);
            if (!response.ok) throw new Error('Failed to fetch weather data');
            const data = await response.json();

            if (data.error) {
                errorDiv.innerHTML = `Error: ${data.error}`;
                return;
            }

            displayWeather(data.forecast);
        } catch (err) {
            console.error(err);
            errorDiv.innerHTML = 'Error fetching weather data';
        }
    }

    function displayWeather(forecast) {
        const container = document.getElementById('weather-container');
        forecast.forEach(day => {
            const card = document.createElement('div');
            card.className = 'weather-card';
            card.innerHTML = `
                <h3>${day.date}</h3>
                <img src="https:${day.icon}" alt="${day.condition}" />
                <p>${day.condition}</p>
                <p>High: ${day.temperature.high}°F</p>
                <p>Low: ${day.temperature.low}°F</p>
            `;
            container.appendChild(card);
        });
    }
</script>