<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AI-Driven Quality Control Dashboard</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f6f8;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #2c3e50;
      color: white;
      padding: 20px;
      text-align: center;
    }
    .container {
      padding: 20px;
    }
    .card {
      background: white;
      border-radius: 8px;
      padding: 20px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      margin-bottom: 20px;
    }
    .sensor {
      font-size: 18px;
      margin-bottom: 10px;
    }
    .status {
      font-weight: bold;
    }
    .green { color: green; }
    .red { color: red; }
    button {
      padding: 10px 15px;
      margin-top: 10px;
      background-color: #3498db;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
    button:hover {
      background-color: #2980b9;
    }
  </style>
</head>
<body>

<header>
  <h1>AI-Driven Quality Control in Manufacturing</h1>
</header>

<div class="container">

  <div class="card">
    <h2>Real-Time Sensor Data</h2>
    <p class="sensor">Temperature: <span id="temp">--</span> °C</p>
    <p class="sensor">Vibration: <span id="vibration">--</span> mm/s</p>
    <p class="sensor">Surface Quality Index: <span id="surface">--</span></p>
    <button onclick="simulateData()">Simulate Sensor Data</button>
  </div>

  <div class="card">
    <h2>AI Analysis</h2>
    <p>Status: <span id="aiStatus" class="status">Awaiting Data...</span></p>
  </div>

</div>

<script>
  function simulateData() {
    const temp = (Math.random() * 10 + 30).toFixed(2); // 30-40°C
    const vibration = (Math.random() * 5).toFixed(2);  // 0-5 mm/s
    const surface = (Math.random() * 100).toFixed(0);  // 0-100 score

    document.getElementById("temp").textContent = temp;
    document.getElementById("vibration").textContent = vibration;
    document.getElementById("surface").textContent = surface;

    analyzeData(temp, vibration, surface);
  }

  function analyzeData(temp, vibration, surface) {
    let issues = [];

    if (temp > 38) issues.push("Overheating detected");
    if (vibration > 3) issues.push("Abnormal vibration");
    if (surface < 60) issues.push("Poor surface quality");

    const statusElement = document.getElementById("aiStatus");
    if (issues.length > 0) {
      statusElement.innerHTML = issues.join(", ");
      statusElement.className = "status red";
    } else {
      statusElement.innerHTML = "All systems normal.";
      statusElement.className = "status green";
    }
  }
</script>

</body>
</html>
