---
layout: bootstrap 
title: Tourist Sites
description: Popular Destinations for Poway/SD Travel
permalink: /live/
hide: true
---    
<!-- once we make live activity work, we will link it to this table -->
<div class="row mx-3 mb-4 rounded-3 align-items-md-stretch" style="height: 100vh; width: 100%; overflow: auto;">
    <table class="table " id="cars" style="table-layout: fixed; height: 100%;">
        <thead>
            <tr>
                <th>Name</th>
                <th>Established</th>
                <th>Price</th>
                <th>Location</th>
            </tr>
        </thead>
        <tbody>
            <!-- Rows will be dynamically added here -->
        </tbody>
    </table>
    <style>
    /* Force black font in table cells */
    tbody td {
        color: #000 !important;
    }
    thead th {
        color: #000 !important;
    }
    /* Optional: Style the table header background for contrast */
    thead {
        background-color: #d4f5d1;
    }
    /* Optional: Light green row hover */
    table tbody tr:hover {
        background-color: #eafae8;
    }
    </style>
    <script>
        // Inline JavaScript Object for Cars
        const cars = [
            { name: "Balboa Park", established: 1868, price: "Free", location: "San Diego, CA" },
            { name: "San Diego Zoo", established: 1916, price: "$69.95", location: "2920 Zoo Dr, San Diego, CA 92101" },
            { name: "SeaWorld San Diego", established: 1964, price: "$74.99+", location: "500 Sea World Dr, San Diego, CA 92109" },
            { name: "USS Midway Museum", established: 2004, price: "$32", location: "910 N Harbor Dr, San Diego, CA 92101" },
            { name: "Old Town San Diego State Historic Park", established: 1969, price: "Free", location: "4002 Wallace St, San Diego, CA 92110" },
            { name: "La Jolla Cove", established: "N/A", price: "Free", location: "La Jolla, CA 92037" },
            { name: "Torrey Pines State Natural Reserve", established: 1959, price: "$12-25 parking", location: "12600 N Torrey Pines Rd, La Jolla, CA 92037" },
            { name: "Cabrillo National Monument", established: 1913, price: "$10 per person", location: "1800 Cabrillo Memorial Dr, San Diego, CA 92106" },
            { name: "Sunset Cliffs Natural Park", established: "N/A", price: "Free", location: "Ladera St, San Diego, CA 92107" },
            { name: "Coronado Beach", established: "N/A", price: "Free", location: "Coronado, CA 92118" },
            { name: "Birch Aquarium at Scripps", established: 1903, price: "$24.95", location: "2300 Expedition Way, La Jolla, CA 92037" },
            { name: "San Diego Air & Space Museum", established: 1963, price: "$22.50", location: "2001 Pan American Plaza, San Diego, CA 92101" },
            { name: "Gaslamp Quarter", established: "1800s", price: "Free", location: "San Diego, CA 92101" },
            { name: "Seaport Village", established: 1980, price: "Free", location: "849 W Harbor Dr, San Diego, CA 92101" },
            { name: "LEGOLAND California", established: 1999, price: "$89+", location: "1 Legoland Dr, Carlsbad, CA 92008" },
            { name: "Mission San Diego de Alcalá", established: 1769, price: "$5 donation", location: "10818 San Diego Mission Rd, San Diego, CA 92108" },
            { name: "Point Loma Tide Pools", established: "N/A", price: "$10 per person", location: "Point Loma, CA 92106" },
            { name: "Petco Park", established: 2004, price: "Varies", location: "100 Park Blvd, San Diego, CA 92101" },
            { name: "The New Children's Museum", established: 2008, price: "$15", location: "200 W Island Ave, San Diego, CA 92101" },
            { name: "Fleet Science Center", established: 1973, price: "$24.95", location: "1875 El Prado, San Diego, CA 92101" },
            { name: "San Diego Natural History Museum", established: 1874, price: "$22", location: "1788 El Prado, San Diego, CA 92101" },
            { name: "San Diego Botanic Garden", established: 1970, price: "$18", location: "300 Quail Gardens Dr, Encinitas, CA 92024" },
            { name: "Poway Lake", established: "N/A", price: "Free", location: "14644 Lake Poway Rd, Poway, CA 92064" },
            { name: "Iron Mountain Trail", established: "N/A", price: "Free", location: "Poway, CA 92064" },
            { name: "San Elijo Lagoon", established: "N/A", price: "Free", location: "2710 Manchester Ave, Cardiff, CA 92007" }
        ];
        // Populate the table dynamically
        const tbody = document.querySelector("#cars tbody");
        cars.forEach(car => {
            const row = document.createElement("tr");
            row.innerHTML = `
                <td>${car.name}</td>
                <td>${car.established}</td>
                <td>${car.price}</td>
                <td>${car.location}</td>
            `;
            tbody.appendChild(row);
        });
        // Initialize DataTable add text-primary to a-tags for visability
        $(document).ready(function () {
            $('#cars').DataTable({
                drawCallback: function () {
                    // Add Bootstrap's text-primary class to the inner HTML of <a> tags inside pagination buttons
                    $('.dataTables_paginate .paginate_button a').each(function () {
                        const link = $(this);
                        const innerHTML = link.html();
                        link.html(`<span class="text-primary">${innerHTML}</span>`);
                    });
                }
            });
        });
    </script>
</div>

<!-- weather.html -->
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather Information</title>
    <!-- Tailwind CSS CDN link -->
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100 font-sans">

<div class="container mx-auto p-4">
    <h1 class="text-3xl font-bold text-center mb-4">Weather Information</h1>

    <div class="flex justify-center mb-4">
        <input
            id="city-input"
            type="text"
            placeholder="Enter a city"
            class="border-2 p-2 rounded-md text-lg"
        />
        <button
            onclick="changeCity()"
            class="ml-4 px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600"
        >
            Get Weather
        </button>
    </div>

    <div class="text-center mt-6">
        <!-- Weather icon -->
        <div class="flex justify-center items-center mb-4">
            <img
                id="weather-icon"
                src=""
                alt="Weather Icon"
                class="w-16 h-16"
            />
        </div>

        <!-- Weather location -->
        <h2 id="weather-location" class="text-2xl font-semibold"></h2>
        <p id="weather-condition" class="text-xl mt-2"></p>
        <p id="weather-temp" class="text-4xl mt-4 font-bold"></p>
    </div>
</div>

<script>
// Function to get weather data from the backend API
async function getWeather(city = "poway") {
    try {
        // Sanitize city input by trimming any extra spaces or newlines
        city = city.trim();

        const response = await fetch(`/api/weather?city=${encodeURIComponent(city)}`);
        const data = await response.json();

        if (response.ok) {
            // Update the DOM with the weather data
            document.getElementById("weather-location").textContent = data.location;
            document.getElementById("weather-temp").textContent = data.temperature;
            document.getElementById("weather-condition").textContent = data.condition;
            // Update the weather icon with the correct image URL
            document.getElementById("weather-icon").src = "https:" + data.icon;
        } else {
            console.error("Error response from backend:", data);
            alert("Could not fetch weather data. Please try again.");
        }
    } catch (err) {
        console.error("Fetch failed:", err);
        alert("An error occurred while fetching weather data.");
    }
}

// Function to update the weather when the city changes
function changeCity() {
    const city = document.getElementById("city-input").value.trim() || "Poway";
    getWeather(city);
}

// Call the getWeather function on page load to show the default weather for Poway
document.addEventListener("DOMContentLoaded", () => {
    getWeather();
});
</script>

</body>

