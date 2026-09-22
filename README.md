<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Un Jardín Para Ti 🌻</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      user-select: none;
    }

    body {
      background-color: #0b0b0b;
      color: #fff;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      overflow: hidden;
      height: 100vh;
      width: 100vw;
      position: relative;
    }

    /* Banner de instrucciones */
    #instruction-box {
      position: absolute;
      top: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(20, 20, 20, 0.85);
      border: 2px solid #ffd700;
      padding: 12px 24px;
      border-radius: 30px;
      box-shadow: 0 0 15px rgba(255, 215, 0, 0.4);
      z-index: 100;
      text-align: center;
      transition: all 0.3s ease;
    }

    #instruction-text {
      color: #ffd700;
      font-size: 1.1rem;
      font-weight: 600;
      letter-spacing: 0.5px;
    }

    /* Contenedor del Jardín */
    #garden-container {
      width: 100%;
      height: 100%;
      position: relative;
      cursor: pointer;
    }

    /* Apodos y Frases flotantes */
    .pop-text {
      position: absolute;
      color: #ffeb3b;
      font-weight: bold;
      font-size: 1.2rem;
      text-shadow: 0 0 10px rgba(255, 215, 0, 0.8), 0 0 20px #000;
      pointer-events: none;
      animation: popup 3s forwards;
      z-index: 50;
      white-space: nowrap;
    }

    @keyframes popup {
      0% {
        opacity: 0;
        transform: translateY(10px) scale(0.8);
      }
      20% {
        opacity: 1;
        transform: translateY(-10px) scale(1.1);
      }
      80% {
        opacity: 1;
      }
      100% {
        opacity: 0;
        transform: translateY(-30px) scale(1);
      }
    }

    /* SVG de Girasol */
    .sunflower {
      position: absolute;
      width: 70px;
      height: 70px;
      transform: translate(-50%, -50%) scale(0);
      animation: bloom 0.6s ease-out forwards;
      pointer-events: none;
      filter: drop-shadow(0 0 8px rgba(255, 215, 0, 0.5));
    }

    @keyframes bloom {
      0% { transform: translate(-50%, -50%) scale(0) rotate(-45deg); }
      100% { transform: translate(-50%, -50%) scale(1) rotate(0deg); }
    }

    /* Modal / Pantalla Final */
    #final-modal {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) scale(0.8);
      width: 90%;
      max-width: 500px;
      background: rgba(18, 18, 18, 0.95);
      border: 3px solid #ffd700;
      border-radius: 20px;
      padding: 30px 20px;
      text-align: center;
      box-shadow: 0 0 30px rgba(255, 215, 0, 0.6);
      opacity: 0;
      pointer-events: none;
      transition: all 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      z-index: 200;
      max-height: 80vh;
      overflow-y: auto;
    }

    #final-modal.active {
      opacity: 1;
      pointer-events: auto;
      transform: translate(-50%, -50%) scale(1);
    }

    .main-title {
      color: #ffd700;
      font-size: 2.8rem;
      font-weight: 900;
      text-shadow: 0 0 15px rgba(255, 215, 0, 0.8);
      margin-bottom: 15px;
      letter-spacing: 2px;
    }

    .story-card {
      color: #eaeaea;
      font-size: 1.05rem;
      line-height: 1.6;
      text-align: left;
      background: rgba(255, 255, 255, 0.05);
      padding: 20px;
      border-radius: 12px;
      border-left: 4px solid #ffd700;
      margin-top: 15px;
    }

    .story-card h3 {
      color: #ffd700;
      margin-bottom: 10px;
    }

    .big-sunflower {
      width: 120px;
      height: 120px;
      margin: 0 auto 15px auto;
      display: block;
      animation: pulse 2s infinite alternate;
    }

    @keyframes pulse {
      0% { transform: scale(1); filter: drop-shadow(0 0 10px rgba(255, 215, 0, 0.5)); }
      100% { transform: scale(1.1); filter: drop-shadow(0 0 25px rgba(255, 215, 0, 0.9)); }
    }
  </style>
