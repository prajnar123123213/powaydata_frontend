---
layout: tailwind
title: Sea World Park Info
permalink: /seaworld
menu: nav/home.html
search_exclude: true
---
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sea World Visitor Guide</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #f4f9f4;
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
  <img src="{{site.baseurl}}/images/seaworld.png" alt="Poway City" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">Sea World Visitor Guide</h1>
    <!-- Zoo Information Section -->
    <section class="section">
      <h2 class="section-title">About Sea World</h2>
      <p>SeaWorld is a marine theme park known for its thrilling rides, animal shows, and up-close encounters with sea creatures. Visitors can enjoy roller coasters like Mako and Infinity Falls, watch dolphin and orca performances, and explore aquariums filled with sharks, rays, and penguins. It's a mix of fun, education, and adventure for all ages.</p>
      <ul>
        <li><strong>Rides:</strong> Mako, Manta, Infinity Falls, Journey to Atlantis, Kraken, Ice Breaker, Wild Arctic Ride, Tidal Twister, and Electric Eel.</li>
        <li><strong>Popular Animals:</strong> Orcas, dolphins, sea lions, penguins, sharks..</li>
        <li><strong>Important Tips:</strong> Wear comfortable shoes, stay hydrated, and plan to arrive early for fewer crowds.</li>
      </ul>
    </section>
    <!-- Weather Recommendation Section -->
    <section class="section">
      <h2 class="section-title">Ideal Weather Conditions</h2>
        <p>San Diego’s climate is mild year-round, but the best months to visit Seaworld are <strong>March through May</strong> and <strong>September through November</strong>. During these months, temperatures are comfortable, and the crowds are generally smaller. Aim for days with temperatures between <strong>65°F and 75°F</strong> and minimal humidity for the best experience. Visit our <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather feature</a> to see predictions for the upcoming days!</p>
    </section>
    <!-- Nearby Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-success">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Sea World</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Firefly Eatery & Bar</td>
            <td>American / Upscale</td>
            <td>1 mile</td>
            <td><a href="https://thedana.com" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Dockside </td>
            <td>Casual / Cafe</td>
            <td>1.7 miles</td>
            <td><a href="https://www.bahiahotel.com/dockside-1953" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Covewood</td>
            <td>Quick Bites</td>
            <td>2.6 miles</td>
            <td><a href="https://www.missionbayresort.com/covewood-restaurant/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Albert's Restaurant</td>
            <td>American / Casual</td>
            <td>Inside Zoo</td>
            <td><a href="https://zoo.sandiegozoo.org/dining/alberts" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>

<!-- 7-Day Forecast Section for SeaWorld -->
<section class="section">
  <h2 class="section-title">7-Day Weather Forecast at SeaWorld</h2>
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
    loadSeaWorldWeather();
});

async function loadSeaWorldWeather() {
    const container = document.getElementById('weather-container');
    if (!container) {
        console.error("weather-container not found in DOM.");
        return;
    }

    container.innerHTML = ''; // Clear previous content

    try {
        const response = await fetch("http://127.0.0.1:8887/api/weather?type=forecast&city=92109"); // SeaWorld is in the 92109 ZIP code
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