<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Jhoyssili, Com Todo Meu Amor</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Montserrat:wght@300;400;600&display=swap');
        
        :root {
            --primary: #ff6b81;
            --secondary: #ff8e8e;
            --dark: #333;
            --light: #fff9f9;
        }
        
        body {
            font-family: 'Montserrat', sans-serif;
            margin: 0;
            padding: 0;
            background-color: var(--light);
            color: var(--dark);
            line-height: 1.6;
            min-height: 100vh;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            text-align: center;
            padding: 4rem 1rem;
            position: relative;
            overflow: hidden;
        }
        
        h1 {
            font-family: 'Dancing Script', cursive;
            font-size: 3rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }
        
        .subtitle {
            font-size: 1.5rem;
            font-style: italic;
            opacity: 0.9;
        }
        
        .container {
            max-width: 1000px;
            margin: 2rem auto;
            padding: 0 1rem;
            display: none; /* Escondido inicialmente */
        }
        
        .envelope {
            width: 100%;
            max-width: 600px;
            margin: 2rem auto;
            position: relative;
            perspective: 1000px;
            cursor: pointer;
        }
        
        .envelope-front {
            width: 100%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 8px;
            padding: 3rem 2rem;
            text-align: center;
            box-shadow: 0 10px 30px rgba(255, 107, 129, 0.3);
            transform-style: preserve-3d;
            transform-origin: bottom;
            transition: all 1s ease;
            position: relative;
            z-index: 2;
        }
        
        .envelope.open .envelope-front {
            transform: rotateX(180deg);
            opacity: 0;
        }
        
        .btn-open {
            background-color: white;
            color: var(--primary);
            border: none;
            padding: 0.8rem 2rem;
            font-size: 1.2rem;
            border-radius: 50px;
            margin-top: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 600;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .btn-open:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(0,0,0,0.15);
        }
        
        .memory {
            background: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            padding: 2rem;
            margin-bottom: 2rem;
            display: flex;
            flex-direction: column;
            align-items: center;
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.8s ease;
        }
        
        .show .memory {
            opacity: 1;
            transform: translateY(0);
        }
        
        .memory:nth-child(1) { transition-delay: 0.2s; }
        .memory:nth-child(2) { transition-delay: 0.4s; }
        .memory:nth-child(3) { transition-delay: 0.6s; }
        .memory:nth-child(4) { transition-delay: 0.8s; }
        .memory:nth-child(5) { transition-delay: 1s; }
        
        .memory img {
            max-width: 100%;
            border-radius: 8px;
            margin-bottom: 1rem;
            box-shadow: 0 3px 10px rgba(0,0,0,0.2);
        }
        
        .memory h2 {
            color: var(--primary);
            text-align: center;
            font-family: 'Dancing Script', cursive;
        }
        
        footer {
            text-align: center;
            padding: 2rem;
            background: var(--dark);
            color: white;
        }
        
        .heart {
            color: var(--primary);
            font-size: 1.5rem;
            animation: pulse 1.5s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.3); }
            100% { transform: scale(1); }
        }
        
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1rem;
            margin-top: 1rem;
        }
        
        .gallery img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 8px;
            transition: transform 0.3s;
        }
        
        .gallery img:hover {
            transform: scale(1.05);
        }
        
        .hearts {
            position: fixed;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
            overflow: hidden;
        }
        
        .heart-bg {
            position: absolute;
            font-size: 1.5rem;
            color: rgba(255, 107, 129, 0.5);
            animation: float 5s linear infinite;
            opacity: 0;
        }
        
        @keyframes float {
            0% {
                transform: translateY(0) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) rotate(360deg);
                opacity: 0;
            }
        }
        
        .music-control {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: white;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 3px 10px rgba(0,0,0,0.2);
            cursor: pointer;
            z-index: 100;
        }
        
        .music-control i {
            color: var(--primary);
            font-size: 1.5rem;
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
</head>
<body>
    <div class="hearts" id="hearts"></div>
    
    <audio id="bgMusic" loop>
        <!-- Substitua pelo seu arquivo de música -->
        <source src="msc/Stephen Sanchez, Em Beihold - Until I Found You (Lyrics) - 192.mp3" type="audio/mpeg">
        Seu navegador não suporta áudio HTML5.
    </audio>
    
    <div class="music-control" id="musicControl">
        <i class="fas fa-music"></i>
    </div>
    
    <div class="envelope" id="envelope">
        <div class="envelope-front">
            <h1>Para Jhoyssili</h1>
            <p class="subtitle">Clique abaixo para abrir minha carta de amor</p>
            <button class="btn-open" id="btnOpen">
                Abrir Carta do Seu Amor <i class="fas fa-heart"></i>
            </button>
        </div>
    </div>
    
    <div class="container" id="mainContent">
        <section class="memory">
            <h2>Por que você é especial</h2>
            <p>Você é especial porque traz luz aos meus dias simples e transforma momentos comuns em memórias inesquecíveis. Seu sorriso é meu lugar favorito, seu abraço é meu porto seguro, e sua voz é a melodia que acalma minha alma.
Você me ensinou que o amor não é só sentir, mas escolher todos os dias estar presente, cuidar, entender e celebrar até os pequenos detalhes. Com você, aprendi que a vida fica mais bonita quando compartilhada, e que os desafios ficam mais leves quando enfrentados juntos.</p>
        </section>
        
        <section class="memory">
            <h2>Nossa História</h2>
            <p>Lembro do dia em que sua amiga veio até mim pedir meu número. Achei curioso, pois ainda não te conhecia. Quando nos vimos na ETEC, fiquei tão nervoso que você teve que falar primeiro. Nosso primeiro encontro foi mágico - você era tão adorável e atenciosa que eu já sabia que era especial. E aquele primeiro beijo? Foi perfeito!</p>
            <img src="img/beijo.jpeg" alt="Nós dois juntos" style="max-height: 400px;">
        </section>
        
        <section class="memory">
            <h2>Memórias Felizes</h2>
            <p>Lembro perfeitamente daquele dia em que sua amiga veio até mim pedir meu número para você. Confesso que achei estranho, pois ainda não te conhecia, mas algo me disse que valeria a pena descobrir quem era você.

Quando nos encontramos pela primeira vez na ETEC, fiquei tão nervoso que nem conseguia falar direito foi você quem teve a coragem de puxar assunto, e eu só agradeço por isso. Depois, quando saímos, tudo mudou. Aquele dia foi mágico: descobri uma pessoa incrivelmente adorável, atenciosa e cheia de luz. E, quando rolou nosso primeiro beijo, meu coração disparou de felicidade. Eu sabia, naquele momento, que você era alguém especial.

Nos meses seguintes, cada saída, cada risada, cada conversa no telefone até tarde só confirmou o que eu já sentia. Até que, um dia, tomei coragem e pedi sua mão em namoro. Quando você disse "sim", foi uma das melhores sensações da minha vida.

Hoje, olhando para trás, só tenho gratidão por cada segundo ao seu lado. Obrigado por me amar, por me entender e por fazer da minha vida uma história mais bonita. Eu te amo mais do que as palavras podem dizer. ❤️</p>
            
            <div class="gallery">
                <img src="img/pato2.jpeg" alt="Memória 1">
                <img src="img/pato.jpeg" alt="Memória 2">
                <img src="img/Show.jpeg" alt="Memória 3">
                <img src="img/Circo.jpeg" alt="Memória 4">
            </div>
        </section>
        
        <section class="memory">
            <h2>Minhas Promessas Para Você</h2>
            <p>
                1. Prometo te amar incondicionalmente, nos dias bons e ruins<br>
                2. Prometo ser seu porto seguro sempre que precisar<br>
                3. Prometo cultivar nossa paixão e nunca deixar o amor virar rotina<br>
                4. Prometo apoiar seus sonhos como você apoia os meus<br>
                5. Prometo lembrar sempre daquele primeiro beijo e manter a magia viva
            </p>
        </section>
        
        <section class="memory">
            <h2>Mensagem Final</h2>
            <p>Se eu pudesse resumir o que sinto em uma só palavra, ela seria "gratidão" gratidão por cada olhar, cada risada, cada momento em que você me mostrou que o amor pode ser tão simples e, ao mesmo tempo, tão grandioso.

Você chegou na minha vida de um jeito inesperado, mas hoje sei que nada foi por acaso. Desde aquele primeiro beijo até os nossos planos mais secretos, cada dia ao seu lado me ensinou que o amor verdadeiro não é só paixão: é parceria, é cumplicidade, é encontrar no outro o lar que a gente nem sabia que procurava.

Você é minha paz no caos, minha alegria nos dias cinzentos, a pessoa que me faz acreditar que o mundo pode ser melhor só porque existe. Não importa o que o futuro traga, eu quero enfrentar tudo com você de mãos dadas, como sempre fizemos.

Obrigado por ser quem você é. Obrigado por me escolher todos os dias. Obrigado por esse amor que não cabe em palavras, mas que eu tento mostrar em cada "bom dia", em cada abraço, em cada "te amo" sussurrado no seu ouvido.

Eu te amo hoje mais do que ontem, mas menos do que amanhã. E prometo continuar provando isso até o último dos nossos "para sempre".

De 💖 Gabriel</p>
        </section>
    </div>
    
    <footer>
        <p>Feito com <span class="heart">♥</span> por Gabriel em <span id="currentDate"></span></p>
    </footer>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const envelope = document.getElementById('envelope');
            const btnOpen = document.getElementById('btnOpen');
            const mainContent = document.getElementById('mainContent');
            const heartsContainer = document.getElementById('hearts');
            const currentDate = document.getElementById('currentDate');
            const bgMusic = document.getElementById('bgMusic');
            const musicControl = document.getElementById('musicControl');
            
            // Set current date
            const today = new Date();
            const options = { day: 'numeric', month: 'long', year: 'numeric' };
            currentDate.textContent = today.toLocaleDateString('pt-BR', options);
            
            // Open envelope and reveal content
            btnOpen.addEventListener('click', function() {
                envelope.classList.add('open');
                setTimeout(() => {
                    mainContent.style.display = 'block';
                    setTimeout(() => {
                        mainContent.classList.add('show');
                        createHearts();
                    }, 100);
                }, 1000);
                
                btnOpen.innerHTML = 'Carta Aberta <i class="fas fa-heart"></i>';
                btnOpen.disabled = true;
            });
            
            // Create floating hearts
            function createHearts() {
                for (let i = 0; i < 20; i++) {
                    const heart = document.createElement('div');
                    heart.innerHTML = '<i class="fas fa-heart"></i>';
                    heart.classList.add('heart-bg');
                    
                    const posX = Math.random() * 100;
                    const delay = Math.random() * 5;
                    const duration = 3 + Math.random() * 7;
                    const size = 0.5 + Math.random() * 2;
                    
                    heart.style.left = `${posX}%`;
                    heart.style.animationDelay = `${delay}s`;
                    heart.style.animationDuration = `${duration}s`;
                    heart.style.fontSize = `${size}rem`;
                    
                    heartsContainer.appendChild(heart);
                }
            }
            
            // Music control
            let isMusicPlaying = false;
            musicControl.addEventListener('click', function() {
                if (isMusicPlaying) {
                    bgMusic.pause();
                    musicControl.innerHTML = '<i class="fas fa-music"></i>';
                } else {
                    bgMusic.play();
                    musicControl.innerHTML = '<i class="fas fa-pause"></i>';
                }
                isMusicPlaying = !isMusicPlaying;
            });
            
            // Auto-start music (opcional - pode ser irritante para alguns usuários)
             bgMusic.volume = 0.1;
            // bgMusic.play();
            // isMusicPlaying = true;
            // musicControl.innerHTML = '<i class="fas fa-pause"></i>';
        });
    </script>
</body>
</html>
