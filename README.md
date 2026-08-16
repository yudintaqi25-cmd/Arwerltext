<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Efek Teks Ketik</title>
<style>
  body {
    background: #1a1a2e;
    color: #f0f0f0;
    font-family: 'Courier New', monospace;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
  }

  button {
    background: #e94560;
    color: white;
    border: none;
    padding: 12px 28px;
    font-size: 16px;
    border-radius: 6px;
    cursor: pointer;
    margin-bottom: 40px;
  }

  button:hover {
    background: #d63851;
  }

  #output {
    font-size: 22px;
    max-width: 500px;
    text-align: center;
    min-height: 60px;
    white-space: pre-line;
  }

  #cursor {
    display: inline-block;
    width: 2px;
    background: #f0f0f0;
    margin-left: 2px;
    animation: blink 0.8s infinite;
  }

  @keyframes blink {
    0%, 50% { opacity: 1; }
    51%, 100% { opacity: 0; }
  }
</style>
</head>
<body>

  <button onclick="mulaiKetik()">Tampilkan Teks</button>
  <div id="output"></div>

  <script>
    // GANTI BAGIAN INI dengan teksmu, pakai tanda backtick ( ` ) bukan kutip biasa
    const teks = `Teman ku semua pada jahat tante
aku lagi susah mereka ga ada
coba kalau lagi jaya
aku di puja puja nya tante
Sudah terbiasa terjadi tante
Teman datang kalau lagi butuh saja
coba kalau lagi susah
mereka semua menghilang
Teman ku semua pada jahat tante
aku lagi susah mereka gak ada
coba kalau lagi jaya
aku di puja puja nya tante`;

    const output = document.getElementById('output');

    function mulaiKetik() {
      output.innerHTML = "";
      let index = 0;

      function ketikHuruf() {
        if (index < teks.length) {
          output.innerHTML = teks.substring(0, index + 1) + '<span id="cursor">|</span>';
          index++;
          setTimeout(ketikHuruf, 50);
        }
      }

      ketikHuruf();
    }
  </script>

</body>
</html>
