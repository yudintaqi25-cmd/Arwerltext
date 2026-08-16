<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kapan Ngoding?</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            font-family: Arial, sans-serif;
            background: linear-gradient(-45deg, #0f172a, #1e1b4b, #0c4a6e, #111827);
            background-size: 400% 400%;
            animation: backgroundMove 10s ease infinite;
        }

        @keyframes backgroundMove {
            0% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
            100% {
                background-position: 0% 50%;
            }
        }

        /* Lingkaran dekorasi */
        .circle {
            position: absolute;
            border-radius: 50%;
            filter: blur(2px);
            opacity: 0.5;
            animation: float 6s ease-in-out infinite;
        }

        .circle1 {
            width: 200px;
            height: 200px;
            background: #38bdf8;
            top: 10%;
            left: 10%;
        }

        .circle2 {
            width: 250px;
            height: 250px;
            background: #a855f7;
            bottom: 5%;
            right: 10%;
            animation-delay: 2s;
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-30px);
            }
        }

        /* Kotak utama */
        .card {
            position: relative;
            z-index: 2;
            width: 85%;
            max-width: 800px;
            padding: 60px 40px;
            text-align: center;

            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 25px;

            backdrop-filter: blur(15px);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4);
        }

        .subtitle {
            color: #bae6fd;
            font-size: 18px;
            margin-bottom: 25px;
            letter-spacing: 3px;
        }

        #text {
            color: white;
            font-size: clamp(30px, 5vw, 55px);
            font-weight: bold;
            text-shadow:
                0 0 10px #38bdf8,
                0 0 30px #38bdf8;

            min-height: 80px;
        }

        /* Cursor mengetik */
        #text::after {
            content: "|";
            animation: blink 0.7s infinite;
            color: #38bdf8;
        }

        @keyframes blink {
            50% {
                opacity: 0;
            }
        }

        .button {
            margin-top: 35px;
            padding: 12px 30px;
            border: none;
            border-radius: 30px;
            background: #38bdf8;
            color: #082f49;
            font-weight: bold;
            font-size: 16px;
            cursor: pointer;
            transition: 0.3s;
        }

        .button:hover {
            transform: scale(1.08);
            box-shadow: 0 0 25px #38bdf8;
        }
    </style>
</head>

<body>

    <div class="circle circle1"></div>
    <div class="circle circle2"></div>

    <div class="card">
        <div class="subtitle">💻 CODING TIME</div>

        <h1 id="text"></h1>

        <button class="button" onclick="ulang()">🔄 Ulangi</button>
    </div>

    <script>
        const pesan = "Basuki, Fadol, Awin, kapan bisa ngoding?";
        let index = 0;
        let timer;

        function ketik() {
            const text = document.getElementById("text");

            if (index < pesan.length) {
                text.innerHTML += pesan.charAt(index);
                index++;

                timer = setTimeout(ketik, 100);
            }
        }

        function ulang() {
            clearTimeout(timer);

            document.getElementById("text").innerHTML = "";
            index = 0;

            setTimeout(ketik, 300);
        }

        // Mulai otomatis
        ketik();
    </script>

</body>
</html>
