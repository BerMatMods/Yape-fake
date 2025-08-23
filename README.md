
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
  <title>Yape</title>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">
  <style>
    :root {
      --purple: #7b1fa2;
      --turquoise: #00c853;
      --white: #ffffff;
      --text: #333333;
      --text-secondary: #666666;
      --border: #e0e0e0;
      --shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', -apple-system, sans-serif;
    }

    body {
      background-color: var(--purple);
      color: var(--text);
      -webkit-font-smoothing: antialiased;
      overflow-x: hidden;
    }

    .container {
      max-width: 414px;
      margin: 0 auto;
      min-height: 100vh;
      position: relative;
    }

    /* Header */
    .top-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 20px 16px;
      color: white;
    }

    .top-bar h1 {
      font-size: 1.5em;
      margin: 0;
    }

    .top-bar .status {
      font-size: 0.8em;
      background: #fbbd00;
      color: black;
      padding: 4px 8px;
      border-radius: 12px;
      font-weight: bold;
    }

    .top-bar .icons {
      display: flex;
      gap: 20px;
    }

    .top-bar .icons i {
      font-size: 1.5em;
      color: white;
    }

    /* Menú hamburguesa */
    .menu-toggle {
      position: absolute;
      top: 20px;
      left: 16px;
      font-size: 1.5em;
      color: white;
      cursor: pointer;
      z-index: 100;
    }

    .menu-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.5);
      z-index: 99;
      display: none;
    }

    .menu-sidebar {
      position: fixed;
      top: 0;
      left: 0;
      width: 280px;
      height: 100%;
      background: var(--white);
      z-index: 100;
      transform: translateX(-100%);
      transition: transform 0.3s ease;
      padding: 80px 16px 20px;
      overflow-y: auto;
    }

    .menu-sidebar.active {
      transform: translateX(0);
    }

    .menu-header {
      text-align: center;
      margin-bottom: 20px;
      padding-bottom: 15px;
      border-bottom: 1px solid var(--border);
    }

    .menu-header img {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      margin: 0 auto 10px;
      border: 3px solid var(--purple);
    }

    .menu-header h3 {
      color: var(--purple);
      font-size: 1.2em;
    }

    .menu-item {
      padding: 16px;
      border-bottom: 1px solid var(--border);
      display: flex;
      align-items: center;
      gap: 12px;
      color: var(--text);
      cursor: pointer;
      transition: background 0.3s;
    }

    .menu-item:hover {
      background: #f5f5f5;
    }

    .menu-item i {
      color: var(--purple);
      font-size: 1.3em;
    }

    .menu-item .label {
      font-weight: 500;
    }

    .menu-item .desc {
      font-size: 0.8em;
      color: #888;
    }

    /* Servicios */
    .services-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 16px;
      padding: 20px;
    }

    .service-item {
      text-align: center;
      color: white;
      font-size: 0.85em;
    }

    .service-icon {
      width: 70px;
      height: 70px;
      background: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 8px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }

    .service-icon i {
      font-size: 1.5em;
      color: var(--purple);
    }

    /* Card: Saldo */
    .balance-card {
      background: var(--white);
      border-radius: 20px;
      margin: 20px 20px 15px;
      padding: 20px;
      box-shadow: var(--shadow);
    }

    .balance-toggle {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 12px 16px;
      background: var(--purple);
      border-radius: 12px;
      margin-bottom: 12px;
      cursor: pointer;
    }

    .balance-toggle span {
      color: white;
      font-weight: 600;
    }

    .balance-amount {
      font-size: 2.2em;
      font-weight: bold;
      margin: 10px 0;
    }

    /* Movimientos */
    .movements-toggle {
      background: var(--white);
      border-radius: 12px;
      padding: 16px;
      margin: 10px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      cursor: pointer;
      box-shadow: var(--shadow);
    }

    .movements-toggle span {
      color: var(--purple);
      font-weight: 600;
    }

    .movements-toggle i {
      color: var(--purple);
    }

    /* Banner promocional */
    .promo-banner {
      margin: 20px 20px 15px;
      background: var(--white);
      border-radius: 20px;
      overflow: hidden;
      box-shadow: var(--shadow);
    }

    .promo-banner img {
      width: 100%;
      height: auto;
      display: block;
    }

    /* Botones grandes */
    .big-button {
      margin: 20px 20px 0;
      background: var(--turquoise);
      color: white;
      border: none;
      padding: 16px;
      border-radius: 12px;
      font-size: 1.1em;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      box-shadow: 0 4px 12px rgba(0,200,83,0.3);
    }

    .big-button:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 16px rgba(0,200,83,0.4);
    }

    .big-button.secondary {
      background: transparent;
      border: 2px solid var(--turquoise);
      color: var(--turquoise);
    }

    .big-button.secondary:hover {
      background: rgba(0,200,83,0.1);
    }

    /* Transacción */
    .transaction-card {
      background: var(--white);
      border-radius: 20px;
      margin: 20px 20px 15px;
      padding: 20px;
      box-shadow: var(--shadow);
      display: none;
    }

    .transaction-title {
      font-size: 1.4em;
      color: var(--purple);
      margin-bottom: 12px;
    }

    .transaction-amount {
      font-size: 3.5em;
      font-weight: bold;
      margin: 10px 0;
    }

    .transaction-name {
      font-size: 1.3em;
      font-weight: 600;
      margin: 10px 0;
    }

    .transaction-date {
      font-size: 0.9em;
      color: var(--text-secondary);
      margin-bottom: 20px;
    }

    .security-code {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 15px 0;
      padding-bottom: 15px;
      border-bottom: 1px solid var(--border);
    }

    .security-code span {
      font-size: 0.9em;
      color: var(--text-secondary);
    }

    .security-code i {
      color: var(--turquoise);
      font-size: 1.2em;
    }

    .security-digits {
      display: flex;
      gap: 10px;
    }

    .digit {
      width: 40px;
      height: 40px;
      background: #f0f0f0;
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      color: var(--text);
    }

    .transaction-details {
      margin-top: 20px;
      font-size: 0.95em;
      color: var(--text-secondary);
    }

    .detail-row {
      display: flex;
      justify-content: space-between;
      margin: 10px 0;
    }

    /* Pantallas */
    .screen {
      display: none;
    }

    .screen.active {
      display: block;
    }

    /* Animaciones */
    @keyframes scanLine {
      0% { top: 0; }
      100% { top: 285px; }
    }

    .scan-line {
      width: 100%;
      height: 5px;
      background: #00ff00;
      position: absolute;
      top: 0;
      animation: scanLine 1.6s ease-in-out infinite;
      box-shadow: 0 0 15px #00ff00;
    }

    .sparkles {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 1001;
      display: none;
    }

    .spark {
      position: absolute;
      width: 10px;
      height: 10px;
      background: #fff;
      border-radius: 50%;
      opacity: 0.8;
      animation: fall linear forwards;
    }

    @keyframes fall {
      0% { transform: translateY(-20px); opacity: 1; }
      100% { transform: translateY(100vh); opacity: 0; }
    }

    /* Footer */
    .footer {
      text-align: center;
      padding: 20px 0;
      color: #aaa;
      font-size: 0.8em;
    }
  </style>
