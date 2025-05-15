<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Target Jamaah Umrah</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: #001f3f;
      color: #ffffff;
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      text-align: center;
    }

    h1 {
      font-size: 4rem;
      margin-bottom: 0.5em;
    }

    .stat {
      font-size: 2.5rem;
      margin: 0.3em 0;
    }

    .highlight {
      color: #00d4ff;
      font-weight: bold;
    }

    .footer {
      position: absolute;
      bottom: 20px;
      font-size: 1.2rem;
      color: #cccccc;
    }
  </style>
</head>
<body>
  <h1>🎯 Target Jamaah Umrah</h1>
  <div class="stat">Target: <span class="highlight" id="target">0</span> Jamaah</div>
  <div class="stat">Sudah Daftar: <span class="highlight" id="terdaftar">0</span></div>
  <div class="stat">Sisa: <span class="highlight" id="sisa">0</span> Jamaah Lagi</div>

  <div class="footer">💫 Bismillah, semoga dimudahkan dan dilancarkan semua prosesnya 💫</div>

  <script>
    async function loadData() {
      try {
        const response = await fetch("https://docs.google.com/spreadsheets/d/e/2PACX-1vTfKna9v3cT_XHOrwF-sPcIhb75LEjRKywbnaSAjb1LMBxNX394RYEkfQBl7hZ3o9MvABfZ1-VElQ6L/pub?output=csv");
        const text = await response.text();
        const rows = text.trim().split('\n');
        const data = rows[1].split(',');
        const target = parseInt(data[0]);
        const terdaftar = parseInt(data[1]);
        const sisa = target - terdaftar;

        document.getElementById('target').textContent = target;
        document.getElementById('terdaftar').textContent = terdaftar;
        document.getElementById('sisa').textContent = sisa;
      } catch (error) {
        console.error('Gagal ambil data:', error);
      }
    }

    loadData();
    setInterval(loadData, 10000); // Update setiap 10 detik
  </script>
</body>
</html>
