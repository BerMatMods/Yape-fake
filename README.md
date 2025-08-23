
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
      display: none; /* Oculto por defecto */
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
        <div class="service-item" onclick="showScreen('settings')">
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
          <span>S/ 27.00</span>
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
        <div class="transaction-amount">S/ 1</div>
        <div class="transaction-name">Cintia Bernaola B.</div>
        <div class="transaction-date">
          <i class="fas fa-calendar"></i> 22 ago. 2025 | <i class="fas fa-clock"></i> 10:35 p.m.
        </div>

        <div class="security-code">
          <span>CÓDIGO DE SEGURIDAD</span>
          <i class="fas fa-info-circle"></i>
          <div class="security-digits">
            <div class="digit">4</div>
            <div class="digit">6</div>
            <div class="digit">4</div>
          </div>
        </div>

        <div class="transaction-details">
          <div class="detail-row">
            <span>Nro. de celular</span>
            <span>*** *** 777</span>
          </div>
          <div class="detail-row">
            <span>Destino</span>
            <span>Yape</span>
          </div>
          <div class="detail-row">
            <span>Nro. de operación</span>
            <span>25422464</span>
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

    <!-- Pantallas ocultas (mantenemos tu lógica) -->
    <div id="sendByNumber" class="screen" style="display:none;">
      <input type="tel" id="phoneNumber">
      <input type="number" id="sendAmount">
    </div>

    <div id="settings" class="screen" style="display:none;">
      <h2>Ajustes</h2>
    </div>

    <div id="profile" class="screen" style="display:none;">
      <h2>Perfil</h2>
    </div>

    <div id="editBalance" class="screen" style="display:none;">
      <h2>Editar Saldo</h2>
    </div>

    <!-- Escaneo QR -->
    <div id="scanScreen" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:black; justify-content:center; align-items:center; z-index:1000;">
      <div style="width:290px; height:290px; border:3px solid #00ff00; border-radius:18px;"></div>
      <div style="position:absolute; top:20px; right:20px; background:white; width:44px; height:44px; border-radius:50%; display:flex; align-items:center; justify-content:center; cursor:pointer;" onclick="document.getElementById('scanScreen').style.display='none';">
        <i class="fas fa-times"></i>
      </div>
    </div>

    <!-- Chispas -->
    <div class="sparkles" id="sparkles" style="position:fixed; top:0; left:0; width:100%; height:100%; pointer-events:none; z-index:1001; display:none;"></div>

    <!-- Footer -->
    <div class="footer">
      Simulación con fines educativos<br>
      <strong>by AnthZz Berrocal</strong>
    </div>

  </div>

  <!-- Mantenemos TODO tu JavaScript original -->
  <script>
    let balance = 27.00;
    let balanceVisible = false;
    let movements = [
      { icon: 'arrow-down', title: 'Saldo inicial', amount: '+S/ 27.00', date: 'Hoy, 00:00' }
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

    function yapearPorNumero() {
      const phone = prompt("Ingresa número de celular");
      const amount = prompt("Ingresa monto");
      if (!phone || !amount || amount <= 0) {
        alert("Datos inválidos");
        return;
      }
      showTransaction(phone, amount);
    }

    function showTransaction(phone, amount) {
      showScreen('transaction');
      document.querySelector('.transaction-amount').textContent = `S/ ${amount}`;
      document.querySelector('.transaction-name').textContent = `Cintia Bernaola B.`;
      document.querySelector('.transaction-date').innerHTML = `<i class="fas fa-calendar"></i> 22 ago. 2025 | <i class="fas fa-clock"></i> 10:35 p.m.`;
      document.querySelector('.security-digits').innerHTML = `
        <div class="digit">${Math.floor(Math.random() * 10)}</div>
        <div class="digit">${Math.floor(Math.random() * 10)}</div>
        <div class="digit">${Math.floor(Math.random() * 10)}</div>
      `;
      document.querySelector('.detail-row:nth-child(1) span:nth-child(2)').textContent = `*** *** ${phone.slice(-3)}`;
    }

    function goBack() {
      showScreen('home');
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

    window.addEventListener('load', () => {
      showScreen('home');
      renderMovements();
    });
  </script>
</body>
</html>
