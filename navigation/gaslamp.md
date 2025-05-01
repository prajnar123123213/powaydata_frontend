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

    <!-- Video Section -->
    <section class="section">
      <h2 class="section-title">Take a Look Around</h2>
      <p>Here's a video tour to help you explore the Gaslamp Quarter before your visit:</p>
      <div class="ratio ratio-16x9">
        <iframe 
          width="560" 
          height="315" 
          src="https://www.youtube.com/embed/jlKXcZ9CPuE" 
          title="Gaslamp Quarter Tour" 
          frameborder="0" 
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
          allowfullscreen>
        </iframe>
      </div>
    </section>
  </div>
</body>