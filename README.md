<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MELOMANIAC - Cyberpunk Neon Style</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Exo 2', 'Orbitron', sans-serif;
        }
        
        :root {
            --neon-purple: #c724f5;
            --neon-pink: #ff2a96;
            --neon-lilac: #b967ff;
            --deep-black: #05001a;
            --electric-purple: #8a2be2;
        }
        
        body {
            background: var(--deep-black);
            color: white;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }
        
        .cyberpunk-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -4;
            background: linear-gradient(45deg, #0a001f 0%, #1a0035 50%, #0f0025 100%);
            overflow: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }
        
        /* Efeitos de partículas e luzes */
        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -2;
        }
        
        .particle {
            position: absolute;
            border-radius: 50%;
            background: var(--neon-purple);
            opacity: 0.6;
            animation: float 15s infinite linear;
        }
        
        .smoke {
            position: absolute;
            width: 200px;
            height: 200px;
            border-radius: 50%;
            filter: blur(30px);
            background: var(--neon-lilac);
            opacity: 0.1;
            animation: smoke 25s infinite alternate;
        }
        
        .energy-beam {
            position: absolute;
            height: 100%;
            width: 2px;
            background: linear-gradient(to bottom, transparent, var(--neon-purple), transparent);
            box-shadow: 0 0 15px 2px var(--neon-purple);
            opacity: 0.3;
            animation: beam 8s infinite linear;
        }
        
        /* Cabeçalho e Navegação */
        header {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-bottom: 40px;
            padding: 20px;
        }
        
        nav {
            width: 100%;
            display: flex;
            justify-content: center;
            margin-bottom: 50px;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 40px;
            background: rgba(0, 0, 0, 0.5);
            padding: 15px 30px;
            border-radius: 30px;
            border: 1px solid rgba(185, 103, 255, 0.3);
            backdrop-filter: blur(5px);
        }
        
        nav a {
            color: white;
            text-decoration: none;
            font-weight: 300;
            font-size: 16px;
            letter-spacing: 1px;
            text-transform: uppercase;
            transition: all 0.3s ease;
            position: relative;
        }
        
        nav a:hover {
            color: var(--neon-lilac);
        }
        
        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 1px;
            background: var(--neon-lilac);
            transition: width 0.3s ease;
        }
        
        nav a:hover::after {
            width: 100%;
        }
        
        /* Logo e Título */
        .logo-container {
            text-align: center;
            margin-bottom: 40px;
        }
        
        .symbol {
            width: 180px;
            height: 180px;
            margin: 0 auto 20px;
            position: relative;
        }
        
        .symbol::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle, var(--neon-purple) 0%, transparent 70%);
            border-radius: 50%;
            animation: pulse 3s infinite alternate;
            z-index: -1;
        }
        
        .symbol-svg {
            width: 100%;
            height: 100%;
            filter: drop-shadow(0 0 10px var(--neon-purple)) drop-shadow(0 0 20px var(--neon-purple));
        }
        
        .title {
            font-family: 'Orbitron', sans-serif;
            font-size: 48px;
            font-weight: 700;
            color: white;
            text-transform: uppercase;
            letter-spacing: 4px;
            margin-bottom: 10px;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.7), 0 0 20px rgba(199, 36, 245, 0.5);
        }
        
        .subtitle {
            font-size: 16px;
            font-weight: 300;
            color: var(--neon-lilac);
            letter-spacing: 3px;
            text-transform: uppercase;
        }
        
        /* Conteúdo Principal */
        .main-content {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .club-sign {
            background: rgba(0, 0, 0, 0.6);
            color: var(--neon-pink);
            font-family: 'Orbitron', sans-serif;
            font-size: 18px;
            padding: 10px 20px;
            border: 1px solid var(--neon-pink);
            border-radius: 5px;
            margin-bottom: 30px;
            text-transform: uppercase;
            letter-spacing: 2px;
            box-shadow: 0 0 10px rgba(255, 42, 150, 0.5);
        }
        
        /* Cubo Holográfico */
        .hologram-cube {
            width: 300px;
            height: 200px;
            perspective: 1000px;
            margin-bottom: 40px;
        }
        
        .cube {
            width: 100%;
            height: 100%;
            position: relative;
            transform-style: preserve-3d;
            animation: rotate 15s infinite linear;
        }
        
        .cube-face {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(199, 36, 245, 0.1), rgba(255, 42, 150, 0.1));
            border: 1px solid rgba(199, 36, 245, 0.5);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            backdrop-filter: blur(5px);
            box-shadow: 0 0 20px rgba(199, 36, 245, 0.3);
        }
        
        .front { transform: translateZ(100px); }
        .back { transform: rotateY(180deg) translateZ(100px); }
        .right { transform: rotateY(90deg) translateZ(150px); }
        .left { transform: rotateY(-90deg) translateZ(150px); }
        .top { transform: rotateX(90deg) translateZ(100px); }
        .bottom { transform: rotateX(-90deg) translateZ(100px); }
        
        .members-count {
            font-family: 'Orbitron', sans-serif;
            font-size: 32px;
            color: white;
            text-shadow: 0 0 10px var(--neon-purple);
            margin-bottom: 10px;
        }
        
        .join-text {
            font-size: 18px;
            color: var(--neon-lilac);
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        
        /* Botões Sociais */
        .social-buttons {
            display: flex;
            gap: 20px;
            margin-bottom: 40px;
        }
        
        .social-icon, .text-button {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid var(--neon-purple);
            color: white;
            font-size: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
        }
        
        .text-button {
            width: auto;
            padding: 0 20px;
            border-radius: 25px;
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .social-icon:hover, .text-button:hover {
            background: rgba(199, 36, 245, 0.2);
            box-shadow: 0 0 15px var(--neon-purple);
            transform: translateY(-3px);
        }
        
        /* Player de Música */
        .music-player {
            width: 100%;
            max-width: 500px;
            background: rgba(10, 0, 20, 0.8);
            border-radius: 15px;
            padding: 20px;
            border: 1px solid rgba(185, 103, 255, 0.3);
            box-shadow: 0 0 20px rgba(199, 36, 245, 0.2);
            backdrop-filter: blur(5px);
        }
        
        .now-playing {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .track-info {
            flex: 1;
        }
        
        .track-name {
            font-size: 18px;
            font-weight: 600;
            color: white;
            margin-bottom: 5px;
        }
        
        .artist {
            font-size: 14px;
            color: var(--neon-lilac);
        }
        
        .heart-icon {
            color: #ccc;
            font-size: 20px;
            cursor: pointer;
            transition: color 0.3s ease;
        }
        
        .heart-icon:hover {
            color: var(--neon-pink);
        }
        
        .player-controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .control-button {
            background: none;
            border: none;
            color: white;
            font-size: 24px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .play-button {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--neon-purple);
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0 0 10px var(--neon-purple);
        }
        
        .control-button:hover {
            color: var(--neon-lilac);
        }
        
        .play-button:hover {
            transform: scale(1.1);
        }
        
        .progress-bar {
            width: 100%;
            height: 4px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 2px;
            margin: 10px 0;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            width: 30%;
            background: linear-gradient(to right, var(--neon-pink), var(--neon-purple));
            border-radius: 2px;
        }
        
        .time {
            display: flex;
            justify-content: space-between;
            font-size: 12px;
            color: rgba(255, 255, 255, 0.7);
        }
        
        /* Painel Lateral */
        .side-panel {
            position: fixed;
            right: 20px;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(5, 0, 15, 0.7);
            border-radius: 15px;
            padding: 20px;
            border: 1px solid rgba(185, 103, 255, 0.3);
            backdrop-filter: blur(5px);
            display: flex;
            flex-direction: column;
            gap: 30px;
            width: 250px;
            z-index: 100;
        }
        
        .profile {
            text-align: center;
        }
        
        .profile-image {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            margin: 0 auto 15px;
            border: 2px solid var(--neon-purple);
            box-shadow: 0 0 15px var(--neon-purple);
            filter: grayscale(100%);
            position: relative;
        }
        
        .profile-image::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(199, 36, 245, 0.1);
            border-radius: 50%;
        }
        
        .profile-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 16px;
            color: var(--neon-purple);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 10px;
        }
        
        .profile-name {
            font-size: 18px;
            color: white;
        }
        
        .quote {
            text-align: center;
            padding: 20px 0;
            border-top: 1px solid rgba(185, 103, 255, 0.2);
        }
        
        .quote-text {
            font-style: italic;
            font-size: 16px;
            color: rgba(255, 255, 255, 0.8);
            margin-bottom: 15px;
            line-height: 1.5;
        }
        
        .signature {
            font-family: 'Orbitron', sans-serif;
            font-size: 14px;
            color: var(--neon-lilac);
        }
        
        /* Rodapé */
        footer {
            text-align: center;
            margin-top: 50px;
            padding: 20px;
            border-top: 1px solid rgba(185, 103, 255, 0.2);
        }
        
        .copyright {
            font-size: 14px;
            color: rgba(255, 255, 255, 0.6);
            margin-bottom: 10px;
        }
        
        .footer-social {
            display: flex;
            justify-content: center;
            gap: 15px;
        }
        
        .footer-social a {
            color: rgba(255, 255, 255, 0.7);
            font-size: 16px;
            transition: color 0.3s ease;
        }
        
        .footer-social a:hover {
            color: var(--neon-purple);
        }
        
        /* Animações */
        @keyframes pulse {
            0% { opacity: 0.5; transform: scale(1); }
            50% { opacity: 0.7; transform: scale(1.05); }
            100% { opacity: 0.5; transform: scale(1); }
        }
        
        @keyframes rotate {
            0% { transform: rotateY(0) rotateX(10deg); }
            100% { transform: rotateY(360deg) rotateX(10deg); }
        }
        
        @keyframes float {
            0% { transform: translateY(0) translateX(0); }
            25% { transform: translateY(-20px) translateX(10px); }
            50% { transform: translateY(-35px) translateX(-10px); }
            75% { transform: translateY(-15px) translateX(15px); }
            100% { transform: translateY(0) translateX(0); }
        }
        
        @keyframes smoke {
            0% { transform: translate(0, 0) scale(1); opacity: 0.1; }
            25% { transform: translate(100px, -100px) scale(1.5); opacity: 0.15; }
            50% { transform: translate(-100px, -200px) scale(2); opacity: 0.2; }
            75% { transform: translate(-200px, -100px) scale(1.5); opacity: 0.15; }
            100% { transform: translate(0, 0) scale(1); opacity: 0.1; }
        }
        
        @keyframes beam {
            0% { transform: translateX(0) rotate(0deg); opacity: 0; }
            10% { opacity: 0.3; }
            50% { opacity: 0.5; }
            90% { opacity: 0.3; }
            100% { transform: translateX(100vw) rotate(5deg); opacity: 0; }
        }
        
        /* Responsividade */
        @media (max-width: 992px) {
            .side-panel {
                position: relative;
                width: 100%;
                right: 0;
                top: 0;
                transform: none;
                margin: 30px 0;
                flex-direction: row;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .profile {
                flex: 1;
                min-width: 150px;
            }
            
            .quote {
                flex-basis: 100%;
            }
        }
        
        @media (max-width: 768px) {
            nav ul {
                gap: 20px;
                padding: 10px 20px;
            }
            
            .title {
                font-size: 36px;
            }
            
            .symbol {
                width: 150px;
                height: 150px;
            }
            
            .hologram-cube {
                width: 250px;
                height: 180px;
            }
        }
        
        @media (max-width: 576px) {
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
                gap: 15px;
            }
            
            .title {
                font-size: 28px;
            }
            
            .subtitle {
                font-size: 14px;
            }
            
            .social-buttons {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .side-panel {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="cyberpunk-bg"></div>
    
    <div class="particles" id="particles"></div>
    
    <div class="container">
        <header>
            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Status</a></li>
                    <li><a href="#">Contact</a></li>
                    <li><a href="#">Exclusive</a></li>
                    <li><a href="#">Notifications</a></li>
                </ul>
            </nav>
            
            <div class="logo-container">
                <div class="symbol">
                    <svg class="symbol-svg" viewBox="0 0 100 100">
                        <path d="M50 15 L65 35 H85 L70 50 L85 65 H65 L50 85 L35 65 H15 L30 50 L15 35 H35 Z" 
                              fill="none" stroke="#c724f5" stroke-width="3" />
                        <circle cx="50" cy="50" r="10" fill="none" stroke="#b967ff" stroke-width="2" />
                        <path d="M50 30 L60 40 L70 30" fill="none" stroke="#ff2a96" stroke-width="2" />
                    </svg>
                </div>
                <h1 class="title">MELOMANIAC</h1>
                <p class="subtitle">Portal de Música Exclusiva</p>
            </div>
        </header>
        
        <main class="main-content">
            <div class="club-sign">CLUB EXCLUSIVO</div>
            
            <div class="hologram-cube">
                <div class="cube">
                    <div class="cube-face front">
                        <div class="members-count">35 INTEGRANTES</div>
                        <div class="join-text">¿TE UNES?</div>
                    </div>
                    <div class="cube-face back"></div>
                    <div class="cube-face right"></div>
                    <div class="cube-face left"></div>
                    <div class="cube-face top"></div>
                    <div class="cube-face bottom"></div>
                </div>
            </div>
            
            <div class="social-buttons">
                <a href="#" class="social-icon"><i class="fab fa-instagram"></i></a>
                <a href="#" class="social-icon"><i class="fab fa-twitter"></i></a>
                <a href="#" class="social-icon"><i class="fab fa-whatsapp"></i></a>
                <a href="#" class="text-button">Reglamento</a>
                <a href="#" class="text-button">Protocolo</a>
            </div>
            
            <div class="music-player">
                <div class="now-playing">
                    <div class="track-info">
                        <div class="track-name">Lumbra</div>
                        <div class="artist">Cali Y El Dandee</div>
                    </div>
                    <div class="heart-icon">♥</div>
                </div>
                
                <div class="progress-bar">
                    <div class="progress"></div>
                </div>
                
                <div class="time">
                    <span>1:20</span>
                    <span>4:30</span>
                </div>
                
                <div class="player-controls">
                    <button class="control-button">⏮</button>
                    <button class="control-button">⏪</button>
                    <button class="control-button play-button">▶</button>
                    <button class="control-button">⏩</button>
                    <button class="control-button">⏭</button>
                </div>
            </div>
        </main>
        
        <aside class="side-panel">
            <div class="profile">
                <div class="profile-image" style="background: url('data:image/svg+xml;utf8,<svg xmlns=%22http://www.w3.org/2000/svg%22 width=%22120%22 height=%22120%22><rect width=%22120%22 height=%22120%22 fill=%22%23333%22/><circle cx=%2260%22 cy=%2245%22 r=%2220%22 fill=%22%23555%22/><rect x=%2230%22 y=%2270%22 width=%2260%22 height=%2240%22 fill=%22%23555%22/></svg>')"></div>
                <div class="profile-title">FOUNDER</div>
                <div class="profile-name">NEXUS-7</div>
            </div>
            
            <div class="profile">
                <div class="profile-image" style="background: url('data:image/svg+xml;utf8,<svg xmlns=%22http://www.w3.org/2000/svg%22 width=%22120%22 height=%22120%22><rect width=%22120%22 height=%22120%22 fill=%22%23333%22/><circle cx=%2260%22 cy=%2245%22 r=%2220%22 fill=%22%23555%22/><rect x=%2230%22 y=%2270%22 width=%2260%22 height=%2240%22 fill=%22%23555%22/></svg>')"></div>
                <div class="profile-title">LEADER</div>
                <div class="profile-name">SYN-0</div>
            </div>
            
            <div class="quote">
                <p class="quote-text">Let the music take control, just let it go.</p>
                <div class="signature">© MELOMANIACS 2024</div>
            </div>
        </aside>
        
        <footer>
            <div class="copyright">© 2024 MELOMANIAC. Todos os direitos reservados.</div>
            <div class="footer-social">
                <a href="#"><i class="fab fa-instagram"></i></a>
                <a href="#"><i class="fab fa-twitter"></i></a>
                <a href="#"><i class="fab fa-whatsapp"></i></a>
                <a href="#"><i class="fab fa-spotify"></i></a>
                <a href="#"><i class="fab fa-github"></i></a>
            </div>
        </footer>
    </div>

    <script>
        // Cria partículas e efeitos de luz
        document.addEventListener('DOMContentLoaded', function() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.classList.add('particle');
                
                const size = Math.random() * 5 + 2;
                const colors = ['#c724f5', '#ff2a96', '#b967ff'];
                const color = colors[Math.floor(Math.random() * colors.length)];
                
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                particle.style.background = color;
                particle.style.left = `${Math.random() * 100}vw`;
                particle.style.top = `${Math.random() * 100}vh`;
                particle.style.animationDuration = `${Math.random() * 20 + 10}s`;
                particle.style.animationDelay = `-${Math.random() * 20}s`;
                
                particlesContainer.appendChild(particle);
            }
            
            // Cria efeitos de fumaça
            for (let i = 0; i < 5; i++) {
                const smoke = document.createElement('div');
                smoke.classList.add('smoke');
                
                smoke.style.left = `${Math.random() * 100}vw`;
                smoke.style.top = `${Math.random() * 100}vh`;
                smoke.style.animationDuration = `${Math.random() * 30 + 20}s`;
                smoke.style.animationDelay = `-${Math.random() * 30}s`;
                
                particlesContainer.appendChild(smoke);
            }
            
            // Cria raios de energia
            for (let i = 0; i < 3; i++) {
                const beam = document.createElement('div');
                beam.classList.add('energy-beam');
                
                beam.style.left = `${Math.random() * 100}vw`;
                beam.style.transform = `rotate(${Math.random() * 10 - 5}deg)`;
                beam.style.animationDuration = `${Math.random() * 10 + 5}s`;
                beam.style.animationDelay = `-${Math.random() * 10}s`;
                
                particlesContainer.appendChild(beam);
            }
            
            // Funcionalidade do player de música
            const playButton = document.querySelector('.play-button');
            let isPlaying = false;
            
            playButton.addEventListener('click', function() {
                isPlaying = !isPlaying;
                playButton.textContent = isPlaying ? '❚❚' : '▶';
                
                // Animação adicional para a barra de progresso
                const progressBar = document.querySelector('.progress');
                if (isPlaying) {
                    progressBar.style.animation = 'progress-animation 4s linear infinite';
                } else {
                    progressBar.style.animation = 'none';
                }
            });
            
            // Adiciona a animação da barra de progresso
            const style = document.createElement('style');
            style.textContent = `
                @keyframes progress-animation {
                    0% { width: 0%; }
                    100% { width: 100%; }
                }
            `;
            document.head.appendChild(style);
        });
    </script>
</body>
</html>
