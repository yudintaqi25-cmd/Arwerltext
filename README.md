<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hadiah Untuk Kalian</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            height: 100vh;
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

        /* Semua halaman */
        .page {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: opacity 1s ease, transform 1s ease;
        }

        /* HALAMAN PERTAMA */
        #page1 {
            opacity: 1;
            transform: scale(1);
        }

        .intro {
            text-align: center;
            color: white;
            animation: muncul 1.5s ease;
        }

        .gift {
            font-size: 100px;
            animation: goyang 1.5s ease-in-out infinite;
            margin-bottom: 25px;
        }

        .intro h1 {
            font-size: clamp(30px, 6vw, 60px);
            text-shadow: 0 0 20px #38bdf8;
        }

        .intro p {
            margin-top: 15px;
            color: #bae6fd;
            font-size: 18px;
        }

        @keyframes goyang {
            0%, 100% {
                transform: rotate(-5deg) translateY(0);
            }

            50% {
                transform: rotate(5deg) translateY(-15px);
            }
        }

        @keyframes muncul {
            from {
                opacity: 0;
                transform: translateY(30px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Tombol buka */
        .button {
            margin-top: 30px;
            padding: 14px 35px;
            border: none;
            border-radius: 30px;
            background: #38bdf8;
            color: #082f49;
            font-size: 17px;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 0 20px rgba(56, 189, 248, 0.6);
            transition: 0.3s;
        }

        .button:hover {
            transform: scale(1.1);
            box-shadow: 0 0 35px #38bdf8;
        }

        /* HALAMAN KEDUA */
        #page2 {
            opacity: 0;
            transform: scale(0.8);
            pointer-events: none;
        }

        .card {
            width: 85%;
            max-width: 850px;
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
            line-height: 1.3;

            text-shadow:
                0 0 10px #38bdf8,
                0 0 30px #38bdf8;

            min-height: 80px;
        }

        #text::after {
            content: "|";
            color: #38bdf8;
            animation: blink 0.7s infinite;
        }

        @keyframes blink {
            50% {
                opacity: 0;
            }
        }

        /* Lingkaran dekorasi */
        .circle {
            position: absolute;
            border-radius: 50%;
            filter: blur(5px);
            opacity: 0.4;
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
    </style>
</head>

<body>

    <!-- Dekorasi -->
    <div class="circle circle1"></div>
    <div class="circle circle2"></div>

    <!-- HALAMAN 1 -->
    <div class="page" id="page1">

        <div class="intro">

            <div class="gift">🎁</div>

            <h1>Saya kasih hadiah nih...</h1>

            <p>Tapi harus dibuka dulu 😏</p>

            <button class="button" onclick="bukaHadiah()">
                🎁 Buka Hadiah
            </button>

        </div>

    </div>


    <!-- HALAMAN 2 -->
    <div class="page" id="page2">

        <div class="card">

            <div class="subtitle">
                💻 PESAN KHUSUS
            </div>

            <h1 id="text"></h1>

        </div>

    </div>


    <script>

        const pesan =
            "Basuki, Fadol, Awin, kapan bisa ngoding?";

        let index = 0;
        let timer;

        function bukaHadiah() {

            // Hilangkan halaman pertama
            document.getElementById("page1").style.opacity = "0";
            document.getElementById("page1").style.transform =
                "scale(1.3)";

            // Tampilkan halaman kedua
            setTimeout(() => {

                document.getElementById("page1").style.display = "none";

                const page2 =
                    document.getElementById("page2");

                page2.style.opacity = "1";
                page2.style.transform = "scale(1)";

                // Mulai mengetik setelah halaman muncul
                setTimeout(ketik, 700);

            }, 1000);
        }


        function ketik() {

            const text =
                document.getElementById("text");

            if (index < pesan.length) {

                text.innerHTML +=
                    pesan.charAt(index);

                index++;

                timer =
                    setTimeout(ketik, 100);

            }

        }

    </script>

</body>
</html>
