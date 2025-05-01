---
layout: tailwind
title: Air & Space Museum Info
permalink: /airspace
menu: nav/home.html
search_exclude: true
---
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>San Diego Air & Space Museum Visitor Guide</title>
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
  <img src="{{site.baseurl}}/images/air.png" alt="Air and Space Museum" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">San Diego Air & Space Museum Visitor Guide</h1>
    <!-- Museum Info Section -->
    <section class="section">
      <h2 class="section-title">About the Museum</h2>
      <p>Located in the heart of Balboa Park, the San Diego Air & Space Museum is a Smithsonian-affiliated institution featuring a vast collection of historic aircraft, spacecraft, and aviation artifacts. It offers interactive exhibits and immersive experiences for all ages, from early flight to modern space exploration.</p>
      <ul>
        <li><strong>Exhibits:</strong> Apollo 9 Command Module, Spirit of St. Louis replica, WWII aircraft, and modern jet fighters.</li>
        <li><strong>Activities:</strong> Flight simulators, 3D/4D theater, educational workshops, and special rotating exhibits.</li>
        <li><strong>Tips:</strong> Great for kids and aviation enthusiasts—buy tickets online to save time and check exhibit schedules in advance.</li>
      </ul>
    </section>
    <!-- Weather Recommendation Section -->
    <section class="section">
      <h2 class="section-title">Ideal Weather Conditions</h2>
      <p>Since most of the museum is indoors, it's a perfect destination year-round—even on rainy or hot days. However, the best overall experience is during <strong>spring and fall (March–May and September–November)</strong>, when the surrounding Balboa Park is especially pleasant. See our <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather feature</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Traffic feature</a> for daily updates.</p>
    </section>
    <!-- Nearby Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-success">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Museum</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Flight Path Grill</td>
            <td>Quick Bites / Cafe</td>
            <td>Inside Museum</td>
            <td><a href="https://sandiegoairandspace.org/visit/food" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Panama 66</td>
            <td>Casual / Cafe</td>
            <td>0.3 miles</td>
            <td><a href="https://www.panama66.com" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>The Prado at Balboa Park</td>
            <td>Upscale American</td>
            <td>0.4 miles</td>
            <td><a href="https://www.cohnrestaurants.com/theprado" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Daniel’s Coffee</td>
            <td>Quick Coffee & Snacks</td>
            <td>0.2 miles</td>
            <td><a href="https://danielscoffee.com" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <!-- Embedded Video Section -->
    <section class="section">
      <h2 class="section-title">See It for Yourself</h2>
      <p>Explore the fascinating exhibits and historic aircraft at the San Diego Air & Space Museum in this short feature video:</p>
      <div class="ratio ratio-16x9">
        <iframe 
          width="560" 
          height="315" 
          src="https://www.youtube.com/embed/Pn12b1B908k?autoplay=1&mute=1" 
          title="Air & Space Museum Video Tour" 
          frameborder="0" 
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
          referrerpolicy="strict-origin-when-cross-origin" 
          allowfullscreen>
        </iframe>
      </div>
    </section>
  </div>
</body>


<!-- 7-Day Forecast Section for San Diego Air & Space Museum -->
<section class="section">
  <h2 class="section-title">7-Day Weather Forecast at the San Diego Air & Space Museum</h2>
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
    loadAirSpaceMuseumWeather();
});

async function loadAirSpaceMuseumWeather() {
    const container = document.getElementById('weather-container');
    if (!container) {
        console.error("weather-container not found in DOM.");
        return;
    }

    container.innerHTML = ''; // Clear previous content

    try {
        const response = await fetch("http://127.0.0.1:8887/api/weather?type=forecast&city=92101"); // Using San Diego's city code 92101 for Air & Space Museum
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