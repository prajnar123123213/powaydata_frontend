---
layout: tailwind
title: Gaslamp Quarter
permalink: /gaslamp
menu: nav/home.html
search_exclude: true
---

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gaslamp Quarter Visitor Guide</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #fff9f4;
      color: #212529;
    }
    .section {
      padding: 40px 0;
    }
    .section-title {
      font-size: 2rem;
      margin-bottom: 20px;
      font-weight: 600;
    }
    .table td, .table th {
      vertical-align: middle;
    }
    iframe {
      border-radius: 10px;
    }
  </style>
</head>

<div class="flex justify-center">
  <img src="{{site.baseurl}}/images/gaslamp.png" alt="Gaslamp Quarter" class="w-80 mb-6 fade-in border-8 border-[#470d0e]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">Gaslamp Quarter Visitor Guide</h1>
    <!-- About Section -->
    <section class="section">
      <h2 class="section-title">About the Gaslamp Quarter</h2>
      <p>The Gaslamp Quarter is a vibrant historic district in downtown San Diego known for its Victorian architecture, nightlife, and entertainment. Stretching over 16 blocks, it's packed with restaurants, rooftop bars, art galleries, and boutique shops. It's especially popular for its cultural festivals, parades, and rich history dating back to the 1860s.</p>
      <ul>
        <li><strong>Visitor Tips:</strong> Wear comfy walking shoes, explore during the afternoon for shopping, and enjoy rooftop dining in the evening. Parking can be tricky, so consider ride-shares or public transit.</li>
      </ul>
    </section>
    <!-- Weather Section -->
    <section class="section">
      <h2 class="section-title">Best Time to Visit</h2>
      <p>The Gaslamp Quarter is enjoyable year-round, but the best seasons are <strong>spring (March–May)</strong> and <strong>fall (September–November)</strong>, when the weather is mild and events are frequent. Look for days between <strong>68°F and 77°F</strong> for the most comfortable walking and dining experience. Check our <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Traffic</a> tools before your trip.</p>
    </section>
    <!-- Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-warning">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Location</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Gaslamp Fish House</td>
            <td>Seafood / American</td>
            <td>Within District</td>
            <td><a href="https://www.gaslampfishhouse.com" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Hodad's Downtown</td>
            <td>Burgers / Casual</td>
            <td>1 block from 5th Ave</td>
            <td><a href="https://hodadies.com" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
  </div>
</body>

<!-- 7-Day Forecast Section -->
<section class="section">
  <h2 class="section-title">7-Day Weather Forecast in the Gaslamp Quarter</h2>
  <div id="weather-container" class="weather-row"></div>
</section>

<style>
  .weather-row {
    display: flex;
    overflow-x: auto;
    gap: 20px; /* Space between the cards */
    padding: 10px;
    justify-content: start;
  }

  .weather-card {
    background-color: #007bff;  /* Set a background color for the card */
    padding: 15px;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 150px;
    min-width: 150px; /* Ensures the cards are a minimum size */
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    color: #ffffff;  /* Set the text color to white */
  }

  .weather-card img {
    max-width: 50px;
    max-height: 50px;
  }

  .weather-card h3 {
    font-size: 1.2rem;
    margin: 10px 0;
    color: #ffffff;  /* Ensure the date text is white */
  }

  .weather-card p {
    font-size: 0.9rem;
    margin: 5px 0;
  }

  .weather-card p strong {
    font-weight: bold;  /* Bold high/low temperature */
  }
</style>

<script>
document.addEventListener("DOMContentLoaded", () => {
    loadGaslampWeather();
});

async function loadGaslampWeather() {
    const container = document.getElementById('weather-container');
    if (!container) {
        console.error("weather-container not found in DOM.");
        return;
    }

    container.innerHTML = ''; // Clear previous content

    try {
        const response = await fetch("http://127.0.0.1:8887/api/weather?type=forecast&city=92101"); // Assuming the endpoint is for forecast
        if (!response.ok) throw new Error("Failed to fetch weather data");

        const data = await response.json();

        if (!data.forecast || !Array.isArray(data.forecast)) {
            container.innerHTML = '<p>Error: Invalid data structure</p>';
            console.error("Unexpected data format:", data);
            return;
        }

        // Loop through the forecast and create a card for each day
        data.forecast.forEach(day => {
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
    } catch (err) {
        console.error(err);
        container.innerHTML = '<p>Unable to load weather data.</p>';
    }
}
</script>