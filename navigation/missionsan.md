---
layout: tailwind
title: Mission San Diego de Alcalá
permalink: /mission
menu: nav/home.html
search_exclude: true
---

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mission San Diego de Alcalá Guide</title>
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
  <img src="{{site.baseurl}}/images/mission.png" alt="Mission San Diego de Alcalá" class="w-80 mb-6 fade-in border-8 border-[#884d2a]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">Mission San Diego de Alcalá Guide</h1>
    <!-- About Section -->
    <section class="section">
      <h2 class="section-title">About the Mission</h2>
      <p>Mission San Diego de Alcalá, founded in 1769, is California’s first of 21 missions and a cornerstone of early Spanish settlement in the region. Located in San Diego’s Mission Valley, it’s a beautifully restored historic site with gardens, a church, museum, and bell tower. Visitors come to explore the architecture, reflect in the peaceful courtyards, and learn about its role in California history.</p>
      <ul>
        <li><strong>Visitor Tip:</strong> Modest attire is recommended, especially if attending mass. Bring a camera—this is a great spot for architecture and garden photos!</li>
      </ul>
    </section>
    <!-- Weather Section -->
    <section class="section">
      <h2 class="section-title">Best Time to Visit</h2>
      <p>The mission is open year-round, but the most comfortable weather occurs from <strong>March to June</strong> and <strong>September to November</strong>. Ideal temperatures range between <strong>65°F and 75°F</strong>. Avoid mid-summer heat and school field trip crowds when possible. Be sure to check the <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather updates</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Traffic routes</a>.</p>
    </section>
    <!-- Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-warning">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Mission</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>The Trails Eatery</td>
            <td>American / Breakfast & Lunch</td>
            <td>6 minutes</td>
            <td><a href="https://thetrailseatery.com" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Phils BBQ</td>
            <td>BBQ / Casual Dining</td>
            <td>10 minutes</td>
            <td><a href="https://philsbbq.net" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <!-- Video Section -->
    <section class="section">
      <h2 class="section-title">Explore the Mission</h2>
      <p>Watch this overview of Mission San Diego de Alcalá to get a glimpse of its history and setting:</p>
      <div class="ratio ratio-16x9">
        <iframe 
          width="560" 
          height="315" 
          src="https://www.youtube.com/embed/0lKZ9v3JnQI?autoplay=1&mute=1&si=oIvHSYqJPeql09wP" 
          title="Mission San Diego Tour" 
          frameborder="0" 
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
          allowfullscreen>
        </iframe>
      </div>
    </section>
  </div>
</body>

<!-- 7-Day Forecast Section for Mission San Diego de Alcalá -->
<section class="section">
  <h2 class="section-title">7-Day Weather Forecast at Mission San Diego de Alcalá</h2>
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
    loadMissionSanDiegoWeather();
});

async function loadMissionSanDiegoWeather() {
    const container = document.getElementById('weather-container');
    if (!container) {
        console.error("weather-container not found in DOM.");
        return;
    }

    container.innerHTML = ''; // Clear previous content

    try {
        const response = await fetch("http://127.0.0.1:8887/api/weather?type=forecast&city=92110"); // Using Mission San Diego de Alcalá's city code 92110
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