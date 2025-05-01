---
layout: tailwind
title: Balboa Park Info
permalink: /balboa
menu: nav/home.html
search_exclude: true
---
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Balboa Park Visitor Guide</title>
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
  <img src="{{site.baseurl}}/images/balboa.png" alt="Poway City" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
</div>

<body>
  <div class="container py-5">
    <h1 class="text-center mb-5">Balboa Park Visitor Guide</h1>
    <!-- Zoo Information Section -->
    <section class="section">
      <h2 class="section-title">About Balboa Park</h2>
      <p>Balboa Park is a 1,200-acre historic urban cultural park in San Diego, California. Placed in reserve in 1835, the park's site is one of the oldest in the United States dedicated to public recreational use. The park hosts various museums, theaters, restaurants, and the San Diego Zoo.</p>
      <ul>
        <li><strong>Important Tips:</strong> Wear comfortable shoes, stay hydrated, and plan to arrive early for fewer crowds. Many attractions also cost money, so bring some cash with you incase. </li>
      </ul>
    </section>
    <!-- Weather Recommendation Section -->
    <section class="section">
      <h2 class="section-title">Ideal Weather Conditions</h2>
        <p>Balboa's climate is mild year-round, but the best months to visit are <strong>April through May</strong> and <strong>September through November</strong>. During these months, temperatures are comfortable, and the crowds are generally smaller. Aim for days with temperatures between <strong>65°F and 75°F</strong> and minimal humidity for the best experience. Visit our <a href="{{site.baseurl}}/weather" class="text-primary" target="_blank">Weather feature</a> and <a href="{{site.baseurl}}/traffic" class="text-primary" target="_blank">Traffic feature</a> to see predictions for the upcoming days!</p>
    </section>
    <!-- Nearby Restaurants Section -->
    <section class="section">
      <h2 class="section-title">Nearby Restaurants</h2>
      <table class="table table-striped table-bordered">
        <thead class="table-success">
          <tr>
            <th>Restaurant</th>
            <th>Type</th>
            <th>Distance from Park</th>
            <th>Website</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>The Prado at Balboa Park</td>
            <td>American / Upscale</td>
            <td>In Park</td>
            <td><a href="https://www.cohnrestaurants.com/theprado" target="_blank">Visit Site</a></td>
          </tr>
          <tr>
            <td>Panama 66</td>
            <td>Casual / Cafe</td>
            <td>2 minutes</td>
            <td><a href="https://www.panama66.com" target="_blank">Visit Site</a></td>
          </tr>
        </tbody>
      </table>
    </section>
    <!-- Embedded Video Section -->
    <section class="section">
      <h2 class="section-title">See It for Yourself</h2>
      <p>Watch this live to see a walk through of the Balboa Park:</p>
<div class="ratio ratio-16x9">
<iframe 
  width="560" 
  height="315" 
  src="https://www.youtube.com/embed/PUy0undDc38?autoplay=1&mute=1" 
  title="YouTube video player" 
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

