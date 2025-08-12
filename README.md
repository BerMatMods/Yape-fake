<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>💖 Para Briyidth - Acceso Protegido 💖</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Great+Vibes&family=Montserrat:wght@400;700&display=swap');
  body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(135deg, #fce1e4, #fbb1b1), url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1350&q=80') no-repeat center center fixed;
    background-size: cover;
    font-family: 'Montserrat', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #4a2c2a;
    overflow: hidden;
    user-select: none;
  }
  #access-container {
    background: rgba(255, 240, 240, 0.85);
    padding: 35px 45px;
    border-radius: 20px;
    box-shadow: 0 0 30px #e86868cc;
    text-align: center;
    max-width: 420px;
    width: 90%;
  }
  #access-container h2 {
    font-family: 'Great Vibes', cursive;
    font-size: 3.5rem;
    margin-bottom: 25px;
    color: #b33a3a;
    text-shadow: 2px 2px 6px #fff0f0;
  }
  #access-container p {
    font-size: 1.2rem;
    margin-bottom: 20px;
  }
  #password-input {
    font-size: 1.3rem;
    padding: 14px 18px;
    border-radius: 10px;
    border: 3px solid #b33a3a;
    width: 100%;
    margin-bottom: 22px;
    text-align: center;
    font-weight: 700;
    letter-spacing: 0.1em;
  }
  #submit-btn {
    background-color: #b33a3a;
    color: white;
    border: none;
    padding: 14px 30px;
    border-radius: 50px;
    font-size: 1.4rem;
    cursor: pointer;
    box-shadow: 0 8px 15px #7a2121cc;
    transition: background-color 0.3s ease;
    font-weight: 700;
    user-select: none;
  }
  #submit-btn:hover {
    background-color: #7a2121;
  }
  #error-msg {
    color: #b33232;
    font-weight: 700;
    margin-top: 14px;
    min-height: 28px;
    font-size: 1.1rem;
  }
  #recover-link {
    margin-top: 28px;
    font-size: 1rem;
    color: #b33a3a;
  }
  #recover-link strong {
    font-weight: 900;
  }
  #recover-link a {
    color: #7a2121;
    font-weight: 900;
    text-decoration: underline;
    cursor: pointer;
  }
  #recover-link a:hover {
    color: #b33a3a;
  }

  /* Estilos página principal */
  #main-page {
    display: none;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
    padding: 20px;
    position: relative;
    width: 100%;
    max-width: 600px;
    color: #4a2c2a;
  }
  #main-page.visible {
    display: flex;
  }
  header {
    font-family: 'Great Vibes', cursive;
    font-size: 3.8rem;
    margin: 30px 0 15px 0;
    color: #b33a3a;
    text-shadow: 1px 1px 6px #fff3f3;
    user-select: none;
  }
  .subtitle {
    font-weight: 700;
    font-size: 1.25rem;
    margin-bottom: 45px;
    user-select: none;
  }
  .counter {
    background: #fff0f0cc;
    padding: 30px 50px;
    border-radius: 18px;
    box-shadow: 0 12px 38px #f2a2a287;
    text-align: center;
    max-width: 480px;
    width: 100%;
    user-select: none;
  }
  .counter h2 {
    font-family: 'Great Vibes', cursive;
    font-size: 2.8rem;
    margin-bottom: 18px;
    color: #b33232;
  }
  .time-values {
    display: flex;
    justify-content: space-around;
    margin-top: 22px;
    font-weight: 700;
    font-size: 1.5rem;
    flex-wrap: wrap;
  }
  .time-values div {
    flex: 1 1 80px;
    margin: 8px;
    padding: 12px;
    border-radius: 10px;
    background: #f6c8c8;
    box-shadow: 0 5px 9px #dc9999;
    user-select: text;
  }
  .message, #secret-message, #sent-message {
    margin-top: 48px;
    max-width: 480px;
    font-style: italic;
    text-align: center;
    line-height: 1.6;
    color: #7a3b3b;
    font-size: 1.55rem;
    font-family: 'Great Vibes', cursive;
    padding: 22px 26px;
    border-radius: 20px;
    background: #f9eaea;
    box-shadow: 0 8px 20px #f2a2a2b3;
    user-select: none;
    opacity: 0;
    transform: translateY(18px);
    transition: all 0.55s ease;
  }
  .visible {
    opacity: 1 !important;
    transform: translateY(0) !important;
  }
  button {
    margin-top: 42px;
    background-color: #b33a3a;
    color: #fff;
    border: none;
    padding: 14px 32px;
    border-radius: 60px;
    font-size: 1.3rem;
    cursor: pointer;
    box-shadow: 0 7px 15px #7a2121cc;
    transition: background-color 0.35s ease;
    font-weight: 900;
    user-select: none;
  }
  button:hover {
    background-color: #7a2121;
  }
  footer {
    margin-top: auto;
    padding: 22px 12px 18px;
    font-size: 1rem;
    color: #842121;
    user-select: none;
  }

  /* Corazones animados */
  .heart {
    position: fixed;
    width: 24px;
    height: 24px;
    background: #b33a3a;
    transform-origin: center;
    animation: floatUp linear forwards;
    opacity: 0.85;
    clip-path: polygon(
      50% 0%, 61% 12%, 75% 15%, 80% 25%, 80% 40%, 75% 55%, 60% 70%, 50% 80%, 40% 70%, 25% 55%, 20% 40%, 20% 25%, 25% 15%, 39% 12%
    );
    user-select: none;
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
</style>
</head>
<body>

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
       style="color:#7a2121; font-weight: 900; text-decoration: underline; cursor: pointer;">
      Haz click aquí para recuperar
    </a>
  </p>
</div>

<!-- Página principal oculta inicialmente -->
<div id="main-page" role="main" aria-label="Página principal romántica para Briyidth">
  <header>Para Briyidth ❤️</header>
  <div class="subtitle">Celebrando nuestro amor cada instante</div>

  <div class="counter" aria-label="Contador del tiempo juntos">
    <h2>Tiempo juntos</h2>
    <div class="time-values" aria-live="polite" aria-atomic="true">
      <div><span id="months">0</span><br>Meses</div>
      <div><span id="weeks">0</span><br>Semanas</div>
      <div><span id="days">0</span><br>Días</div>
      <div><span id="hours">0</span><br>Horas</div>
      <div><span id="minutes">0</span><br>Minutos</div>
      <div><span id="seconds">0</span><br>Segundos</div>
    </div>
  </div>

  <div class="message visible" id
