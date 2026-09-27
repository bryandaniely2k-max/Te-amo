<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Feliz Primer Aniversario</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Quicksand:wght@300;400;600&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: #121212; 
            color: #E0E0E0;
            font-family: 'Quicksand', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            background-image: radial-gradient(circle at center, #1a1a1a 0%, #0a0a0a 100%);
            overflow-x: hidden; 
        }

        .container {
            background: rgba(30, 30, 30, 0.85);
            border: 2px solid #D4AF37; /* Dorado Hamilton */
            border-radius: 15px;
            max-width: 800px;
            padding: 40px;
            text-align: center;
            box-shadow: 0 0 20px rgba(212, 175, 55, 0.2), 
                        inset 0 0 15px rgba(255, 105, 180, 0.1); /* Destello rosa Suzuki */
            position: relative;
            z-index: 10; 
            backdrop-filter: blur(5px); 
        }

        h1 {
            font-family: 'Playfair Display', serif;
            color: #D4AF37;
            font-size: 2.5rem;
            margin-bottom: 20px;
            letter-spacing: 2px;
        }

        .ship-title {
            font-size: 1.2rem;
            color: #89CFF0; /* Azul suave Tani */
            margin-bottom: 30px;
            font-weight: 600;
        }

        .ship-title span {
            color: #FF69B4; /* Rosa vibrante Suzuki */
        }

        p.letter {
            font-size: 1.1rem;
            line-height: 1.8;
            margin-bottom: 20px;
            text-align: justify;
        }

        .quote {
            font-family: 'Playfair Display', serif;
            font-style: italic;
            color: #D4AF37;
            font-size: 1.3rem;
            margin: 25px 0;
            text-align: center;
        }

        .decor-images {
            display: flex;
            justify-content: space-around;
            margin: 30px 0;
            gap: 15px;
        }

        .decor-images img {
            width: 150px;
            height: 150px;
            object-fit: cover;
            border-radius: 50%;
            border: 3px solid #D4AF37;
            box-shadow: 0 4px 10px rgba(0,0,0,0.5);
            transition: transform 0.3s ease;
        }

        .decor-images img:hover {
            transform: scale(1.05);
        }

        .decor-images img.suzuki-tani {
            border-color: #FF69B4; /* Borde rosa para la foto de ellos */
        }

        .music-controls {
            margin-top: 30px;
        }

        #play-btn {
            background-color: #D4AF37;
            color: #121212;
            border: none;
            padding: 12px 25px;
            font-size: 1rem;
            font-weight: 600;
            border-radius: 25px;
            cursor: pointer;
            font-family: 'Quicksand', sans-serif;
            transition: all 0.3s ease;
            box-shadow: 0 0 10px rgba(212, 175, 55, 0.4);
        }

        #play-btn:hover {
            background-color: #F1C40F;
            box-shadow: 0 0 15px rgba(241, 196, 15, 0.6);
        }

        .signature {
            margin-top: 40px;
            font-family: 'Playfair Display', serif;
            font-size: 1.5rem;
            color: #D4AF37;
            text-align: right;
        }

        .heart-particle {
            position: fixed;
            top: -10vh; 
            user-select: none;
            pointer-events: none; 
            z-index: 1; 
            animation: fall linear forwards;
            opacity: 0.7;
        }

        @keyframes fall {
            to {
                transform: translateY(110vh); 
            }
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Feliz Primer Aniversario, Isabel</h1>
        <div class="ship-title">Como Tani y <span>Suzuki</span></div>

        <div class="decor-images">
            <img src="link_a_imagen_burr.jpg" alt="Aaron Burr" title="Aaron Burr">
            <img src="link_a_imagen_suzuki_tani.jpg" alt="Suzuki y Tani" class="suzuki-tani" title="Suzuki y Tani">
        </div>

        <p class="letter">
            Mi amor, si algo he aprendido en este tiempo juntos, es que siempre estuve destinado a encontrarte. Al igual que Burr, durante mucho tiempo observé el mundo pasar, siempre <em>willing to wait for it</em>, esperando el momento exacto y a la persona indicada. Y valió cada segundo de espera porque llegaste tú.
        </p>

        <div class="quote">
            "I am the one thing in life I can control... I am willing to wait for it."
        </div>

        <p class="letter">
            Eres mi Suzuki. Eres esa energía, esa alegría y esa luz brillante que le da todo el color a mis días. Y quiero que sepas que yo siempre seré tu Tani, observándote con total admiración y amándote a mi manera tranquila pero profunda. Aunque a veces parezcamos polos opuestos, encajamos a la perfección. Me complementas de la forma más hermosa y sincera posible.
        </p>

        <p class="letter">
            Cada día a tu lado se siente como un auténtico arrullo de estrellas. Gracias por hacer de este primer año la mejor historia que he vivido. Este es solo el primer capítulo de todo lo que nos espera.
        </p>

        <div class="signature">
            Te amo,<br>
            Atte: Brian
        </div>

        <audio id="bg-music" loop>
            <source src="arrullo_de_estrellas.mp3" type="audio/mpeg">
            Tu navegador no soporta el elemento de audio.
        </audio>

        <div class="music-controls">
            <button id="play-btn">🎵 Reproducir nuestra canción</button>
        </div>
    </div>

    <script>
        // Controles de Música
        const playBtn = document.getElementById('play-btn');
        const audio = document.getElementById('bg-music');
        let isPlaying = false;

        playBtn.addEventListener('click', () => {
            if (isPlaying) {
                audio.pause();
                playBtn.innerHTML = '🎵 Reproducir nuestra canción';
            } else {
                audio.play();
                playBtn.innerHTML = '⏸️ Pausar música';
            }
            isPlaying = !isPlaying;
        });

        // Animación de Corazones Cayendo (Polos Opuestos)
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart-particle');
            
            // Alternar entre corazones rosas (Suzuki) y azules/blancos (Tani)
            const isPink = Math.random() > 0.5;
            heart.innerText = isPink ? '💖' : '💙'; 
            
            heart.style.left = Math.random() * 100 + 'vw';
            
            const duration = Math.random() * 5 + 5;
            heart.style.animationDuration = duration + 's';
            
            heart.style.fontSize = Math.random() * 1 + 1 + 'rem';
            
            document.body.appendChild(heart);
            
            setTimeout(() => {
                heart.remove();
            }, duration * 1000);
        }

        setInterval(createHeart, 600);
    </script>
</body>
</html>
