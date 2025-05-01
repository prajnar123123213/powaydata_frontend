---
layout: tailwind
title: La Jolla Cove
permalink: /lajolla
menu: nav/home.html
search_exclude: true
---

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>La Jolla Cove Visitor Guide</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background-color: #f0f8ff;
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
  <img src="{{site.baseurl}}/images/lajolla.png" alt="La Jolla Cove" class="w-80 mb-6 fade-in border-8 border-[#0d3e47]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">La Jolla Cove Visitor Guide</h1>
    <!-- About Section -->
    <section class="section">
      <h2 class="section-title">About La Jolla Cove</h2>
      <p>La Jolla Cove is a picturesque coastal spot in San Diego, famous for its dramatic cliffs, turquoise water, sea lions, and marine life. It’s a top destination for snorkeling, scuba diving, kayaking, and sunset watching. The area is part of the San Diego-La Jolla Underwater Park Ecological Reserve, meaning the waters are protected and filled with wildlife.</p>
      <ul>
        <li><strong>Helpful Tips:</strong> Arrive early for parking, bring a wetsuit or snorkel gear, and be respectful of wildlife—especially the sea lions, which are often resting on the rocks!</li>
      </ul>
    </section>
    <!-- Weather Section -->
    <section class="section">
      <h2 class="section-title">Ideal Visiting Conditions</h2>
      <p>La Jolla Cove is best enjoyed from <strong>May to October</strong> when ocean visibility is clear and the water is warmest. Temperatures between <strong>70°F and 80°F</strong> with low wind make for the perfect beach day. Check the <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather Report</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Live Traffic</a> before visiting.</p>
    </section>
    <!-- Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-primary">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Cove</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Brockton Villa</td>
            <td>Coastal / Breakfast</td>
            <td>2-minute walk</td>
            <td><a href="https://www.brocktonvilla.com" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Duke’s La Jolla</td>
            <td>Hawaiian / Seafood</td>
            <td>5-minute walk</td>
            <td><a href="https://www.dukeslajolla.com" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <!-- Video Section -->
    <section class="section">
      <h2 class="section-title">See It for Yourself</h2>
      <p>Enjoy this short walkthrough of La Jolla Cove to get a feel for its beauty and marine life:</p>
      <div class="ratio ratio-16x9">
        <iframe 
          width="560" 
          height="315" 
          src="https://www.youtube.com/embed/FfhpYTRhgHc?autoplay=1&mute=1&si=oIvHSYqJPeql09wP" 
          title="La Jolla Cove Tour" 
          frameborder="0" 
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
          allowfullscreen>
        </iframe>
      </div>
    </section>
  </div>
</body>

<!-- 7-Day Forecast Section for La Jolla Cove -->
<section class="section">
  <h2 class="section-title">7-Day Weather Forecast at La Jolla Cove</h2>
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
    loadLaJollaCoveWeather();
});

async function loadLaJollaCoveWeather() {
    const container = document.getElementById('weather-container');
    if (!container) {
        console.error("weather-container not found in DOM.");
        return;
    }

    container.innerHTML = ''; // Clear previous content

    try {
        const response = await fetch("http://127.0.0.1:8887/api/weather?type=forecast&city=92037"); // Using La Jolla's city code 92037 for La Jolla Cove
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