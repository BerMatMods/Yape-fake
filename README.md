<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>💖 Para Briyidth - Amor Interactivo 💖</title>
<style>
  /* Fuentes */
  @import url('https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@400;700&display=swap');

  /* Reset */
  * {
    margin: 0; padding: 0; box-sizing: border-box;
  }

  body {
    font-family: 'Montserrat', sans-serif;
    background: linear-gradient(135deg, #ffe5e9 0%, #ffb3bf 50%, #ff7a87 100%);
    color: #4a1f1f;
    height: 100vh;
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    user-select: none;
    position: relative;
  }

  /* Corazones animados */
  .heart {
    position: fixed;
    width: 24px;
    height: 24px;
    background: #ff4f6d;
    transform-origin: center;
    animation: floatUp linear forwards;
    opacity: 0.85;
    clip-path: polygon(
      50% 0%, 61% 12%, 75% 15%, 80% 25%, 80% 40%, 75% 55%, 60% 70%, 50% 80%, 40% 70%, 25% 55%, 20% 40%, 20% 25%, 25% 15%, 39% 12%
    );
    z-index: 0;
  }
  @keyframes floatUp {
    0% {
      transform: translateY(0) scale(1);
      opacity: 0.85;
    }
    100% {
      transform: translateY(-150vh) scale(1.5);
      opacity: 0;
    }
  }

  /* Contenedor principal */
  #access-container, #main-page {
    background: rgba(255, 255, 255, 0.92);
    border-radius: 25px;
    box-shadow: 0 10px 25px rgba(255, 79, 109, 0.4);
    padding: 40px 50px;
    max-width: 480px;
    width: 90vw;
    text-align: center;
    z-index: 1;
  }

  /* --- Acceso --- */
  #access-container h2 {
    font-family: 'Great Vibes', cursive;
    font-size: 3.8rem;
    color: #ff2d5a;
    text-shadow: 1px 1px 5px #ffd7dd;
    margin-bottom: 30px;
    user-select: none;
  }

  #access-container p {
    font-size: 1.25rem;
    color: #772b35;
    margin-bottom: 25px;
  }

  #password-input {
    width: 100%;
    padding: 16px 20px;
    font-size: 1.35rem;
    font-weight: 700;
    border-radius: 12px;
    border: 3px solid #ff2d5a;
    outline: none;
    text-align: center;
    letter-spacing: 0.15em;
    color: #772b35;
    transition: border-color 0.3s ease;
  }
  #password-input:focus {
    border-color: #ff4f6d;
  }

  #submit-btn {
    margin-top: 28px;
    background-color: #ff2d5a;
    color: #fff;
    font-weight: 900;
    font-size: 1.4rem;
    border: none;
    padding: 14px 40px;
    border-radius: 50px;
    cursor: pointer;
    box-shadow: 0 8px 20px rgba(255, 79, 109, 0.7);
    transition: background-color 0.4s ease;
  }
  #submit-btn:hover {
    background-color: #d62c48;
  }

  #error-msg {
    margin-top: 20px;
    font-weight: 700;
    font-size: 1.15rem;
    color: #d32f2f;
    min-height: 28px;
  }

  #recover-link {
    margin-top: 30px;
    font-size: 1rem;
    color: #772b35;
  }
  #recover-link strong {
    font-weight: 900;
  }
  #recover-link a {
    color: #ff2d5a;
    font-weight: 900;
    text-decoration: underline;
    cursor: pointer;
    transition: color 0.3s ease;
  }
  #recover-link a:hover {
    color: #d62c48;
  }

  /* --- Página Principal --- */
  #main-page {
    display: none;
    flex-direction: column;
    align-items: center;
  }
  #main-page.visible {
    display: flex;
  }

  #main-page header {
    font-family: 'Great Vibes', cursive;
    font-size: 4.2rem;
    color: #ff2d5a;
    text-shadow: 2px 2px 10px #ffd7dd;
    margin-bottom: 15px;
    user-select: none;
  }
  #main-page .subtitle {
    font-weight: 700;
    font-size: 1.3rem;
    color: #772b35;
    margin-bottom: 50px;
    user-select: none;
  }
  .counter {
    background: #fff0f0;
    padding: 32px 55px;
    border-radius: 25px;
    box-shadow: 0 15px 40px #ff4f6d70;
    max-width: 520px;
    width: 100%;
    user-select: none;
  }
  .counter h2 {
    font-family: 'Great Vibes', cursive;
    font-size: 3rem;
    color: #d81e3e;
    margin-bottom: 22px;
  }
  .time-values {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    font-weight: 800;
    font-size: 1.6rem;
    color: #772b35;
  }
  .time-values > div {
    flex: 1 1 90px;
    margin: 12px;
    padding: 16px 0;
    border-radius: 20px;
    background: #ffb0bb;
    box-shadow: 0 8px 16px #d62c48aa;
    user-select: text;
  }

  .time-values > div span {
    font-size: 2.4rem;
    display: block;
    margin-bottom: 8px;
  }

  /* Mensajes */
  .message, #secret-message, #sent-message {
    margin-top: 55px;
    max-width: 520px;
    font-style: italic;
    text-align: center;
    line-height: 1.6;
    color: #7a2a3b;
    font-size: 1.65rem;
    font-family: 'Great Vibes', cursive;
    padding: 26px 32px;
    border-radius: 28px;
    background: #ffd7dd;
    box-shadow: 0 12px 28px #ff2d5a88;
    opacity: 0;
    transform: translateY(25px);
    transition: all 0.7s ease;
    user-select: none;
  }
  .visible {
    opacity: 1 !important;
    transform: translateY(0) !important;
  }

  /* Botones */
  button {
    margin-top: 48px;
    background-color: #ff2d5a;
    color: #fff;
    border: none;
    padding: 16px 48px;
    border-radius: 60px;
    font-size: 1.4rem;
    cursor: pointer;
    box-shadow: 0 10px 26px rgba(255, 79, 109, 0.75);
    font-weight: 900;
    transition: background-color 0.4s ease;
    user-select: none;
  }
  button:hover {
    background-color: #d62c48;
  }

  footer {
    margin-top: 70px;
    padding: 18px 10px;
    font-size: 1rem;
    color: #942433;
    user-select: none;
  }

  /* Animación escritura */
  .typing {
    border-right: 3px solid #d62c48;
    white-space: nowrap;
    overflow: hidden;
    animation: typing 4s steps(40, end) forwards, blink 1s step-end infinite;
  }
  @keyframes typing {
    from { width: 0; }
    to { width: 100%; }
  }
  @keyframes blink {
    50% { border-color: transparent; }
  }

  /* Responsive */
  @media (max-width: 480px) {
    #access-container, #main-page {
      padding: 30px 25px;
      width: 95vw;
    }
    #main-page header {
      font-size: 3.2rem;
    }
    .counter h2 {
      font-size: 2.2rem;
    }
    .time-values > div {
      font-size: 1.3rem;
    }
  }
