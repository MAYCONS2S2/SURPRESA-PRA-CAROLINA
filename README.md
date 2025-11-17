<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Pedido de Namoro</title>

    <style>
        body {
            background: #ffdde6;
            font-family: Arial, sans-serif;
            text-align: center;
            overflow-x: hidden;
        }

        .card {
            background: white;
            max-width: 420px;
            width: 90%;
            margin: 80px auto;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 0 15px rgba(0,0,0,0.2);
            position: relative;
            z-index: 10;
        }

        h2, h3 {
            color: #d6336c;
            margin-bottom: 15px;
        }

        button {
            padding: 15px 25px;
            border: none;
            border-radius: 12px;
            font-size: 20px;
            cursor: pointer;
            margin: 10px;
            transition: 0.2s;
            width: 70%;
            max-width: 250px;
        }

        .sim {
            background: #ff5c8a;
            color: white;
        }

        .nao {
            background: #999;
            color: white;
            position: absolute;
        }

        .music {
            background: #ff0066;
            color: white;
            margin-top: 20px;
        }

        .heart {
            position: fixed;
            color: #ff5c8a;
            animation: fall linear;
        }

        @keyframes fall {
            0% { transform: translateY(-10vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>

<body>

    <div class="card">
        <h2>Sofia...</h2>
        <h3>Eu queria te perguntar algo muito especial 💗</h3>
        <h3>Você aceitaria namorar comigo?</h3>

        <button class="sim" onclick="respostaSim()">Sim 💖</button>
        <button class="nao" id="nao" onclick="fugir()">Não 😢</button>

        <p id="resultado" style="margin-top:20px; font-size:20px; color:#d6336c;"></p>
        <p id="extraMsg" style="margin-top:15px; font-size:18px; color:#c70039;"></p>

        <div id="musicButton"></div>
    </div>

    <script>
        let fugas = 0;

        function fugir() {
            let botao = document.getElementById("nao");

            let maxX = window.innerWidth - botao.offsetWidth - 20;
            let maxY = window.innerHeight - botao.offsetHeight - 20;

            let x = Math.random() * maxX;
            let y = Math.random() * maxY;

            botao.style.left = x + "px";
            botao.style.top = y + "px";

            fugas++;

            // MENSAGEM após 7 fugidas
            if (fugas > 7) {
                document.getElementById("extraMsg").innerHTML =
                    "Nossa, você não quer mesmo… aceita logo 🔪☠😍";
            }
        }

        function respostaSim() {
            document.getElementById("resultado").innerHTML =
                "Eu sabia que você diria sim, Sofia! 💕💍<br>Agora começa a nossa história!";

            // Corações caindo
            setInterval(() => {
                let heart = document.createElement("div");
                heart.innerHTML = "❤";
                heart.classList.add("heart");
                heart.style.left = Math.random() * 100 + "vw";
                heart.style.fontSize = Math.random() * 25 + 15 + "px";
                heart.style.animationDuration = Math.random() * 3 + 2 + "s";
                document.body.appendChild(heart);
                setTimeout(() => heart.remove(), 5000);
            }, 150);

            document.getElementById("musicButton").innerHTML = `
                <button class="music" onclick="musica()">
                    Ouvir nossa música 💞🎶
                </button>
            `;
        }

        function musica() {
            window.open("https://www.youtube.com/watch?v=QDYfEBY9NM4", "_blank");
        }
    </script>

</body>
</html>
