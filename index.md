---
layout: tailwind
title: Poway City
search_exclude: true
hide: true
menu: nav/home.html
show_reading_time: false
---

# Welcome to Poway City!!
{: class="text-7xl text-center drop-shadow-lg"}

<p class="text-2xl text-center  max-w-3xl mx-auto mt-4 leading-relaxed">
    Reliable insights and information for Poway and beyond
</p>

<div class="flex justify-center">
  <img src="{{site.baseurl}}/images/poway.png" alt="Poway City" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
</div>

<svg viewBox="0 0 200 20" class="mx-auto mt-6 w-full h-32" xmlns="http://www.w3.org/2000/svg">
  <path d="M0,10 Q50,0 100,10 T200,10" fill="none" stroke="#801f7b" stroke-width="4" stroke-linecap="round" class="wave"/>
</svg>

<style>
  .wave {
    stroke-dasharray: 500; /* Length of the wave path */
    stroke-dashoffset: 500; /* Initially hide the stroke */
    animation: drawWave 2s ease-in-out forwards;
  }

  @keyframes drawWave {
    to {
      stroke-dashoffset: 0; /* Reveal the stroke */
    }
  }
</style>

## Features
{: class="text-6xl font-bold text-center mt-20 text-white"}

<div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-10 px-8 mt-12">
  <a href="{{site.baseurl}}/traffic/" class="bg-gradient-to-br from-green-100 to-green-300 rounded-3xl shadow-md p-6 hover:scale-105 transform transition-all duration-300">
      <h3 class="text-3xl font-bold text-green-900 text-center">Traffic</h3>
      <p class="text-md text-gray-800 mt-4 text-center">Real-time updates and analytics on Poway's traffic flow and congestion hotspots.</p>
  </a>
  <a href="{{site.baseurl}}/live/" class="bg-gradient-to-br from-green-100 to-green-300 rounded-3xl shadow-md p-6 hover:scale-105 transform transition-all duration-300">
      <h3 class="text-3xl font-bold text-green-900 text-center">Live Activity</h3>
      <p class="text-md text-gray-800 mt-4 text-center">Explore current events, local happenings, and community dynamics around you.</p>
  </a>
  <a href="{{site.baseurl}}/yelp" class="bg-gradient-to-br from-green-100 to-green-300 rounded-3xl shadow-md p-6 hover:scale-105 transform transition-all duration-300">
      <h3 class="text-3xl font-bold text-green-900 text-center"> Restaurant</h3>
      <p class="text-md text-gray-800 mt-4 text-center"> Explore and share reviews of restaurants that tourists can find around Poway.</p>
  </a>
</div>

<div class="w-24 h-1 mx-auto mt-16 rounded-full bg-green-600"></div>