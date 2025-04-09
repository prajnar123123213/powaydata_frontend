---
layout: weather
title: Disaster predict
search_exclude: true
permalink: /weather/
---

<div class="wrapper">
        <div class="container">
            <h1>San Diego Disaster Survival Prediction</h1>
            <p class="description">Fill in the details below to predict the survival chances based on San Diego disaster data.</p>
            <!-- Disaster Prediction Form -->
            <form id="disasterForm" class="form-container">
            <label for="disaster_type">Disaster Type:</label>
                <select id="disaster_type" required>
                    <option value="earthquake">Earthquake</option>
                    <option value="fire">Fire</option>
                    <option value="tsunami">Tsunami</option>
                </select>
                <label for="magnitude_or_intensity">Magnitude / Intensity (e.g., 7.2 for earthquake):</label>
                <input type="number" id="magnitude_or_intensity" required>
                <label for="distance_to_disaster">Distance to Disaster (in miles):</label>
                <input type="number" id="distance_to_disaster" required>
                <label for="alert_time">Time Alerted Before Event (in hours):</label>
                <input type="number" id="alert_time" required>
                <label for="evacuation_available">Evacuation Available (0 for No, 1 for Yes):</label>
                <input type="number" id="evacuation_available" min="0" max="1" required>
                <label for="shelter_nearby">Shelter Nearby (0 for No, 1 for Yes):</label>
                <input type="number" id="shelter_nearby" min="0" max="1" required>
                <button type="submit" class="submit-btn">Predict Survival</button>
            </form>
            <!-- Prediction Result -->
            <div id="resultContainer" class="result-container">
                <h2>Prediction Result:</h2>
                <p id="result" class="result-text">Please enter disaster details to see the prediction.</p>
            </div>
            <footer>
                <p>Powered by Totally Real Scientists :)</p>
            </footer>
        </div>
    </div>
<script>
        document.getElementById('disasterForm').addEventListener('submit', function (event) {
            event.preventDefault();
            // Collect data from the form
            const data = {
                disaster_type: document.getElementById('disaster_type').value,
                magnitude_or_intensity: parseFloat(document.getElementById('magnitude_or_intensity').value),
                distance_to_disaster: parseFloat(document.getElementById('distance_to_disaster').value),
                alert_time: parseInt(document.getElementById('alert_time').value),
                evacuation_available: parseInt(document.getElementById('evacuation_available').value),
                shelter_nearby: parseInt(document.getElementById('shelter_nearby').value)
            };
            // Show loading message
            document.getElementById('result').innerText = "Predicting... Please wait.";
            // Send data to the API
            fetch('http://127.0.0.1:8887/api/disaster/predict', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(data)
            })
                .then(response => response.json())
                .then(result => {
                    // Display the prediction result
                    const survivalProb = result.survive * 100;
                    const deathProb = result.die * 100;
                    document.getElementById('result').innerHTML = `
                        <strong>Survival Probability:</strong> ${survivalProb.toFixed(2)}%<br>
                        <strong>Death Probability:</strong> ${deathProb.toFixed(2)}%
                    `;
                })
                .catch(error => {
                    console.error('Error:', error);
                    document.getElementById('result').innerText = 'There was an error processing your request. Please try again later.';
                });
        });
</script>

