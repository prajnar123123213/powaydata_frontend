---
layout: post
title: Poway City
search_exclude: true
hide: true
menu: nav/home.html
show_reading_time: false
---
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Poway City</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Julius+Sans+One&display=swap" rel="stylesheet">>
    <style>
        /* Loading Screen */
        body {
            font-family: 'Julius Sans One', sans-serif;
        }
        .loader {
            border-top-color: #0e470d;
            animation: spin 1.5s infinite linear;
        }
        @keyframes spin {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }
        /* Fade-in animation */
        .fade-in {
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 1.2s ease-out, transform 1.2s ease-out;
        }
        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
        /* Gradient Animation */
        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        .animate-gradient {
            background-size: 200% 200%;
            animation: gradient 8s ease infinite;
        }
        /* Typewriter effect */
        .typewriter {
            font-size: 5rem;
            font-weight: 900;
            overflow: hidden;
            white-space: nowrap;
            margin: 0 auto;
            word-spacing: 1em;
            line-height: 1.2;
        }
        .typewriter .text {
            display: inline-block;
            opacity: 0;
        }
    </style>
</head>

<body class="bg-black text-white relative">
    <!-- Loading Screen -->
    <div id="loading-screen" class="fixed inset-0 bg-green-900 flex items-center justify-center z-50">
        <div class="text-center">
            <div class="loader ease-linear rounded-full border-8 border-t-8 border-white h-32 w-32 mb-4"></div>
            <h2 class="text-4xl font-semibold text-white">Loading...</h2>
        </div>
    </div>
    <!-- Background Animation -->
    <div class="absolute top-0 left-0 w-full h-full overflow-hidden -z-10">
        <div class="bg-gradient-to-r from-green-700 via-green-600 to-green-900 w-full h-full opacity-70 animate-gradient"></div>
    </div>
    <!-- About Us Section -->
    <section id="about" class="h-screen flex flex-col items-center justify-center text-center bg-orange-100 text-black">
        <h2 class="text-7xl font-extrabold text-teal-800 fade-in mb-6">The City of Poway</h2>
        <img src="{{site.baseurl}}/images/poway.png" alt="Poway City" class="w-80 mb-6 fade-in border-8 border-[#0e470d]" />
        <p class="text-3xl text-teal-800 max-w-5xl fade-in">
            Discover city-wide analytics and explore interactive content that shape our future.
        </p>
    </section>
    <!-- Features Section -->
    <section id="features" class="py-20 bg-teal-800">
        <h2 class="text-7xl font-bold text-center text-orange-100 mb-10 fade-in">Our Features</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div class="bg-white rounded-lg shadow-lg overflow-hidden transform transition-transform duration-500 hover:scale-105 max-w-sm mx-auto">
                <div class="p-6">
                    <h3 class="text-3xl font-bold mb-2 text-green-900">Community Insights</h3>
                    <p class="text-lg text-green-800">Explore real-time data on city resources, traffic patterns, and community events.</p>
                </div>
            </div>
            <div class="bg-white rounded-lg shadow-lg overflow-hidden transform transition-transform duration-500 hover:scale-105 max-w-sm mx-auto">
                <div class="p-6">
                    <h3 class="text-3xl font-bold mb-2 text-green-900">Interactive Maps</h3>
                    <p class="text-lg text-green-800">Navigate Poway through dynamic, interactive maps that provide valuable insights.</p>
                </div>
            </div>
            <div class="bg-white rounded-lg shadow-lg overflow-hidden transform transition-transform duration-500 hover:scale-105 max-w-sm mx-auto">
                <div class="p-6">
                    <h3 class="text-3xl font-bold mb-2 text-green-900">Event Calendar</h3>
                    <p class="text-lg text-green-800">Stay up-to-date with upcoming community events and city council meetings.</p>
                </div>
            </div>
        </div>
    </section>
    <script>
        document.addEventListener("DOMContentLoaded", function() {
            const loadingScreen = document.getElementById('loading-screen');
            window.addEventListener('load', function() {
                loadingScreen.style.display = 'none';
            });
            // Typewriter effect for the welcome message
            const text = "Welcome to Poway City";
            const typewriterElement = document.querySelector(".typewriter");
            let index = 0;
            function type() {
                if (index < text.length) {
                    const span = document.createElement('span');
                    span.textContent = text.charAt(index);
                    span.classList.add('text');
                    typewriterElement.appendChild(span);
                    setTimeout(() => {
                        span.style.opacity = 1;
                    }, 50 * index);
                    index++;
                    setTimeout(type, 80);
                }
            }
            type();
            // Fade in effect
            const fadeInElements = document.querySelectorAll('.fade-in');
            window.addEventListener('scroll', function() {
                fadeInElements.forEach(function(element) {
                    if (element.getBoundingClientRect().top < window.innerHeight) {
                        element.classList.add('visible');
                    }
                });
            });
        });
    </script>
</body>
</html>