</style>
</head>
<body>

<!-- Corazones animados -->
<script>
  // Crea corazones flotantes aleatorios
  function createHeart() {
    const heart = document.createElement('div');
    heart.className = 'heart';
    heart.style.left = Math.random() * window.innerWidth + 'px';
    heart.style.animationDuration = (5 + Math.random() * 5) + 's';
    heart.style.width = heart.style.height = (12 + Math.random() * 18) + 'px';
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 10000);
  }
  setInterval(createHeart, 400);
</script>

<!-- Acceso protegido -->
<div id="access-container" role="main" aria-label="Acceso protegido para Briyidth">
  <h2>💖 Código de acceso 💖</h2>
  <p>Introduce la fecha cuando nos besamos por primera vez (dd/mm/aa):</p>
  <input type="text" id="password-input" placeholder="Ejemplo: 14/01/24" aria-label="Código de acceso" autocomplete="off" />
  <button id="submit-btn" aria-label="Enviar código de acceso">Entrar</button>
  <div id="error-msg" aria-live="polite"></div>

  <p id="recover-link" aria-label="Recuperar código de acceso">
    ¿<strong>Olvidaste la fecha</strong>?&nbsp;
    <a href="https://wa.me/51937556459?text=%E2%9D%A4%EF%B8%8F%20*AnthZz%20Berrocal*%20%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20*Olvid%C3%B3%20la%20fecha%20tu%20princesa%20%E2%9D%A4%EF%B8%8F*" 
       target="_blank" 
       rel="noopener noreferrer"
       style="color:#ff2d5a; font-weight: 900; text-decoration: underline; cursor: pointer;">
      Haz click aquí para recuperar
    </a>
  </p>
</div>