</head>
<body>

  <!-- Mensaje de instrucción flotante -->
  <div id="instruction-box">
    <p id="instruction-text">✨ Toca la pantalla para sembrar tus girasoles...</p>
  </div>

  <!-- Contenedor del Jardín Interactivo -->
  <div id="garden-container"></div>

  <!-- Modal del Mensaje Final -->
  <div id="final-modal">
    <!-- SVG de Girasol Gigante Centrado -->
    <svg class="big-sunflower" viewBox="0 0 100 100">
      <g transform="translate(50,50)">
        <!-- Petalos -->
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffd700" transform="rotate(0)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffa700" transform="rotate(30)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffd700" transform="rotate(60)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffa700" transform="rotate(90)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffd700" transform="rotate(120)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffa700" transform="rotate(150)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffd700" transform="rotate(180)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffa700" transform="rotate(210)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffd700" transform="rotate(240)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffa700" transform="rotate(270)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffd700" transform="rotate(300)" />
        <path d="M0,-10 C-5,-35 0,-48 0,-48 C0,-48 5,-35 0,-10" fill="#ffa700" transform="rotate(330)" />
        <!-- Centro del girasol -->
        <circle cx="0" cy="0" r="16" fill="#3e2723" />
        <circle cx="0" cy="0" r="12" fill="#5d4037" stroke="#ffa700" stroke-width="1" />
      </g>
    </svg>

    <h1 class="main-title">¡TE AMO!</h1>

    <div class="story-card">
      <h3>Nuestra Historia (2 Meses Juntos) 💛</h3>
      <p>
        Desde el primer día en que nos conocimos, supe que tenías algo verdaderamente especial. Estos dos meses a tu lado han estado llenos de momentos mágicos, risas inolvidables y una felicidad gigantesca.
      </p>
      <br>
      <p>
        Gracias por ser mi lugar seguro, por cada sonrisa y por llenar mi vida de luz como este jardín de girasoles. ¡Felices 2 meses, mi amor hermoso!
      </p>
    </div>
  </div>

  <script>
    // Configuración de palabras y frases
    const words = [
      "Mi cachetona 💛",
      "Mi gorditaaaa 🥰",
      "Chimuelita 🌻",
      "Mi lugar favorito 🌟",
      "2 meses increíbles ✨",
      "La más hermosa 😍",
      "Mi luz 💛",
      "Eres mi todo 💖"
    ];

    const instructions = [
      "✨ Toca la pantalla para sembrar tus girasoles...",
      "Sigue tocando para hacer crecer el jardín 🌻",
      "¡Mira cómo florecen tus palabras! 💛",
      "Unos toques más para descubrir la sorpresa finale... ✨",
      "¡Haz el último toque en el centro! 🌟"
    ];

    let clickCount = 0;
    const totalClicksNeeded = 12;
    const garden = document.getElementById('garden-container');
    const instructionText = document.getElementById('instruction-text');
    const finalModal = document.getElementById('final-modal');

    // Plantilla SVG para generar girasoles dinámicamente
    function createSunflowerSVG() {
      return `
        <svg class="sunflower" viewBox="0 0 100 100">
          <g transform="translate(50,50)">
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffd700" transform="rotate(0)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffa700" transform="rotate(30)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffd700" transform="rotate(60)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffa700" transform="rotate(90)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffd700" transform="rotate(120)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffa700" transform="rotate(150)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffd700" transform="rotate(180)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffa700" transform="rotate(210)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffd700" transform="rotate(240)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffa700" transform="rotate(270)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffd700" transform="rotate(300)" />
            <path d="M0,-8 C-4,-25 0,-35 0,-35 C0,-35 4,-25 0,-8" fill="#ffa700" transform="rotate(330)" />
            <circle cx="0" cy="0" r="12" fill="#3e2723" />
            <circle cx="0" cy="0" r="9" fill="#5d4037" />
          </g>
        </svg>
      `;
    }

    garden.addEventListener('click', (e) => {
      if (clickCount >= totalClicksNeeded) return;

      clickCount++;

      // Coordenadas del toque
      const x = e.clientX;
      const y = e.clientY;

      // 1. Crear Girasol
      const flowerWrapper = document.createElement('div');
      flowerWrapper.innerHTML = createSunflowerSVG();
      const flowerElem = flowerWrapper.firstElementChild;
      flowerElem.style.left = `${x}px`;
      flowerElem.style.top = `${y}px`;
      garden.appendChild(flowerElem);

      // 2. Crear Texto Apodo/Frase
      const textElem = document.createElement('div');
      textElem.className = 'pop-text';
      textElem.innerText = words[(clickCount - 1) % words.length];
      textElem.style.left = `${x - 20}px`;
      textElem.style.top = `${y - 40}px`;
      garden.appendChild(textElem);

      // 3. Actualizar Instrucciones
      if (clickCount === 3) instructionText.innerText = instructions[1];
      if (clickCount === 6) instructionText.innerText = instructions[2];
      if (clickCount === 9) instructionText.innerText = instructions[3];
      if (clickCount === 11) instructionText.innerText = instructions[4];

      // 4. Desbloquear Mensaje Final
      if (clickCount === totalClicksNeeded) {
        document.getElementById('instruction-box').style.display = 'none';
        setTimeout(() => {
          finalModal.classList.add('active');
        }, 600);
      }
    });
  </script>
</body>
</html>
