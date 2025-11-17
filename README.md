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
            overflow: hidden;
            margin: 0;
            padding: 0;
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
            position: relative;
            z-index: 20;
        }

        .nao {
            background: #999;
            color: white;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 20;
        }

        .heart {
            position: fixed;
            color: #ff5c8a;
            font-size: 25px; /* tamanho médio */
            animation: fall linear;
            pointer-events: none;
        }

        @keyframes fall {
            0% { transform: translateY(-50px) rotate(0deg); opacity: 1; }
            100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
        }

        #resultado {
            margin-top: 20px;
            font-size: 20px;
            color: #d6336c;
        }

    </style>
</head>
<body>

    <div class="card">
        <h2>Sofia...</h2>
        <h3>Eu queria te perguntar algo muito especial 💗</h3>
        <h3>Você aceitaria namorar comigo?</h3>

        <button class="sim" id="btnSim">Sim 💖</button>
        <button class="nao" id="btnNao">Não 😢</button>

        <p id="resultado"></p>
    </div>

    <script>
        // ==== Corações caindo contínuos ====
        function criarCoracao() {
            const heart = document.createElement("div");
            heart.classList.add("heart");
            heart.innerHTML = "❤";
            heart.style.left = Math.random() * 100 + "vw";
            heart.style.fontSize = Math.random() * 15 + 20 + "px"; // tamanho médio 20-35px
            heart.style.animationDuration = Math.random() * 3 + 3 + "s"; // 3-6s
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 6000);
        }

        setInterval(criarCoracao, 200); // corações contínuos

        // ==== Botão SIM ====
        document.getElementById("btnSim").addEventListener("click", () => {
            window.open("https://www.tiktok.com/@fernandaphx/video/7367535233597459718", "_blank");
        });

        // ==== Botão NÃO ====
        let cliquesNao = 0;
        const btnNao = document.getElementById("btnNao");

        btnNao.addEventListener("click", () => {
            // Área visível da tela
            const largura = window.innerWidth - btnNao.offsetWidth;
            const altura = window.innerHeight - btnNao.offsetHeight;

            const x = Math.random() * largura;
            const y = Math.random() * altura;

            btnNao.style.left = x + "px";
            btnNao.style.top = y + "px";

            cliquesNao++;
            if (cliquesNao >= 3) {
                document.getElementById("resultado").innerText = "Nossa, você não quer mesmo, aceita logo 🔪☠😍";
            }
        });
    </script>

</body>
</html>
