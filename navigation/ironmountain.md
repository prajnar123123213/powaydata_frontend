---
layout: tailwind
title: Iron Mountain Trial
permalink: /iron
menu: nav/home.html
search_exclude: true
---

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Iron Mountain Trail Guide</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #f4f4f9;
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
  <img src="{{site.baseurl}}/images/iron.png" alt="Iron Mountain Trail" class="w-80 mb-6 fade-in border-8 border-[#1d3e53]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">Iron Mountain Trail Guide</h1>
    <!-- About Section -->
    <section class="section">
      <h2 class="section-title">About Iron Mountain</h2>
      <p>Iron Mountain is one of the most popular hiking spots in San Diego County, located just outside Poway. The trail is approximately 5.2 miles round-trip and offers scenic views of the mountains and valleys, especially rewarding at the summit. It’s a moderate hike suitable for all skill levels, including beginners and families.</p>
      <ul>
        <li><strong>Pro Tip:</strong> Bring sunscreen, plenty of water, and a hat. The trail is mostly exposed with little shade. Early morning or late afternoon hikes are best to avoid heat.</li>
      </ul>
    </section>
    <!-- Weather Section -->
    <section class="section">
      <h2 class="section-title">Best Hiking Conditions</h2>
      <p>The best months to hike Iron Mountain are <strong>October through May</strong> when temperatures are cooler. Avoid midday in the summer due to intense heat. Ideal hiking weather is between <strong>60°F and 72°F</strong>. Be sure to check the <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">weather</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">trail access</a> before heading out.</p>
    </section>
    <!-- Nearby Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Food Options</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-info">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Trailhead</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Hamburger Factory</td>
            <td>American / Family Dining</td>
            <td>8 minutes</td>
            <td><a href="https://hamburgerfactory.com" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Nutmeg Bakery & Cafe</td>
            <td>Cafe / Breakfast</td>
            <td>10 minutes</td>
            <td><a href="https://nutmegcv.com" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <!-- Video Section -->
    <section class="section">
      <h2 class="section-title">Experience the Trail</h2>
      <p>Watch this quick overview of Iron Mountain to get a feel for the trail’s views and terrain:</p>
      <div class="ratio ratio-16x9">
        <iframe 
          width="560" 
          height="315" 
          src="https://www.youtube.com/embed/JbIDqHxBWLo?autoplay=1&mute=1&si=oIvHSYqJPeql09wP" 
          title="Iron Mountain Trail Poway" 
          frameborder="0" 
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
          allowfullscreen>
        </iframe>
      </div>
    </section>
  </div>
</body>

<!-- 7-Day Forecast Section for Iron Mountain Trail -->
<section class="section">
  <h2 class="section-title">7-Day Weather Forecast at Iron Mountain Trail</h2>
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
    loadIronMountainTrailWeather();
});

async function loadIronMountainTrailWeather() {
    const container = document.getElementById('weather-container');
    if (!container) {
        console.error("weather-container not found in DOM.");
        return;
    }

    container.innerHTML = ''; // Clear previous content

    try {
        const response = await fetch("http://127.0.0.1:8887/api/weather?type=forecast&city=92127"); // Using Poway's city code 92127 for Iron Mountain Trail
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