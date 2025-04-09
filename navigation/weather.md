---
layout: tailwind
title: Disaster predict
search_exclude: true
permalink: /disaster/
---

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Disaster Survival Prediction</title>
    <link rel="stylesheet" href="styles.css">
</head>

<body>
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
            </select><br><br>

            <label for="magnitude_or_intensity">Magnitude / Intensity (e.g., 7.2 for earthquake):</label>
            <input type="number" id="magnitude_or_intensity" required><br><br>

            <label for="distance_to_disaster">Distance to Disaster (in miles):</label>
            <input type="number" id="distance_to_disaster" required><br><br>

            <label for="alert_time">Time Alerted Before Event (in hours):</label>
            <input type="number" id="alert_time" required><br><br>

            <label for="evacuation_available">Evacuation Available (0 for No, 1 for Yes):</label>
            <input type="number" id="evacuation_available" min="0" max="1" required><br><br>

            <label for="shelter_nearby">Shelter Nearby (0 for No, 1 for Yes):</label>
            <input type="number" id="shelter_nearby" min="0" max="1" required><br><br>

            <button type="submit" class="submit-btn">Predict Survival</button>
        </form>

        <!-- Prediction Result -->
        <div id="resultContainer" class="result-container">
            <h2>Prediction Result:</h2>
            <p id="result" class="result-text">Please enter disaster details to see the prediction.</p>
        </div>

        <footer>
            <p>Powered by Disaster Survival Prediction API</p>
        </footer>
    </div>

    <script src="script.js"></script>
</body>

</html>

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f4f7fa;
    color: #333;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    padding: 20px;
}

.container {
    background-color: #fff;
    padding: 30px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 600px;
}

h1 {
    font-size: 24px;
    margin-bottom: 10px;
}

.description {
    font-size: 14px;
    margin-bottom: 20px;
    color: #666;
}

.form-container {
    display: flex;
    flex-direction: column;
}

label {
    font-size: 14px;
    margin-bottom: 5px;
}

input, select {
    padding: 8px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 14px;
}

button.submit-btn {
    padding: 10px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s;
}

button.submit-btn:hover {
    background-color: #45a049;
}

.result-container {
    margin-top: 30px;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 4px;
    background-color: #f9f9f9;
}

.result-text {
    font-size: 16px;
    color: #333;
}

footer {
    text-align: center;
    margin-top: 30px;
    font-size: 12px;
    color: #777;
}

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
    fetch('http://127.0.0.1:5000/api/disaster/predict', {
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