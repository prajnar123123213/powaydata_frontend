---
layout: tailwind
title: Fleet Science Center
permalink: /fleet
menu: nav/home.html
search_exclude: true
---
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fleet Science Center Visitor Guide</title>
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
  <img src="{{site.baseurl}}/images/fleet.png" alt="Fleet Science Center" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
</div>
<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">Fleet Science Center Visitor Guide</h1>  
    <!-- About Section -->
    <section class="section">
      <h2 class="section-title">About Fleet Science Center</h2>
      <p>The Fleet Science Center, located in the heart of Balboa Park, San Diego, is an interactive science museum and planetarium dedicated to inspiring lifelong learning through science. With hands-on exhibits, IMAX films, and science workshops for all ages, it’s an exciting destination for students, families, and curious minds of all ages.</p>
      <ul>
        <li><strong>Tip:</strong> Visit on a weekday morning to avoid school group crowds. Don’t miss the interactive “Power Play San Diego” exhibit!</li>
      </ul>
    </section>
    <!-- Weather Section -->
    <section class="section">
      <h2 class="section-title">Ideal Weather Conditions</h2>
      <p>Since Fleet Science Center is indoors, it’s perfect to visit year-round—even on rainy or hot days. Still, for a complete Balboa Park experience, visit during <strong>spring or fall</strong> when the park is green and temperatures are <strong>65°F to 75°F</strong>. Use our <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Traffic</a> pages to plan your trip!</p>
    </section>
    <!-- Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-success">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Science Center</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>The Prado at Balboa Park</td>
            <td>Californian / Upscale</td>
            <td>2 minutes</td>
            <td><a href="https://www.cohnrestaurants.com/theprado" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Panama 66</td>
            <td>American / Outdoor Patio</td>
            <td>3 minutes</td>
            <td><a href="https://www.panama66.com/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Craft Cafe</td>
            <td>Quick Bites / Coffee</td>
            <td>1 minute</td>
            <td><a href="https://www.instagram.com/craftcafesd/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>CUCINA urbana</td>
            <td>Italian / Modern</td>
            <td>7 minutes</td>
            <td><a href="https://www.cucinaurbana.com/" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <!-- Video Section -->
    <section class="section">
      <h2 class="section-title">See It for Yourself</h2>
      <p>Explore the Fleet Science Center through this fun virtual tour and see what makes it a must-visit San Diego destination:</p>
      <div class="ratio ratio-16x9">
        <iframe 
          width="560" 
          height="315" 
          src="https://www.youtube.com/embed/Xdl2wlkLjng?autoplay=1&mute=1" 
          title="Fleet Science Center Tour" 
          frameborder="0" 
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
          referrerpolicy="strict-origin-when-cross-origin" 
          allow="autoplay" 
          allowfullscreen>
        </iframe>
      </div>
    </section>
  </div>
</body>


<!-- 7-Day Forecast Section for Fleet Science Center -->
<section class="section">
  <h2 class="section-title">7-Day Weather Forecast at the Fleet Science Center</h2>
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
    loadFleetScienceCenterWeather();
});

async function loadFleetScienceCenterWeather() {
    const container = document.getElementById('weather-container');
    if (!container) {
        console.error("weather-container not found in DOM.");
        return;
    }

    container.innerHTML = ''; // Clear previous content

    try {
        const response = await fetch("http://127.0.0.1:8887/api/weather?type=forecast&city=92101"); // Using San Diego's city code 92101 for Fleet Science Center
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