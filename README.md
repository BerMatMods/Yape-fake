
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
  <title>Yape</title>
  <!-- Corregido: espacio extra eliminado -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">
  <style>
    :root {
      --primary: #9c27b0;
      --primary-light: #f3e5f5;
      --white: #ffffff;
      --bg: #f5f5f5;
      --text: #333333;
      --text-secondary: #5f5f5f;
      --border: #e0e0e0;
      --shadow: 0 1px 6px rgba(0,0,0,0.1);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', -apple-system, sans-serif;
    }

    body {
      background-color: var(--bg);
      color: var(--text);
      -webkit-font-smoothing: antialiased;
    }

    .container {
      max-width: 414px;
      margin: 0 auto;
      background: var(--white);
      min-height: 100vh;
      position: relative;
      box-shadow: var(--shadow);
      overflow: hidden;
    }

    /* Header */
    .top-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 14px 16px;
      background: var(--white);
      border-bottom: 1px solid var(--border);
      position: sticky;
      top: 0;
      z-index: 100;
    }

    .top-bar h1 {
      font-size: 1.55em;
      color: var(--primary);
      font-weight: 700;
    }

    .top-bar .icons {
      display: flex;
      gap: 20px;
      position: relative;
    }

    .top-bar .notification-dot {
      position: absolute;
      top: 12px;
      right: 8px;
      width: 8px;
      height: 8px;
      background: red;
      border-radius: 50%;
    }

    /* Saldo */
    .balance-section {
      text-align: center;
      padding: 30px 20px 24px;
      background: var(--primary);
      color: white;
    }

    .balance-label {
      font-size: 0.9em;
      opacity: 0.9;
    }

    .balance-amount {
      font-size: 3.1em;
      font-weight: bold;
      margin: 10px 0;
      letter-spacing: -1px;
    }

    .show-hide {
      font-size: 0.95em;
      opacity: 0.95;
      cursor: pointer;
      text-decoration: underline;
    }

    /* Servicios */
    .quick-services {
      display: flex;
      flex-wrap: wrap;
      padding: 14px 10px 12px;
      gap: 14px;
      justify-content: center;
    }

    .service-item {
      width: 72px;
      text-align: center;
      font-size: 0.82em;
      color: var(--text-secondary);
    }

    .service-icon {
      width: 52px;
      height: 52px;
      background: var(--primary-light);
      border-radius: 14px;
      margin: 0 auto 7px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--primary);
      font-size: 1.35em;
    }

    /* Botones */
    .big-button {
      margin: 16px 20px 10px;
      background: var(--primary);
      color: white;
      border: none;
      padding: 16px;
      border-radius: 13px;
      font-size: 1.12em;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 11px;
      box-shadow: 0 4px 12px rgba(156, 39, 176, 0.3);
    }

    .big-button:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 16px rgba(156, 39, 176, 0.4);
    }

    .big-button.secondary {
      background: var(--white);
      color: var(--primary);
      border: 1.5px solid var(--primary);
    }

    /* Movimientos */
    .movements {
      padding: 16px;
    }

    .movement-item {
      display: flex;
      padding: 14px 0;
      border-bottom: 1px solid #f0f0f0;
    }

    .movement-icon {
      width: 44px;
      height: 44px;
      background: var(--primary-light);
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--primary);
      margin-right: 14px;
    }

    .movement-info {
      flex: 1;
    }

    .movement-title {
      font-weight: 600;
      font-size: 0.98em;
    }

    .movement-date {
      font-size: 0.83em;
      color: #888;
    }

    .movement-amount {
      font-weight: 600;
      color: var(--primary);
    }

    /* Formulario */
    .form-group {
      margin: 15px 0;
    }

    .form-group label {
      display: block;
      margin-bottom: 8px;
      color: var(--text-secondary);
      font-size: 0.9em;
    }

    .form-group input, .form-group textarea {
      width: 100%;
      padding: 12px;
      border: 1px solid var(--border);
      border-radius: 8px;
      font-size: 1em;
    }

    /* Ajustes */
    .setting-item {
      padding: 15px;
      border-bottom: 1px solid var(--border);
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .setting-item i {
      color: var(--primary);
      font-size: 1.3em;
    }

    .setting-text {
      flex: 1;
    }

    .setting-label {
      font-weight: 500;
    }

    .setting-desc {
      font-size: 0.8em;
      color: #888;
    }

    /* Perfil */
    .profile-header {
      text-align: center;
      margin-bottom: 20px;
    }

    .profile-pic {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      margin: 20px auto 10px;
      background: #ddd;
      background-size: cover;
      background-position: center;
      cursor: pointer;
      border: 3px solid var(--primary);
    }

    /* Pantallas */
    .screen {
      display: none;
      padding-bottom: 80px;
    }

    .screen.active {
      display: block;
    }

    /* Animaciones */
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes pop {
      0% { transform: scale(1); }
      50% { transform: scale(1.05); }
      100% { transform: scale(1); }
    }

    .pop {
      animation: pop 0.3s ease-in-out;
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

    /* Escaneo */
    .scan-screen {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #000;
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }

    .scan-overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.6);
    }

    .scan-frame {
      width: 290px;
      height: 290px;
      border: 3px solid #00ff00;
      border-radius: 18px;
      position: relative;
      z-index: 2;
      overflow: hidden;
      box-shadow: 0 0 25px rgba(0,255,0,0.5);
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

    @keyframes scanLine {
      0% { top: 0; }
      100% { top: 285px; }
    }

    .scan-close {
      position: absolute;
      top: 20px;
      right: 20px;
      background: white;
      color: black;
      width: 44px;
      height: 44px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 3;
      cursor: pointer;
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

    <!-- Header -->
    <div class="top-bar">
      <h1>Yape</h1>
      <div class="icons">
        <i class="fas fa-bell"></i>
        <div class="notification-dot"></div>
      </div>
    </div>

    <!-- Pantalla: Inicio -->
    <div id="home" class="screen active">
      <div class="balance-section">
        <div class="balance-label">Saldo disponible</div>
        <div class="balance-amount" id="balanceAmount">S/ 3,500.00</div>
        <div class="show-hide" onclick="toggleBalance()">●●●●●●</div>
      </div>

      <div class="quick-services">
        <div class="service-item" onclick="startScan()">
          <div class="service-icon"><i class="fas fa-qrcode"></i></div>
          <div>Yapear</div>
        </div>
        <div class="service-item" onclick="alert('Recarga de celular')">
          <div class="service-icon"><i class="fas fa-mobile-alt"></i></div>
          <div>Recarga</div>
        </div>
        <div class="service-item" onclick="alert('Pagar servicio')">
          <div class="service-icon"><i class="fas fa-bolt"></i></div>
          <div>Yapear servicio</div>
        </div>
        <div class="service-item" onclick="alert('Transferir a primos')">
          <div class="service-icon"><i class="fas fa-users"></i></div>
          <div>Primos</div>
        </div>
        <div class="service-item" onclick="showScreen('settings')">
          <div class="service-icon"><i class="fas fa-cog"></i></div>
          <div>Ajustes</div>
        </div>
        <div class="service-item" onclick="alert('Ver tiendas cercanas')">
          <div class="service-icon"><i class="fas fa-store"></i></div>
          <div>Tiendas</div>
        </div>
        <div class="service-item" onclick="alert('Comprar dólares')">
          <div class="service-icon"><i class="fas fa-dollar-sign"></i></div>
          <div>Dólares</div>
        </div>
        <div class="service-item" onclick="alert('Enviar remesas')">
          <div class="service-icon"><i class="fas fa-globe-americas"></i></div>
          <div>Remesas</div>
        </div>
        <div class="service-item" onclick="alert('Pagar SOAT')">
          <div class="service-icon"><i class="fas fa-car"></i></div>
          <div>SOAT</div>
        </div>
        <div class="service-item" onclick="alert('Comprar pasaje')">
          <div class="service-icon"><i class="fas fa-bus"></i></div>
          <div>Bus</div>
        </div>
        <div class="service-item" onclick="alert('Configurar biométrica')">
          <div class="service-icon"><i class="fas fa-fingerprint"></i></div>
          <div>Biométrica</div>
        </div>
        <div class="service-item" onclick="alert('Ver todos los servicios')">
          <div class="service-icon"><i class="fas fa-ellipsis-h"></i></div>
          <div>Ver todo</div>
        </div>
      </div>

      <button class="big-button pop" onclick="startScan()">
        <i class="fas fa-qrcode"></i> Yapear con QR
      </button>
      <button class="big-button secondary" onclick="showScreen('sendByNumber')">
        <i class="fas fa-mobile-alt"></i> Yapear por número
      </button>

      <div class="movements">
        <h3 style="margin-bottom:16px; color:var(--text-secondary);">Historial de movimientos</h3>
        <div id="movementsList">
          <!-- Movimientos dinámicos -->
          <div class="movement-item">
            <div class="movement-icon"><i class="fas fa-arrow-down"></i></div>
            <div class="movement-info">
              <div class="movement-title">Saldo inicial</div>
              <div class="movement-date">Hoy, 00:00</div>
            </div>
            <div class="movement-amount" style="color:var(--primary);">+S/ 800.00</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Pantalla: Enviar por número -->
    <div id="sendByNumber" class="screen">
      <h2 style="margin:22px 0; color:var(--primary);">Yapear por número</h2>
      <div class="form-group">
        <label>Número de celular</label>
        <input type="tel" id="phoneNumber" placeholder="987 654 321">
      </div>
      <div class="form-group">
        <label>Monto (S/)</label>
        <input type="number" id="sendAmount" placeholder="0.00">
      </div>
      <button class="big-button" onclick="sendByNumber()">Enviar Dinero</button>
      <button class="big-button secondary" style="margin-top:12px;" onclick="showScreen('home')">← Volver</button>
    </div>

    <!-- Pantalla: Ajustes -->
    <div id="settings" class="screen">
      <h2 style="margin:20px 16px; color:var(--primary);">Ajustes</h2>

      <div class="setting-item" onclick="showScreen('profile')">
        <i class="fas fa-user"></i>
        <div class="setting-text">
          <div class="setting-label">Perfil</div>
          <div class="setting-desc">Editar información personal</div>
        </div>
      </div>

      <div class="setting-item" onclick="showScreen('editBalance')">
        <i class="fas fa-wallet"></i>
        <div class="setting-text">
          <div class="setting-label">Editar Saldo</div>
          <div class="setting-desc">Modificar tu saldo disponible</div>
        </div>
      </div>

      <div class="setting-item">
        <i class="fas fa-bell"></i>
        <div class="setting-text">
          <div class="setting-label">Notificaciones</div>
          <div class="setting-desc">Activadas</div>
        </div>
        <i class="fas fa-toggle-on" style="color:var(--primary);"></i>
      </div>

      <div class="setting-item">
        <i class="fas fa-shield-alt"></i>
        <div class="setting-text">
          <div class="setting-label">Seguridad</div>
          <div class="setting-desc">PIN, huella, facial</div>
        </div>
      </div>

      <div class="setting-item">
        <i class="fas fa-info-circle"></i>
        <div class="setting-text">
          <div class="setting-label">Información de la app</div>
          <div class="setting-desc">Yape Fake v2.5 - By: BerMatMods</div>
        </div>
      </div>

      <button class="big-button secondary" style="margin:20px;" onclick="showScreen('home')">← Volver</button>
    </div>

    <!-- Pantalla: Perfil -->
    <div id="profile" class="screen">
      <div class="profile-header">
        <!-- Corregido: espacio eliminado en URL -->
        <img src="https://ui-avatars.com/api/?name=AnthZz+Berrocal&background=9c27b0&color=fff" alt="Foto" class="profile-pic" id="profilePic" onclick="changePhoto()">
        <h2>AnthZz Berrocal</h2>
        <p>_BerMat_Mods</p>
      </div>

      <div class="form-group">
        <label>Nombre completo</label>
        <input type="text" id="editName" value="AnthZz Berrocal">
      </div>
      <div class="form-group">
        <label>Apodo</label>
        <input type="text" id="editNickname" value="_BerMat_Mods">
      </div>
      <div class="form-group">
        <label>Email</label>
        <input type="email" id="editEmail" value="anthzz@bermatmods.dev">
      </div>
      <div class="form-group">
        <label>Teléfono</label>
        <input type="tel" id="editPhone" value="+51 999 888 777">
      </div>
      <button class="big-button" onclick="saveProfile()">Guardar Cambios</button>
      <button class="big-button secondary" style="margin-top:10px;" onclick="showScreen('settings')">← Ajustes</button>
    </div>

    <!-- Pantalla: Editar Saldo -->
    <div id="editBalance" class="screen">
      <h2 style="margin:20px 16px; color:var(--primary);">Editar Saldo</h2>
      <div class="form-group">
        <label>Saldo actual (S/)</label>
        <input type="number" id="editBalanceInput" value="3500.00">
      </div>
      <button class="big-button" onclick="saveBalance()">Guardar Saldo</button>
      <button class="big-button secondary" style="margin-top:10px;" onclick="showScreen('settings')">← Ajustes</button>
    </div>

    <!-- Escaneo -->
    <div id="scanScreen" class="scan-screen">
      <div class="scan-overlay"></div>
      <div class="scan-frame">
        <div class="scan-line"></div>
      </div>
      <div class="scan-close" onclick="closeScan()">
        <i class="fas fa-times"></i>
      </div>
    </div>

    <!-- Chispas -->
    <div class="sparkles" id="sparkles"></div>

    <!-- Footer -->
    <div class="footer">
      BerMatMods<br>
      <strong>by AnthZz Berrocal</strong>
    </div>

  </div>

  <script>
    let balance = 3500.00;
    let balanceVisible = false;
    let movements = [
      { icon: 'arrow-down', title: 'Saldo inicial', amount: '+S/ 3,500.00', date: 'Hoy, 00:00' }
    ];

    function toggleBalance() {
      const elem = document.getElementById('balanceAmount');
      if (balanceVisible) {
        elem.textContent = `S/ ${balance.toFixed(2)}`;
        document.querySelector('.show-hide').textContent = '●●●●●●';
        balanceVisible = false;
      } else {
        elem.textContent = '●●●●●●';
        document.querySelector('.show-hide').textContent = 'Mostrar';
        balanceVisible = true;
      }
    }

    function showScreen(id) {
      document.querySelectorAll('.screen').forEach(s => s.style.display = 'none');
      document.getElementById(id).style.display = 'block';
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
        }, 500);
      }, 2500);
    }

    function closeScan() {
      document.getElementById('scanScreen').style.display = 'none';
    }

    function sendByNumber() {
      const phone = document.getElementById('phoneNumber').value;
      const amount = document.getElementById('sendAmount').value;
      if (!phone || phone.length < 9) {
        alert('Número inválido');
        return;
      }
      if (!amount || amount <= 0) {
        alert('Monto inválido');
        return;
      }
      showSparkles();
      setTimeout(() => {
        alert(`✅ Enviado S/ ${amount} a ${phone}`);
        addToHistory('mobile-alt', `Enviado a ${phone.slice(-3)}`, `-S/ ${amount}`);
        balance -= parseFloat(amount);
        document.getElementById('balanceAmount').textContent = `S/ ${balance.toFixed(2)}`;
        document.getElementById('phoneNumber').value = '';
        document.getElementById('sendAmount').value = '';
        showScreen('home');
      }, 600);
    }

    function saveProfile() {
      const name = document.getElementById('editName').value;
      const nickname = document.getElementById('editNickname').value;
      if (!name) {
        alert('Nombre es obligatorio');
        return;
      }
      document.querySelector('#profile h2').textContent = name;
      document.querySelector('#profile p').textContent = nickname;
      alert('✅ Perfil actualizado');
      showScreen('settings');
    }

    function saveBalance() {
      const newBalance = parseFloat(document.getElementById('editBalanceInput').value);
      if (isNaN(newBalance) || newBalance < 0) {
        alert('Ingresa un saldo válido');
        return;
      }
      const diff = newBalance - balance;
      balance = newBalance;
      document.getElementById('balanceAmount').textContent = `S/ ${balance.toFixed(2)}`;
      addToHistory('wallet', 'Saldo editado', diff >= 0 ? `+S/ ${diff.toFixed(2)}` : `-S/ ${Math.abs(diff).toFixed(2)}`);
      alert('✅ Saldo actualizado');
      showScreen('settings');
    }

    function addToHistory(icon, title, amount) {
      const now = new Date();
      const time = now.getHours().toString().padStart(2, '0') + ':' + now.getMinutes().toString().padStart(2, '0');
      movements.push({ icon, title, amount, date: `Hoy, ${time}` });
      renderMovements();
    }

    function renderMovements() {
      const container = document.getElementById('movementsList');
      container.innerHTML = '';
      // Más reciente arriba
      movements.slice().reverse().forEach(m => {
        const item = document.createElement('div');
        item.className = 'movement-item';
        item.innerHTML = `
          <div class="movement-icon"><i class="fas fa-${m.icon}"></i></div>
          <div class="movement-info">
            <div class="movement-title">${m.title}</div>
            <div class="movement-date">${m.date}</div>
          </div>
          <div class="movement-amount">${m.amount}</div>
        `;
        container.appendChild(item);
      });
    }

    function changePhoto() {
      const url = prompt('Ingresa URL de foto (o deja vacío para avatar)', '');
      if (url && url.trim() !== '') {
        document.getElementById('profilePic').src = url.trim();
      } else {
        const name = document.getElementById('editName').value || 'AnthZz Berrocal';
        document.getElementById('profilePic').src = `https://ui-avatars.com/api/?name=${encodeURIComponent(name)}&background=9c27b0&color=fff`;
      }
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

    // Iniciar
    window.addEventListener('load', () => {
      showScreen('home');
      renderMovements();
    });
  </script>
</body>
</html>