<!-- Página principal oculta inicialmente -->
<div id="main-page" role="main" aria-label="Página principal romántica para Briyidth" aria-live="polite">
  <header>Para Briyidth ❤️</header>
  <div class="subtitle">Celebrando nuestro amor cada instante</div>

  <div class="counter" aria-label="Contador del tiempo juntos">
    <h2>Tiempo juntos</h2>
    <div class="time-values" aria-atomic="true" aria-live="polite">
      <div><span id="months">0</span><br>Meses</div>
      <div><span id="weeks">0</span><br>Semanas</div>
      <div><span id="days">0</span><br>Días</div>
      <div><span id="hours">0</span><br>Horas</div>
      <div><span id="minutes">0</span><br>Minutos</div>
      <div><span id="seconds">0</span><br>Segundos</div>
    </div>
  </div>

  <div class="message visible" id="main-message">
    Cada momento contigo es un regalo que atesoro en mi corazón.<br>
    ¡Te amo muchísimo, mi reina hermosa! ❤️
  </div>

  <button id="secret-btn" aria-expanded="false" aria-controls="secret-message" aria-label="Mostrar mensaje secreto">
    Mostrar mensaje secreto
  </button>

  <div id="secret-message" class="message" role="region" aria-live="polite" aria-atomic="true" style="max-width:480px; margin-top:30px; user-select:none;">
    <!-- Mensajes secretos aparecerán aquí -->
  </div>

  <button id="send-love-btn" aria-label="Enviar mensaje de amor">
    Enviar mensaje de amor ❤️
  </button>

  <div id="sent-message" class="message" role="alert" aria-live="assertive"></div>

  <footer>⚡ BerMat-Bot MD🔥 &copy; 2025</footer>
</div>

<script>
  // Acceso con contraseña
  const password = '14/01/24';
  const accessContainer = document.getElementById('access-container');
  const passwordInput = document.getElementById('password-input');
  const submitBtn = document.getElementById('submit-btn');
  const errorMsg = document.getElementById('error-msg');
  const mainPage = document.getElementById('main-page');

  submitBtn.addEventListener('click', () => {
    const entered = passwordInput.value.trim();
    if(entered === password) {
      errorMsg.textContent = '';
      accessContainer.style.display = 'none';
      mainPage.classList.add('visible');
      startCounter();
      setupSecretMessages();
    } else {
      errorMsg.textContent = 'Código incorrecto, intenta de nuevo ❤️';
      passwordInput.value = '';
      passwordInput.focus();
    }
  });

  passwordInput.addEventListener('keypress', (e) => {
    if(e.key === 'Enter') submitBtn.click();
  });

  // Contador
  function startCounter() {
    const monthsEl = document.getElementById('months');
    const weeksEl = document.getElementById('weeks');
    const daysEl = document.getElementById('days');
    const hoursEl = document.getElementById('hours');
    const minutesEl = document.getElementById('minutes');
    const secondsEl = document.getElementById('seconds');

    // Fecha del primer beso (año, mes-1, día, hora, minuto, segundo)
    const firstKiss = new Date(2024, 0, 14, 0, 0, 0); // 14 de enero 2024

    function updateCounter() {
      const now = new Date();
      let diff = now - firstKiss;

      if(diff < 0) diff = 0;

      // Cálculos aproximados
      const msInSecond = 1000;
      const msInMinute = msInSecond * 60;
      const msInHour = msInMinute * 60;
      const msInDay = msInHour * 24;
      const msInWeek = msInDay * 7;
      const msInMonth = msInDay * 30.44; // promedio

      const months = Math.floor(diff / msInMonth);
      diff -= months * msInMonth;

      const weeks = Math.floor(diff / msInWeek);
      diff -= weeks * msInWeek;

      const days = Math.floor(diff / msInDay);
      diff -= days * msInDay;

      const hours = Math.floor(diff / msInHour);
      diff -= hours * msInHour;

      const minutes = Math.floor(diff / msInMinute);
      diff -= minutes * msInMinute;

      const seconds = Math.floor(diff / msInSecond);

      monthsEl.textContent = months;
      weeksEl.textContent = weeks;
      daysEl.textContent = days;
      hoursEl.textContent = hours;
      minutesEl.textContent = minutes;
      secondsEl.textContent = seconds;
    }

    updateCounter();
    setInterval(updateCounter, 1000);
  }

  // Mensajes secretos
  const secretBtn = document.getElementById('secret-btn');
  const secretMessage = document.getElementById('secret-message');
  const messages = [
    "Eres mi sueño hecho realidad, la luz que guía mis días y la paz de mis noches.",
    "Mi corazón late más fuerte cada vez que pienso en ti, Briyidth.",
    "Gracias por ser mi compañera, mi amiga y mi amor eterno.",
    "Cada día contigo es una bendición que atesoro profundamente.",
    "Tu sonrisa ilumina hasta mis días más oscuros.",
    "Te amo con toda el alma y siempre estaré a tu lado."
  ];

  let msgIndex = 0;
  function setupSecretMessages() {
    secretBtn.addEventListener
