<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Botão Fujão - Vai pro Rio Comigo?</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-image: url('https://s5.static.brasilescola.uol.com.br/be/2021/05/cristo-redentor.jpg'); /* URL da imagem do Rio de Janeiro */
            background-size: cover;
            background-position: center;
            font-family: Arial, sans-serif;
            overflow: hidden; /* Esconde qualquer overflow da página */
            position: relative;
            color: white; /* Muda a cor do texto para branco */
            margin: 0;
            padding: 0;
        }
        .container {
            text-align: center;
            position: relative; /* Mantém o texto centralizado */
            z-index: 1; /* Garante que o texto fique na frente dos corações */
            background-color: rgba(0, 0, 0, 0.5); /* Fundo semitransparente para destacar o texto */
            padding: 20px;
            border-radius: 10px;
            max-width: 80%; /* Limita a largura do container em telas grandes */
            margin: 0 10px; /* Margem lateral para evitar encostar nas bordas em telas pequenas */
        }
        .button-container {
            margin-top: 20px;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            margin: 5px;
            z-index: 1;
            border: none;
            border-radius: 5px;
            background-color: #007BFF; /* Cor azul para os botões */
            color: white;
        }
        button:hover {
            background-color: #0056b3; /* Cor mais escura no hover */
        }
        #botao-nao {
            position: absolute;
        }
        /* Estilo para os corações */
        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            transform: rotate(-45deg);
            animation: float 5s infinite ease-in-out;
            z-index: 0; /* Coloca os corações atrás do texto */
        }
        .heart::before,
        .heart::after {
            content: "";
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: red;
            border-radius: 50%;
        }
        .heart::before {
            top: -10px;
            left: 0;
        }
        .heart::after {
            left: 10px;
            top: 0;
        }
        @keyframes float {
            0% {
                opacity: 1;
                transform: translateY(0) rotate(-45deg);
            }
            100% {
                opacity: 0;
                transform: translateY(-200px) rotate(-45deg);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>VAI PRO RIO COMIGO?</h1>
        <div class="button-container">
            <button id="botao-sim">SIM</button>
            <button id="botao-nao">NÃO</button>
        </div>
    </div>

    <!-- Script para os corações flutuantes e o botão fujão -->
    <script>
        // Função para criar corações flutuantes
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            document.body.appendChild(heart);
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's';
            setTimeout(() => {
                heart.remove();
            }, 5000);
        }

        // Cria corações continuamente
        setInterval(createHeart, 300);

        // Botão Fujão
        const botaoNao = document.getElementById('botao-nao');

        function moveButton() {
            const containerWidth = window.innerWidth - botaoNao.clientWidth;
            const containerHeight = window.innerHeight - botaoNao.clientHeight;
            const randomX = Math.floor(Math.random() * containerWidth);
            const randomY = Math.floor(Math.random() * containerHeight);
            botaoNao.style.left = randomX + 'px';
            botaoNao.style.top = randomY + 'px';
        }

        // Mover o botão quando o mouse passa por cima ou em toques
        botaoNao.addEventListener('mouseenter', moveButton);
        botaoNao.addEventListener('touchstart', moveButton);

        // Mover o botão quando clicado
        botaoNao.addEventListener('click', moveButton);

        // Botão SIM com mudança de texto
        const botaoSim = document.getElementById('botao-sim');
        botaoSim.addEventListener('click', () => {
            if (botaoSim.innerText === 'SIM') {
                botaoSim.innerText = 'Você tem certeza?';
            } else if (botaoSim.innerText === 'Você tem certeza?') {
                botaoSim.innerText = 'EU ACEITO SER FELIZ COM O VITOR';
            }
        });
    </script>
</body>
</html>
