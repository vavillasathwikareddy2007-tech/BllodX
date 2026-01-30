# BllodX
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BloodX Donor Eligibility</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f7f7f7;
      padding: 20px;
    }
    h3 {
      color: #d32f2f;
    }
    form {
      background: white;
      padding: 20px;
      border-radius: 10px;
      max-width: 500px;
      margin: auto;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    label {
      display: block;
      margin-top: 10px;
      font-weight: bold;
    }
    select, input {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      margin-top: 15px;
      padding: 10px 20px;
      background-color: #d32f2f;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
    }
    button:hover {
      background-color: #b71c1c;
    }
    #result {
      margin-top: 15px;
      font-size: 1.1em;
      font-weight: bold;
    }
    .note {
      font-size: 0.9em;
      color: #555;
      margin-top: 10px;
    }
  </style>
</head>
<body>

<form id="healthForm">
  <h3>Confidential Donor Eligibility Check</h3>

  <label>Have you donated blood in the last 3 months?</label>
  <select id="recentDonation">
    <option>No</option>
    <option>Yes</option>
  </select>

  <label>Do you have diabetes?</label>
  <select id="diabetes">
    <option>No</option>
    <option>Yes</option>
  </select>

  <label>Are you HIV positive?</label>
  <select id="hiv">
    <option>Prefer not to say</option>
    <option>No</option>
    <option>Yes</option>
  </select>

  <label>Recent surgery?</label>
  <select id="surgery">
    <option>No</option>
    <option>Yes</option>
  </select>

  <label>Hemoglobin level (optional)</label>
  <input type="number" id="hb" placeholder="e.g. 13.5">

  <label>Borderline hemoglobin?</label>
  <select id="borderlineHb">
    <option>Not sure</option>
    <option>No</option>
    <option>Yes</option>
  </select>

  <button type="button" onclick="checkEligibility()">Check Eligibility</button>

  <p class="note">
    🔒 All health data is confidential and used only to guide donation eligibility. Final approval is done by medical professionals.
  </p>
</form>

<p id="result"></p>

<script>
function checkEligibility() {
  const recentDonation = document.getElementById("recentDonation").value;
  const diabetes = document.getElementById("diabetes").value;
  const hiv = document.getElementById("hiv").value;
  const surgery = document.getElementById("surgery").value;
  const borderlineHb = document.getElementById("borderlineHb").value;

  let result = "";

  if (hiv === "Yes") {
    result = "❌ You are not eligible to donate at this time. Please consult a blood bank.";
  } 
  else if (recentDonation === "Yes" || surgery === "Yes") {
    result = "⏳ You are temporarily not eligible. Please try again later.";
  } 
  else if (diabetes === "Yes" || borderlineHb === "Yes") {
    result = "⚠️ Donation requires hospital verification. Please visit the nearest blood bank.";
  } 
  else {
    result = "✅ You are eligible to donate blood. Thank you for saving lives!";
  }

  document.getElementById("result").innerText = result;
}
</script>

</body>
</html>
