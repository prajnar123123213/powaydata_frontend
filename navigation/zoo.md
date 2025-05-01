---
layout: tailwind
title: San Diego Zoo Info
permalink: /zoo
menu: nav/home.html
search_exclude: true
---
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>San Diego Zoo Visitor Guide</title>
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
  <img src="{{site.baseurl}}/images/zoo.png" alt="Poway City" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">San Diego Zoo Visitor Guide</h1>
    <!-- Zoo Information Section -->
    <section class="section">
      <h2 class="section-title">About San Diego Zoo</h2>
      <p>The San Diego Zoo is one of the most renowned zoos in the world, housing over 12,000 rare and endangered animals representing more than 650 species and subspecies. Located in Balboa Park, it features lush, naturalistic habitats and cutting-edge exhibits.</p>
      <ul>
        <li><strong>Rides:</strong> Guided Bus Tour, Skyfari Aerial Tram, and Kangaroo Express Bus.</li>
        <li><strong>Popular Animals:</strong> Giant Pandas, Koalas, Elephants, Tigers, Gorillas, and Polar Bears.</li>
        <li><strong>Important Tips:</strong> Wear comfortable shoes, stay hydrated, and plan to arrive early for fewer crowds.</li>
      </ul>
    </section>
    <!-- Weather Recommendation Section -->
    <section class="section">
      <h2 class="section-title">Ideal Weather Conditions</h2>
        <p>San Diego’s climate is mild year-round, but the best months to visit the zoo are <strong>March through May</strong> and <strong>September through November</strong>. During these months, temperatures are comfortable, and the crowds are generally smaller. Aim for days with temperatures between <strong>65°F and 75°F</strong> and minimal humidity for the best experience. Visit our <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather feature</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Traffic feature</a> to see predictions for the upcoming days!</p>
    </section>
    <!-- Nearby Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-success">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Zoo</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>The Prado at Balboa Park</td>
            <td>American / Upscale</td>
            <td>0.2 miles</td>
            <td><a href="https://www.cohnrestaurants.com/theprado" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Panama 66</td>
            <td>Casual / Cafe</td>
            <td>0.3 miles</td>
            <td><a href="https://www.panama66.com" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Flight Path Grill</td>
            <td>Quick Bites</td>
            <td>Inside Zoo</td>
            <td><a href="https://zoo.sandiegozoo.org/dining" target="_blank">Visit Site</a></td>
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
    <!-- Embedded Video Section -->
    <section class="section">
      <h2 class="section-title">See It for Yourself</h2>
      <p>Watch this live to explore the beautiful landscapes, animal habitats, and attractions at the San Diego Zoo:</p>
<div class="ratio ratio-16x9">
  <iframe 
    width="560" 
    height="315" 
    src="https://www.youtube.com/embed/g5Yp2F438xk?autoplay=1&mute=1&si=oIvHSYqJPeql09wP" 
    title="YouTube video player" 
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" 
    allowfullscreen>
  </iframe>
</div>
    </section>
  </div>
</body>

<!-- 7-Day Forecast Section for San Diego Zoo -->
<section class="section">
  <h2 class="section-title">7-Day Weather Forecast at San Diego Zoo</h2>
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
    loadZooWeather();
});

async function loadZooWeather() {
    const container = document.getElementById('weather-container');
    if (!container) {
        console.error("weather-container not found in DOM.");
        return;
    }

    container.innerHTML = ''; // Clear previous content

    try {
        const response = await fetch("http://127.0.0.1:8887/api/weather?type=forecast&city=92101"); // San Diego Zoo is in the 92101 ZIP code
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