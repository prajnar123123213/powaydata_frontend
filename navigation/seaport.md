---
layout: tailwind
title: Seaport Village Info
permalink: /seaport
menu: nav/home.html
search_exclude: true
---
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Seaport Village Visitor Guide</title>
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
  <img src="{{site.baseurl}}/images/seaport.png" alt="Seaport Village" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">Seaport Village Visitor Guide</h1>
    <!-- Seaport Info Section -->
    <section class="section">
      <h2 class="section-title">About Seaport Village</h2>
      <p>Seaport Village is a waterfront shopping and dining complex in downtown San Diego. It features over 50 diverse shops, casual and fine dining restaurants, and stunning views of the San Diego Bay. It's a great spot for relaxing walks, live entertainment, and watching boats glide by.</p>
      <ul>
        <li><strong>Highlights:</strong> Unique boutiques, waterfront dining, kite-flying areas, and a historic carousel.</li>
        <li><strong>Activities:</strong> Strolling the boardwalk, shopping, dining, and watching street performers.</li>
        <li><strong>Tips:</strong> Parking can be limited—consider public transit or rideshare. Wear sun protection and comfy shoes.</li>
      </ul>
    </section>
    <!-- Weather Recommendation Section -->
    <section class="section">
      <h2 class="section-title">Ideal Weather Conditions</h2>
      <p>Seaport Village enjoys San Diego’s year-round mild weather. For the most enjoyable experience, plan your visit between <strong>March and May</strong> or <strong>September and November</strong>, when temperatures range from <strong>65°F to 75°F</strong> and the breeze off the bay is refreshing. Check out our <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather feature</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Traffic feature</a> to plan your trip efficiently.</p>
    </section>
    <!-- Nearby Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-success">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Seaport Village</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Edgewater Grill</td>
            <td>Seafood / American</td>
            <td>Inside Village</td>
            <td><a href="https://www.edgewatergrill.com" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Busters Beach House</td>
            <td>Casual Dining</td>
            <td>Inside Village</td>
            <td><a href="https://www.bustersbeachhouse.com" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Mike Hess Brewing</td>
            <td>Craft Beer & Bites</td>
            <td>0.1 miles</td>
            <td><a href="https://www.mikehessbrewing.com/seaport-village/" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Puesto at The Headquarters</td>
            <td>Mexican / Modern</td>
            <td>0.2 miles</td>
            <td><a href="https://www.eatpuesto.com/locations/headquarters-san-diego/" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <!-- Embedded Video Section -->
    <section class="section">
      <h2 class="section-title">See It for Yourself</h2>
      <p>Take a look at the scenic views, shops, and relaxing atmosphere of Seaport Village in this short video:</p>
      <div class="ratio ratio-16x9">
        <iframe 
          width="560" 
          height="315" 
          src="https://www.youtube.com/embed/WA79RYzJzXU?autoplay=1&mute=1" 
          title="Seaport Village Tour" 
          frameborder="0" 
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
          referrerpolicy="strict-origin-when-cross-origin" 
          allowfullscreen>
        </iframe>
      </div>
    </section>
  </div>
</body>
