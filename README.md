<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <title>โปรแกรมคำนวณ BMI</title>
  <style>
    body {
      font-family: "Prompt", Tahoma, sans-serif;
      background: linear-gradient(135deg, #fdfcfb, #e2d1c3);
      margin: 0;
      padding: 0;
    }
    header {
      background: #ff6b6b;
      color: white;
      padding: 20px;
      text-align: center;
      font-size: 24px;
      font-weight: bold;
      letter-spacing: 1px;
    }
    .container {
      background: white;
      padding: 30px;
      border-radius: 15px;
      max-width: 420px;
      margin: 40px auto;
      box-shadow: 0 6px 18px rgba(0,0,0,0.15);
      text-align: center;
    }
    h2 {
      margin-bottom: 15px;
      color: #444;
    }
    input {
      padding: 12px;
      margin: 10px 0;
      width: 90%;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 16px;
      box-sizing: border-box;
      outline: none;
      transition: 0.2s;
    }
    input:focus {
      border-color: #ff6b6b;
      box-shadow: 0 0 5px rgba(255,107,107,0.6);
    }
    button {
      padding: 12px 25px;
      margin-top: 15px;
      background: #ff6b6b;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 8px;
      font-size: 16px;
      font-weight: bold;
      transition: 0.3s;
    }
    button:hover {
      background: #e63946;
    }
    #result {
      margin-top: 20px;
      font-size: 18px;
      font-weight: bold;
      padding: 15px;
      border-radius: 10px;
    }
    .underweight { color: #1d3557; background: #a8dadc; }
    .normal { color: #2a9d8f; background: #d4f8e8; }
    .overweight { color: #e9c46a; background: #fff3cd; }
    .obese1 { color: #f77f00; background: #ffe5b4; }
    .obese2 { color: #d62828; background: #ffd6d6; }
    footer {
      text-align: center;
      padding: 15px;
      color: #666;
      font-size: 14px;
    }
  </style>
</head>
<body>
  <header>🌿 โปรแกรมคำนวณ BMI เพื่อสุขภาพ</header>
  <div class="container">
    <h2>กรอกข้อมูลของคุณ</h2>
    <input type="number" id="weight" placeholder="น้ำหนัก (กิโลกรัม)" step="0.1">
    <input type="number" id="height" placeholder="ส่วนสูง (เซนติเมตร)" step="0.1">
    <br>
    <button onclick="calculateBMI()">คำนวณ BMI</button>
    <div id="result"></div>
  </div>
  <footer>
    © 2025 HealthyLife | เว็บไซต์ให้ความรู้ภาวะน้ำหนักเกินและโรคอ้วน
  </footer>

  <script>
    function calculateBMI() {
      let weight = document.getElementById("weight").value;
      let height = document.getElementById("height").value;
      let resultBox = document.getElementById("result");

      if (weight > 0 && height > 0) {
        let heightM = height / 100; // แปลงเป็นเมตร
        let bmi = weight / (heightM * heightM);
        let resultText = "ค่า BMI ของคุณคือ: " + bmi.toFixed(2) + "<br>";
        let category = "";
        let cssClass = "";

        if (bmi < 18.5) {
          category = "อยู่ในเกณฑ์: น้ำหนักน้อย / ผอม";
          cssClass = "underweight";
        } else if (bmi >= 18.5 && bmi < 23) {
          category = "อยู่ในเกณฑ์: น้ำหนักปกติ";
          cssClass = "normal";
        } else if (bmi >= 23 && bmi < 25) {
          category = "อยู่ในเกณฑ์: น้ำหนักเกิน";
          cssClass = "overweight";
        } else if (bmi >= 25 && bmi < 30) {
          category = "อยู่ในเกณฑ์: โรคอ้วนระดับ 1";
          cssClass = "obese1";
        } else {
          category = "อยู่ในเกณฑ์: โรคอ้วนระดับ 2";
          cssClass = "obese2";
        }

        resultBox.className = cssClass;
        resultBox.innerHTML = resultText + category;
      } else {
        resultBox.className = "";
        resultBox.innerHTML = "⚠️ กรุณากรอกข้อมูลให้ครบถ้วน";
      }
    }
  </script>
</body>
</html>
