---
layout: tailwind
title: Birch Aquarium 
permalink: /birch
menu: nav/home.html
search_exclude: true
---
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Birch Aquarium Visitor Guide</title>
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
  <img src="{{site.baseurl}}/images/birch.png" alt="Birch Aquarium" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">Birch Aquarium Visitor Guide</h1>
    <!-- About Section -->
    <section class="section">
      <h2 class="section-title">About Birch Aquarium</h2>
      <p>Birch Aquarium at Scripps Institution of Oceanography is a public exploration center for marine research and education in La Jolla, San Diego. It offers stunning ocean views, interactive exhibits, and live animal displays showcasing the wonders of the ocean and ocean science. The aquarium is perfect for families, school trips, or anyone passionate about marine life.</p>
      <ul>
        <li><strong>Tip:</strong> Tickets are cheaper when bought online in advance. Wear sunscreen, as many exhibits are outdoors with ocean views!</li>
      </ul>
    </section>
    <!-- Weather Section -->
    <section class="section">
      <h2 class="section-title">Ideal Weather Conditions</h2>
      <p>La Jolla weather is pleasant year-round, but the best time to visit Birch Aquarium is from <strong>April to June</strong> or <strong>September to October</strong>. Avoid peak summer crowds. Ideal visiting days have temperatures between <strong>68°F and 75°F</strong> with clear skies. Use our <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Traffic</a> features to plan your trip!</p>
    </section>
    <!-- Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-success">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Aquarium</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Duke's La Jolla</td>
            <td>Hawaiian / Seafood</td>
            <td>5 minutes</td>
            <td><a href="https://www.dukeslajolla.com/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Shorehouse Kitchen</td>
            <td>Brunch / American</td>
            <td>4 minutes</td>
            <td><a href="https://www.shorehousekitchen.com/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>The Taco Stand</td>
            <td>Mexican / Casual</td>
            <td>6 minutes</td>
            <td><a href="https://www.letstaco.com/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Piatti</td>
            <td>Italian / Upscale</td>
            <td>7 minutes</td>
            <td><a href="https://www.piatti.com/" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <!-- Video Section -->
    <section class="section">
      <h2 class="section-title">See It for Yourself</h2>
      <p>Check out this video for a tour of Birch Aquarium’s exhibits:</p>
      <div class="ratio ratio-16x9">
        <iframe 
          width="560" 
          height="315" 
          src="https://www.youtube.com/embed/dzmw0rRujrk?autoplay=1&mute=1" 
          title="Birch Aquarium Tour" 
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
