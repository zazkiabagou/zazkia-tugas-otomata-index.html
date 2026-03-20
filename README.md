<html lang="id">
<head>
<meta charset="UTF-8">
<title>Scientific Notation Scanner</title>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Segoe UI', sans-serif;
}

body {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #000000, #1a0000, #330000);
  color: white;
}

/* CONTAINER */
.container {
  display: flex;
  gap: 50px;
  width: 90%;
  max-width: 1100px;
}

/* LEFT SIDE */
.left {
  flex: 1;
}

.left h1 {
  font-size: 40px;
}

.left span {
  color: red;
  text-shadow: 0 0 10px red;
}

.left p {
  margin-top: 10px;
  opacity: 0.7;
}

/* FORMAT BOX */
.format-box {
  margin-top: 30px;
  padding: 20px;
  border-radius: 15px;
  background: rgba(255,0,0,0.08);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255,0,0,0.3);
}

.format-box code {
  color: #ff4d4d;
  font-size: 18px;
}

/* RIGHT CARD */
.card {
  flex: 1;
  padding: 30px;
  border-radius: 20px;
  background: rgba(255,0,0,0.08);
  backdrop-filter: blur(15px);
  box-shadow: 0 0 25px rgba(255,0,0,0.6);
  text-align: center;
}

/* INPUT */
input {
  width: 100%;
  padding: 12px;
  border-radius: 10px;
  border: 1px solid red;
  outline: none;
  background: black;
  color: white;
  margin-bottom: 15px;
}

/* BUTTON */
button {
  width: 100%;
  padding: 12px;
  border-radius: 10px;
  border: none;
  background: linear-gradient(90deg, red, darkred);
  color: white;
  font-weight: bold;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  box-shadow: 0 0 15px red;
}

/* RESULT BOX */
.result-box {
  margin-top: 20px;
  display: flex;
  gap: 10px;
}

/* VALID / INVALID */
.box {
  flex: 1;
  padding: 15px;
  border-radius: 12px;
  font-size: 14px;
}

.valid {
  background: rgba(0,255,100,0.1);
  border: 1px solid #00ff88;
  color: #00ff88;
}

.invalid {
  background: rgba(255,0,0,0.15);
  border: 1px solid red;
  color: #ff4d4d;
}
</style>
</head>

<body>

<div class="container">

  <!-- LEFT -->
  <div class="left">
    <h1>Scientific Notation <br><span>Scanner</span></h1>
    <p>Validasi format notasi ilmiah secara instan.</p>

    <div class="format-box">
      <p>Format yang diterima:</p>
      <code>a × 10^n</code>
      <ul>
        <li>a = angka desimal</li>
        <li>n = bilangan bulat</li>
      </ul>
    </div>
  </div>

  <!-- RIGHT -->
  <div class="card">
    <input type="text" id="inputNumber" placeholder="Contoh: 3 x 10^2 / 4.5e-3">
    <button onclick="scan()">SCAN NOTASI</button>

    <div class="result-box">
      <div class="box valid" id="validBox">✔ Valid: -</div>
      <div class="box invalid" id="invalidBox">✖ Tidak Valid: -</div>
    </div>
  </div>

</div>

<script>
function scan() {
  let input = document.getElementById("inputNumber").value.trim();

  let regex1 = /^[+-]?(\d+(\.\d+)?)\s*x\s*10\^[-+]?\d+$/i;
  let regex2 = /^[+-]?\d+(\.\d+)?e[-+]?\d+$/i;

  let validBox = document.getElementById("validBox");
  let invalidBox = document.getElementById("invalidBox");

  if (regex1.test(input) || regex2.test(input)) {
    validBox.innerHTML = "✔ Valid: " + input;
    invalidBox.innerHTML = "✖ Tidak Valid: -";
  } else {
    validBox.innerHTML = "✔ Valid: -";
    invalidBox.innerHTML = "✖ Tidak Valid: " + input;
  }
}
</script>

</body>
</html>
