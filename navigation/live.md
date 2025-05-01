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
                <th>Price</th>
                <th>Location</th>
                <th>Info</th>
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
            { name: "Balboa Park", price: "Free", location: "San Diego, CA", info: "{{site.baseurl}}/balboa" },
            { name: "San Diego Zoo", price: "$69.95", location: "2920 Zoo Dr, San Diego, CA 92101", info: "{{site.baseurl}}/zoo" },
            { name: "SeaWorld San Diego", price: "$74.99+", location: "500 Sea World Dr, San Diego, CA 92109", info: "lol" },
            { name: "USS Midway Museum", price: "$32", location: "910 N Harbor Dr, San Diego, CA 92101", info: "lol" },
            { name: "Old Town San Diego State Historic Park", price: "Free", location: "4002 Wallace St, San Diego, CA 92110", info: "lol" },
            { name: "La Jolla Cove", price: "Free", location: "La Jolla, CA 92037", info: "lol" },
            { name: "Torrey Pines State Natural Reserve", price: "$12-25 parking", location: "12600 N Torrey Pines Rd, La Jolla, CA 92037", info: "lol" },
            { name: "Cabrillo National Monument", price: "$10 per person", location: "1800 Cabrillo Memorial Dr, San Diego, CA 92106", info: "lol" },
            { name: "Sunset Cliffs Natural Park", price: "Free", location: "Ladera St, San Diego, CA 92107", info: "lol" },
            { name: "Coronado Beach", price: "Free", location: "Coronado, CA 92118", info: "{{site.baseurl}}/coronado" },
            { name: "Birch Aquarium at Scripps", price: "$24.95", location: "2300 Expedition Way, La Jolla, CA 92037", info: "{{site.baseurl}}/birch" },
            { name: "San Diego Air & Space Museum", price: "$22.50", location: "2001 Pan American Plaza, San Diego, CA 92101", info: "lol" },
            { name: "Gaslamp Quarter", price: "Free", location: "San Diego, CA 92101", info: "lol" },
            { name: "Seaport Village", price: "Free", location: "849 W Harbor Dr, San Diego, CA 92101", info: "lol" },
            { name: "LEGOLAND California", price: "$89+", location: "1 Legoland Dr, Carlsbad, CA 92008", info: "{{site.baseurl}}/legoland" },
            { name: "Mission San Diego de Alcalá", price: "$5 donation", location: "10818 San Diego Mission Rd, San Diego, CA 92108", info: "lol" },
            { name: "Point Loma Tide Pools", price: "$10 per person", location: "Point Loma, CA 92106", info: "lol" },
            { name: "Petco Park", price: "Varies", location: "100 Park Blvd, San Diego, CA 92101", info: "lol" },
            { name: "The New Children's Museum", price: "$15", location: "200 W Island Ave, San Diego, CA 92101", info: "lol" },
            { name: "Fleet Science Center", price: "$24.95", location: "1875 El Prado, San Diego, CA 92101", info: "{{site.baseurl}}/fleet" },
            { name: "San Diego Natural History Museum", price: "$22", location: "1788 El Prado, San Diego, CA 92101", info: "lol" },
            { name: "San Diego Botanic Garden", price: "$18", location: "300 Quail Gardens Dr, Encinitas, CA 92024", info: "lol" },
            { name: "Poway Lake", price: "Free", location: "14644 Lake Poway Rd, Poway, CA 92064", info: "lol" },
            { name: "Iron Mountain Trail", price: "Free", location: "Poway, CA 92064", info: "lol" },
            { name: "San Elijo Lagoon", price: "Free", location: "2710 Manchester Ave, Cardiff, CA 92007", info: "lol" }
        ];
        // Populate the table dynamically
        const tbody = document.querySelector("#cars tbody");
        cars.forEach(car => {
            const row = document.createElement("tr");
            row.innerHTML = `
                <td>${car.name}</td>
                <td>${car.price}</td>
                <td>${car.location}</td>
                <td><a href="${car.info}" target="_blank">Click Here! 📌</a></td>
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

