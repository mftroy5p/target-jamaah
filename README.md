<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Target Jamaah Umrah</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: #001f3f;
      color: #ffffff;
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      text-align: center;
    }

    h1 {
      font-size: 2.5rem;
      margin-bottom: 0.5rem;
      color: #66b3ff;
    }

    hr {
      width: 80%;
      margin: 10px auto 30px;
      border: 1px solid #ccc;
    }

    .stat {
      font-size: 2rem;
      margin: 0.6em 0;
    }

    .highlight {
      background-color: #00d4ff;
      color: #001f3f;
      padding: 0.2em 0.5em;
      border-radius: 6px;
      font-weight: bold;
    }

    .footer {
      margin-top: 3rem;
      font-size: 1.1rem;
      color: #cccccc;
    }
  </style>
</head>
<body>
  <h1>🎯 Target Jamaah Umrah</h1>
  <hr />
  <div class="stat">Target: <span class="highlight" id="target">1000</span> Jamaah</div>
  <div class="stat">Sudah Daftar: <span class="highlight" id="terdaftar">20</span></div>
  <div class="stat">Sisa: <span class="highlight" id="sisa">980</span> Jamaah Lagi</div>
  <div class="footer">🕊️ Bismillah, semoga dimudahkan dan dilancarkan semua prosesnya 🕊️</div>

  <script>
    async function loadData() {
      try {
        const response = await fetch("https://docs.google.com/spreadsheets/d/e/2PACX-1vTfKna9v3cT_XHOrwF-sPcIhb75LEjRKywbnaSAjb1LMBxNX394RYEkfQBl7hZ3o9MvABfZ1-VElQ6L/pub?output=csv");
        const csv = await response.text();
        const rows = csv.split("\n");
        const data = rows[1].split(",");
        
        const target = parseInt(data[0]);
        const terdaftar = parseInt(data[1]);
        const sisa = target - terdaftar;

        document.getElementById("target").textContent = target;
        document.getElementById("terdaftar").textContent = terdaftar;
        document.getElementById("sisa").textContent = sisa;
      } catch (error) {
        console.error("Gagal memuat data:", error);
      }
    }

    loadData();
    setInterval(loadData, 50); // update setiap 5 mili detik
  </script>
</body>
</html>