</head>
<body>

  <div class="container">

    <!-- Menú hamburguesa -->
    <div class="menu-toggle" onclick="toggleMenu()">
      <i class="fas fa-bars"></i>
    </div>

    <div class="menu-overlay" id="menuOverlay" onclick="toggleMenu()"></div>

    <div class="menu-sidebar" id="menuSidebar">
      <div class="menu-header">
        <img src="https://ui-avatars.com/api/?name=AnthZz+Berrocal&background=7b1fa2&color=fff" alt="Perfil" id="menuProfilePic">
        <h3 id="menuName">AnthZz Berrocal</h3>
        <p>_BerMat_Mods</p>
      </div>

      <div class="menu-item" onclick="showScreen('profile')">
        <i class="fas fa-user"></i>
        <div>
          <div class="label">Perfil</div>
          <div class="desc">Editar información</div>
        </div>
      </div>

      <div class="menu-item" onclick="showScreen('editBalance')">
        <i class="fas fa-wallet"></i>
        <div>
          <div class="label">Editar Saldo</div>
          <div class="desc">S/ <span id="menuBalance">27.00</span></div>
        </div>
      </div>

      <div class="menu-item" onclick="alert('Créditos: S/ 800 disponibles')">
        <i class="fas fa-hand-holding-usd"></i>
        <div>
          <div class="label">Créditos</div>
          <div class="desc">S/ 800 disponibles</div>
        </div>
      </div>

      <div class="menu-item" onclick="alert('Promociones')">
        <i class="fas fa-percent"></i>
        <div>
          <div class="label">Promociones</div>
          <div class="desc">Ofertas exclusivas</div>
        </div>
      </div>

      <div class="menu-item" onclick="alert('Notificaciones')">
        <i class="fas fa-bell"></i>
        <div>
          <div class="label">Notificaciones</div>
          <div class="desc">Activadas</div>
        </div>
      </div>

      <div class="menu-item" onclick="alert('Seguridad')">
        <i class="fas fa-shield-alt"></i>
        <div>
          <div class="label">Seguridad</div>
          <div class="desc">PIN, huella, facial</div>
        </div>
      </div>

      <div class="menu-item" onclick="alert('Soporte')">
        <i class="fas fa-headset"></i>
        <div>
          <div class="label">Soporte</div>
          <div class="desc">Chatea con nosotros</div>
        </div>
      </div>

      <div class="menu-item" onclick="alert('Ayuda')">
        <i class="fas fa-question-circle"></i>
        <div>
          <div class="label">Ayuda</div>
          <div class="desc">Centro de ayuda</div>
        </div>
      </div>

      <div class="menu-item" onclick="alert('Términos y condiciones')">
        <i class="fas fa-file-alt"></i>
        <div>
          <div class="label">Términos y condiciones</div>
        </div>
      </div>

      <div class="menu-item" onclick="alert('Privacidad')">
        <i class="fas fa-lock"></i>
        <div>
          <div class="label">Privacidad</div>
        </div>
      </div>

      <div class="menu-item" onclick="alert('Cerrar sesión')">
        <i class="fas fa-sign-out-alt"></i>
        <div>
          <div class="label">Cerrar sesión</div>
        </div>
      </div>
    </div>

    <!-- Header -->
    <div class="top-bar">
      <i class="fas fa-user"></i>
      <h1>Hola, Antonio</h1>
      <span class="status">Gratis</span>
      <div class="icons">
        <i class="fas fa-headset"></i>
        <i class="fas fa-bell"></i>
      </div>
    </div>

    <!-- Pantalla: Inicio -->
    <div id="home" class="screen active">
      <div class="services-grid">
        <div class="service-item" onclick="startScan()">
          <div class="service-icon"><i class="fas fa-mobile-alt"></i></div>
          <div>Recargar celular</div>
        </div>
        <div class="service-item" onclick="alert('Yapear servicios')">
          <div class="service-icon"><i class="fas fa-bolt"></i></div>
          <div>Yapear servicios</div>
        </div>
        <div class="service-item" onclick="alert('Promos')">
          <div class="service-icon"><i class="fas fa-percent"></i></div>
          <div>Promos</div>
        </div>
        <div class="service-item" onclick="alert('Aprobar compras')">
          <div class="service-icon"><i class="fas fa-lock"></i></div>
          <div>Aprobar compras</div>
        </div>
        <div class="service-item" onclick="alert('Créditos')">
          <div class="service-icon"><i class="fas fa-wallet"></i></div>
          <div>Créditos</div>
        </div>
        <div class="service-item" onclick="alert('Tienda')">
          <div class="service-icon"><i class="fas fa-store"></i></div>
          <div>Tienda</div>
        </div>
        <div class="service-item" onclick="alert('Dólares')">
          <div class="service-icon"><i class="fas fa-dollar-sign"></i></div>
          <div>Dólares</div>
        </div>
        <div class="service-item" onclick="alert('Remesas')">
          <div class="service-icon"><i class="fas fa-globe-americas"></i></div>
          <div>Remesas</div>
        </div>
        <div class="service-item" onclick="alert('SOAT')">
          <div class="service-icon"><i class="fas fa-shield-alt"></i></div>
          <div>SOAT</div>
        </div>
        <div class="service-item" onclick="alert('Viajar en bus')">
          <div class="service-icon"><i class="fas fa-bus"></i></div>
          <div>Viajar en bus</div>
        </div>
        <div class="service-item" onclick="alert('Biométrica')">
          <div class="service-icon"><i class="fas fa-fingerprint"></i></div>
          <div>Biométrica</div>
        </div>
        <div class="service-item" onclick="alert('Ver todo')">
          <div class="service-icon"><i class="fas fa-plus"></i></div>
          <div>Ver todo</div>
        </div>
      </div>

      <div class="balance-card">
        <div class="balance-toggle" onclick="toggleBalance()">
          <span>Ocultar saldo</span>
          <span id="balanceAmount">S/ 27.00</span>
        </div>
      </div>

      <div class="movements-toggle" onclick="showScreen('movementsList')">
        <span>Mostrar movimientos</span>
        <i class="fas fa-chevron-down"></i>
      </div>

      <div class="promo-banner">
        <img src="https://via.placeholder.com/360x180?text=iPhone+16e+-+Solo+para+ti" alt="Promoción">
      </div>

      <button class="big-button secondary" onclick="startScan()">
        <i class="fas fa-qrcode"></i> ESCANEAR QR
      </button>
      <button class="big-button" onclick="yapearPorNumero()">
        <i class="fas fa-paper-plane"></i> YAPEAR
      </button>
    </div>

    <!-- Pantalla: Transacción -->
    <div id="transaction" class="screen" style="display:none;">
      <div class="transaction-card">
        <div class="transaction-title">¡Yapeaste!</div>
        <div class="transaction-amount">S/ <span id="transAmount">1</span></div>
        <div class="transaction-name"><span id="transName">Cintia Bernaola B.</span></div>
        <div class="transaction-date">
          <i class="fas fa-calendar"></i> <span id="transDate">22 ago. 2025</span> | <i class="fas fa-clock"></i> <span id="transTime">10:35 p.m.</span>
        </div>

        <div class="security-code">
          <span>CÓDIGO DE SEGURIDAD</span>
          <i class="fas fa-info-circle"></i>
          <div class="security-digits">
            <div class="digit" id="code1">4</div>
            <div class="digit" id="code2">6</div>
            <div class="digit" id="code3">4</div>
          </div>
        </div>

        <div class="transaction-details">
          <div class="detail-row">
            <span>Nro. de celular</span>
            <span id="transPhone">*** *** 777</span>
          </div>
          <div class="detail-row">
            <span>Destino</span>
            <span>Yape</span>
          </div>
          <div class="detail-row">
            <span>Nro. de operación</span>
            <span id="transOp">25422464</span>
          </div>
        </div>
      </div>

      <div class="promo-banner">
        <img src="https://via.placeholder.com/360x180?text=iPhone+16e+-+Solo+para+ti" alt="Promoción">
      </div>

      <button class="big-button secondary" onclick="goBack()">
        <i class="fas fa-arrow-left"></i> Volver
      </button>
    </div>

    <!-- Pantalla: Perfil -->
    <div id="profile" class="screen" style="display:none; padding:20px;">
      <h2 style="color:var(--purple); margin:20px 0;">Editar Perfil</h2>
      <img src="https://ui-avatars.com/api/?name=AnthZz+Berrocal&background=7b1fa2&color=fff" alt="Foto" class="profile-pic" id="profilePic" onclick="changePhoto()" style="width:80px; height:80px; border-radius:50%; margin:20px auto; display:block; border:3px solid var(--purple);">
      <div style="margin:15px 0;">
        <label style="display:block; margin-bottom:8px; color:white;">Nombre completo</label>
        <input type="text" id="editName" value="AnthZz Berrocal" style="width:100%; padding:12px; border-radius:8px; border:none; font-size:1em;">
      </div>
      <div style="margin:15px 0;">
        <label style="display:block; margin-bottom:8px; color:white;">Apodo</label>
        <input type="text" id="editNickname" value="_BerMat_Mods" style="width:100%; padding:12px; border-radius:8px; border:none; font-size:1em;">
      </div>
      <div style="margin:15px 0;">
        <label style="display:block; margin-bottom:8px; color:white;">Email</label>
        <input type="email" id="editEmail" value="anthzz@bermatmods.dev" style="width:100%; padding:12px; border-radius:8px; border:none; font-size:1em;">
      </div>
      <button class="big-button" onclick="saveProfile()">Guardar Cambios</button>
      <button class="big-button secondary" style="margin-top:10px;" onclick="goBack()">← Volver</button>
    </div>

    <!-- Pantalla: Editar Saldo -->
    <div id="editBalance" class="screen" style="display:none; padding:20px;">
      <h2 style="color:var(--purple); margin:20px 0;">Editar Saldo</h2>
      <div style="margin:15px 0;">
        <label style="display:block; margin-bottom:8px; color:white;">Saldo actual (S/)</label>
        <input type="number" id="editBalanceInput" value="27.00" style="width:100%; padding:12px; border-radius:8px; border:none; font-size:1em;">
      </div>
      <button class="big-button" onclick="saveBalance()">Guardar Saldo</button>
      <button class="big-button secondary" style="margin-top:10px;" onclick="goBack()">← Volver</button>
    </div>

    <!-- Escaneo QR -->
    <div id="scanScreen" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:black; justify-content:center; align-items:center; z-index:1000;">
      <div style="position:absolute; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.6);"></div>
      <div style="width:290px; height:290px; border:3px solid #00ff00; border-radius:18px; position:relative; overflow:hidden; z-index:2;">
        <div class="scan-line"></div>
      </div>
      <div style="position:absolute; top:20px; right:20px; background:white; width:44px; height:44px; border-radius:50%; display:flex; align-items:center; justify-content:center; cursor:pointer; z-index:3;" onclick="closeScan()">
        <i class="fas fa-times"></i>
      </div>
    </div>

    <!-- Chispas -->
    <div class="sparkles" id="sparkles"></div>

    <!-- Footer -->
    <div class="footer">
      Simulación con fines educativos<br>
      <strong>by AnthZz Berrocal</strong>
    </div>

  </div>

  <script>
    let balance = 27.00;
    let balanceVisible = false;

    function toggleMenu() {
      const sidebar = document.getElementById('menuSidebar');
      const overlay = document.getElementById('menuOverlay');
      sidebar.classList.toggle('active');
      overlay.style.display = sidebar.classList.contains('active') ? 'block' : 'none';
    }

    function toggleBalance() {
      const elem = document.getElementById('balanceAmount');
      if (balanceVisible) {
        elem.textContent = `S/ ${balance.toFixed(2)}`;
        document.querySelector('.balance-toggle span:nth-child(1)').textContent = 'Ocultar saldo';
        balanceVisible = false;
      } else {
        elem.textContent = '●●●●●●';
        document.querySelector('.balance-toggle span:nth-child(1)').textContent = 'Mostrar saldo';
        balanceVisible = true;
      }
    }

    function startScan() {
      document.getElementById('scanScreen').style.display = 'flex';
      setTimeout(() => {
        closeScan();
        const amount = (Math.random() * 60 + 10).toFixed(2);
        showSparkles();
        setTimeout(() => {
          alert(`✅ Pago realizado\nMonto: S/ ${amount}`);
          addToHistory('hamburger', 'Pago en comercio', `-S/ ${amount}`);
          balance -= parseFloat(amount);
          document.getElementById('balanceAmount').textContent = `S/ ${balance.toFixed(2)}`;
          document.getElementById('menuBalance').textContent = balance.toFixed(2);
        }, 500);
      }, 2500);
    }

    function closeScan() {
      document.getElementById('scanScreen').style.display = 'none';
    }

    function yapearPorNumero() {
      const phone = prompt("Ingresa número de celular");
      if (!phone || phone.length < 9) {
        alert("Número inválido");
        return;
      }
      const amount = prompt("Ingresa monto (S/)", "1");
      if (!amount || amount <= 0) {
        alert("Monto inválido");
        return;
      }
      showTransaction(phone, amount);
    }

    function showTransaction(phone, amount) {
      showScreen('transaction');
      document.getElementById('transAmount').textContent = amount;
      document.getElementById('transName').textContent = `Cintia Bernaola B.`;
      const now = new Date();
      document.getElementById('transDate').textContent = `${now.getDate()} ago. ${now.getFullYear()}`;
      document.getElementById('transTime').textContent = `${now.getHours()}:${now.getMinutes().toString().padStart(2, '0')} ${now.getHours() >= 12 ? 'p.m.' : 'a.m.'}`;
      document.getElementById('code1').textContent = Math.floor(Math.random() * 10);
      document.getElementById('code2').textContent = Math.floor(Math.random() * 10);
      document.getElementById('code3').textContent = Math.floor(Math.random() * 10);
      document.getElementById('transPhone').textContent = `*** *** ${phone.slice(-3)}`;
      document.getElementById('transOp').textContent = Math.floor(Math.random() * 90000000 + 10000000);
    }

    function goBack() {
      showScreen('home');
    }

    function showScreen(id) {
      document.querySelectorAll('.screen').forEach(s => s.style.display = 'none');
      document.getElementById(id).style.display = 'block';
    }

    function changePhoto() {
      const url = prompt('Ingresa URL de foto (o deja vacío para avatar)', '');
      if (url && url.trim() !== '') {
        document.getElementById('profilePic').src = url.trim();
        document.getElementById('menuProfilePic').src = url.trim();
      } else {
        const name = document.getElementById('editName').value || 'AnthZz Berrocal';
        const avatar = `https://ui-avatars.com/api/?name=${encodeURIComponent(name)}&background=7b1fa2&color=fff`;
        document.getElementById('profilePic').src = avatar;
        document.getElementById('menuProfilePic').src = avatar;
      }
    }

    function saveProfile() {
      const name = document.getElementById('editName').value;
      const nickname = document.getElementById('editNickname').value;
      if (!name) {
        alert('Nombre es obligatorio');
        return;
      }
      document.getElementById('menuName').textContent = name;
      alert('✅ Perfil actualizado');
      goBack();
    }

    function saveBalance() {
      const newBalance = parseFloat(document.getElementById('editBalanceInput').value);
      if (isNaN(newBalance) || newBalance < 0) {
        alert('Ingresa un saldo válido');
        return;
      }
      balance = newBalance;
      document.getElementById('balanceAmount').textContent = `S/ ${balance.toFixed(2)}`;
      document.getElementById('menuBalance').textContent = balance.toFixed(2);
      alert('✅ Saldo actualizado');
      goBack();
    }

    function addToHistory(icon, title, amount) {
      // (Opcional: agregar a historial real)
    }

    function showSparkles() {
      const container = document.getElementById('sparkles');
      container.style.display = 'block';
      for (let i = 0; i < 30; i++) {
        setTimeout(() => {
          const spark = document.createElement('div');
          spark.classList.add('spark');
          spark.style.left = Math.random() * 100 + 'vw';
          spark.style.opacity = Math.random();
          spark.style.width = spark.style.height = (Math.random() * 10 + 5) + 'px';
          spark.style.animationDuration = (Math.random() * 2 + 1) + 's';
          container.appendChild(spark);
          setTimeout(() => spark.remove(), 3000);
        }, i * 50);
      }
      setTimeout(() => container.style.display = 'none', 3000);
    }

    window.addEventListener('load', () => {
      showScreen('home');
    });
  </script>
</body>
</html>
