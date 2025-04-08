---
layout: tailwind
title: Weather
search_exclude: true
permalink: /weather/
---

<!-- weather.html -->
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather Information</title>
    <!-- Tailwind CSS CDN link -->
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100 font-sans">

<div class="container mx-auto p-4">
    <h1 class="text-3xl font-bold text-center mb-4">Weather Information</h1>
    <div class="flex justify-center mb-4">
        <input
            id="city-input"
            type="text"
            placeholder="Enter a city"
            class="border-2 p-2 rounded-md text-lg"
        />
        <button
            onclick="changeCity()"
            class="ml-4 px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600"
        >
            Get Weather
        </button>
    </div>
    <div class="text-center mt-6">
        <!-- Weather icon -->
        <div class="flex justify-center items-center mb-4">
            <img
                id="weather-icon"
                src=""
                alt="Weather Icon"
                class="w-16 h-16"
            />
        </div>
        <!-- Weather location -->
        <h2 id="weather-location" class="text-2xl font-semibold"></h2>
        <p id="weather-condition" class="text-xl mt-2"></p>
        <p id="weather-temp" class="text-4xl mt-4 font-bold"></p>
    </div>
</div>

<script>
// Function to get weather data from the backend API
async function getWeather(city = "poway") {
    try {
        // Sanitize city input by trimming any extra spaces or newlines
        city = city.trim();

        const response = await fetch(`/api/weather?city=${encodeURIComponent(city)}`);
        const data = await response.json();

        if (response.ok) {
            // Update the DOM with the weather data
            document.getElementById("weather-location").textContent = data.location;
            document.getElementById("weather-temp").textContent = data.temperature;
            document.getElementById("weather-condition").textContent = data.condition;
            // Update the weather icon with the correct image URL
            document.getElementById("weather-icon").src = "https:" + data.icon;
        } else {
            console.error("Error response from backend:", data);
            alert("Could not fetch weather data. Please try again.");
        }
    } catch (err) {
        console.error("Fetch failed:", err);
        alert("An error occurred while fetching weather data.");
    }
}

// Function to update the weather when the city changes
function changeCity() {
    const city = document.getElementById("city-input").value.trim() || "Poway";
    getWeather(city);
}

// Call the getWeather function on page load to show the default weather for Poway
document.addEventListener("DOMContentLoaded", () => {
    getWeather();
});
</script>

</body>

