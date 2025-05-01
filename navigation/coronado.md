---
layout: tailwind
title: Coronado Beach
permalink: /coronado
menu: nav/home.html
search_exclude: true
---
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Coronado Beach Visitor Guide</title>
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
  <img src="{{site.baseurl}}/images/coronado.png" alt="Coronado Beach" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">Coronado Beach Visitor Guide</h1>
    <!-- About Section -->
    <section class="section">
      <h2 class="section-title">About Coronado Beach</h2>
      <p>Coronado Beach is one of San Diego’s most iconic and scenic coastal destinations, known for its wide, flat sand and the historic Hotel del Coronado. Ideal for swimming, sunbathing, beachcombing, or surfing, it's a perfect spot for families, couples, or solo travelers looking to relax and soak up the California sun.</p>
      <ul>
        <li><strong>Tip:</strong> Parking can get busy on weekends, so arrive early or consider biking. Bring sunscreen, towels, and snacks for a full beach day!</li>
      </ul>
    </section>
    <!-- Weather Section -->
    <section class="section">
      <h2 class="section-title">Ideal Weather Conditions</h2>
      <p>Coronado Beach has beautiful weather most of the year. The best time to visit is between <strong>May and October</strong> when temperatures range from <strong>70°F to 80°F</strong>. Early fall offers warm water, fewer crowds, and stunning sunsets. Check our <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Traffic</a> pages to plan ahead!</p>
    </section>
    <!-- Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-success">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Beach</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Peohe’s</td>
            <td>Seafood / Waterfront Dining</td>
            <td>8 minutes</td>
            <td><a href="https://www.peohes.com/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Clayton’s Coffee Shop</td>
            <td>Classic Diner / Breakfast</td>
            <td>3 minutes</td>
            <td><a href="https://www.claytonscoffeeshop.com/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Brigantine Seafood & Oyster Bar</td>
            <td>Seafood / Upscale Casual</td>
            <td>7 minutes</td>
            <td><a href="https://www.brigantine.com/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Little Frenchie</td>
            <td>French Bistro</td>
            <td>5 minutes</td>
            <td><a href="https://www.littlefrenchiesd.com/" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <!-- Video Section -->
    <section class="section">
      <h2 class="section-title">See It for Yourself</h2>
      <p>Take a virtual tour of Coronado Beach and see why it's a top destination in San Diego:</p>
      <div class="ratio ratio-16x9">
        <iframe 
          width="560" 
          height="315" 
          src="https://www.youtube.com/embed/aCmuzAPpAZg?autoplay=1&mute=1" 
          title="Coronado Beach Tour" 
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

<!-- 7-Day Forecast Section for Coronado -->
<section class="section">
  <h2 class="section-title">7-Day Weather Forecast in Coronado</h2>
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
    loadCoronadoWeather();
});

async function loadCoronadoWeather() {
    const container = document.getElementById('weather-container');
    if (!container) {
        console.error("weather-container not found in DOM.");
        return;
    }

    container.innerHTML = ''; // Clear previous content

    try {
        const response = await fetch("http://127.0.0.1:8887/api/weather?type=forecast&city=92118"); // Assuming Coronado's city code is 92118
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