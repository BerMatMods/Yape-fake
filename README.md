
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BerMatMods Tech Store</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700;900&family=Roboto:wght@300;400;500&display=swap');
        
        :root {
            --primary: #00ff88;
            --secondary: #0066ff;
            --dark: #0a0a1a;
            --darker: #05050f;
            --light: #f0f0f0;
            --purple: #8a2be2;
            --pink: #ff00ff;
            --blue: #00ffff;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            cursor: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="%2300ff88"><circle cx="12" cy="12" r="10" stroke="%2300ff88" stroke-width="2" fill="none"/><circle cx="12" cy="12" r="4" fill="%2300ff88"/></svg>'), auto;
        }
        
        body {
            background: linear-gradient(135deg, var(--darker), var(--dark)) fixed;
            color: var(--light);
            font-family: 'Roboto', sans-serif;
            min-height: 100vh;
            overflow-x: hidden;
            background-attachment: fixed;
        }
        
        /* Animaciones */
        @keyframes neon-pulse {
            0%, 100% { text-shadow: 0 0 10px var(--primary), 0 0 20px var(--primary), 0 0 30px var(--primary); }
            50% { text-shadow: 0 0 5px var(--primary), 0 0 10px var(--primary), 0 0 15px var(--primary); }
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        @keyframes glow {
            0%, 100% { box-shadow: 0 0 15px var(--primary), 0 0 30px rgba(0, 255, 136, 0.3); }
            50% { box-shadow: 0 0 25px var(--primary), 0 0 50px rgba(0, 255, 136, 0.5); }
        }
        
        @keyframes flicker {
            0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% { opacity: 1; }
            20%, 22%, 24%, 55% { opacity: 0.5; }
        }
        
        /* Header */
        .header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            background: rgba(10, 10, 26, 0.9);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(0, 255, 136, 0.3);
            animation: glow 2s infinite alternate;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
            font-family: 'Orbitron', sans-serif;
            font-weight: 900;
            font-size: 28px;
            color: var(--primary);
            animation: neon-pulse 2s infinite alternate;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        
        .logo-icon {
            width: 50px;
            height: 50px;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            animation: rotate 10s linear infinite;
        }
        
        .logo-icon::before {
            content: "A";
            color: white;
            font-weight: bold;
            font-size: 24px;
        }
        
        .nav {
            display: flex;
            gap: 30px;
        }
        
        .nav-item {
            color: var(--light);
            text-decoration: none;
            font-size: 18px;
            position: relative;
            padding: 5px 0;
            transition: all 0.3s;
        }
        
        .nav-item:hover {
            color: var(--primary);
        }
        
        .nav-item::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary);
            transition: width 0.3s;
        }
        
        .nav-item:hover::after {
            width: 100%;
        }
        
        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            padding: 0 20px;
            overflow: hidden;
        }
        
        .hero-content {
            text-align: center;
            max-width: 800px;
            z-index: 10;
        }
        
        .hero-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 5rem;
            font-weight: 900;
            margin-bottom: 20px;
            line-height: 1;
            color: white;
            text-shadow: 0 0 20px rgba(0, 255, 136, 0.5);
            animation: neon-pulse 2s infinite alternate;
        }
        
        .hero-subtitle {
            font-size: 1.5rem;
            margin-bottom: 40px;
            color: var(--light);
            opacity: 0.9;
        }
        
        .hero-info {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-bottom: 40px;
            flex-wrap: wrap;
        }
        
        .info-item {
            background: rgba(10, 10, 26, 0.7);
            padding: 15px 25px;
            border-radius: 10px;
            border: 1px solid rgba(0, 255, 136, 0.3);
            backdrop-filter: blur(10px);
            animation: glow 3s infinite alternate;
        }
        
        .info-label {
            font-size: 14px;
            color: var(--primary);
            margin-bottom: 5px;
        }
        
        .info-value {
            font-size: 18px;
            font-weight: bold;
        }
        
        .cta-button {
            display: inline-block;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: white;
            padding: 15px 40px;
            border-radius: 50px;
            font-size: 18px;
            font-weight: bold;
            text-decoration: none;
            margin: 10px;
            transition: all 0.3s;
            border: none;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            animation: glow 2s infinite alternate;
        }
        
        .cta-button:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 255, 136, 0.3);
        }
        
        .cta-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }
        
        .cta-button:hover::before {
            left: 100%;
        }
        
        /* Products Section */
        .products {
            padding: 100px 20px;
            max-width: 1400px;
            margin: 0 auto;
        }
        
        .section-title {
            text-align: center;
            font-family: 'Orbitron', sans-serif;
            font-size: 3rem;
            margin-bottom: 60px;
            color: var(--primary);
            animation: neon-pulse 2s infinite alternate;
            position: relative;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: var(--primary);
            box-shadow: 0 0 10px var(--primary);
        }
        
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 60px;
        }
        
        .product-card {
            background: rgba(10, 10, 26, 0.7);
            border-radius: 15px;
            overflow: hidden;
            transition: all 0.5s;
            border: 1px solid rgba(0, 255, 136, 0.3);
            backdrop-filter: blur(10px);
            position: relative;
        }
        
        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 255, 136, 0.2);
        }
        
        .product-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent, rgba(0, 255, 136, 0.1), transparent);
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .product-card:hover::before {
            opacity: 1;
        }
        
        .product-image {
            height: 200px;
            background: linear-gradient(45deg, var(--secondary), var(--purple));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 60px;
        }
        
        .product-content {
            padding: 25px;
        }
        
        .product-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5rem;
            margin-bottom: 10px;
            color: var(--primary);
        }
        
        .product-category {
            color: var(--blue);
            font-size: 14px;
            margin-bottom: 15px;
            display: inline-block;
            padding: 5px 10px;
            background: rgba(0, 255, 255, 0.1);
            border-radius: 5px;
        }
        
        .product-description {
            color: var(--light);
            opacity: 0.8;
            margin-bottom: 20px;
            font-size: 14px;
            line-height: 1.5;
        }
        
        .product-features {
            list-style: none;
            margin-bottom: 20px;
        }
        
        .product-features li {
            color: var(--light);
            font-size: 14px;
            margin-bottom: 8px;
            position: relative;
            padding-left: 20px;
        }
        
        .product-features li::before {
            content: '✓';
            color: var(--primary);
            position: absolute;
            left: 0;
            font-weight: bold;
        }
        
        .vip-tag {
            position: absolute;
            top: 15px;
            right: 15px;
            background: linear-gradient(45deg, var(--pink), var(--purple));
            color: white;
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 12px;
            font-weight: bold;
            animation: neon-pulse 2s infinite alternate;
        }
        
        /* Features Section */
        .features {
            padding: 80px 20px;
            background: rgba(5, 5, 15, 0.5);
            margin: 60px 0;
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .feature-card {
            text-align: center;
            padding: 30px;
            background: rgba(10, 10, 26, 0.7);
            border-radius: 15px;
            border: 1px solid rgba(0, 255, 136, 0.3);
            transition: all 0.3s;
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 255, 136, 0.2);
        }
        
        .feature-icon {
            font-size: 50px;
            margin-bottom: 20px;
            color: var(--primary);
            animation: float 3s ease-in-out infinite;
        }
        
        .feature-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: var(--primary);
        }
        
        .feature-desc {
            color: var(--light);
            opacity: 0.8;
            line-height: 1.6;
        }
        
        /* Registration Section */
        .registration {
            padding: 100px 20px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .register-container {
            max-width: 600px;
            margin: 0 auto;
            background: rgba(10, 10, 26, 0.8);
            border-radius: 20px;
            padding: 40px;
            border: 1px solid rgba(0, 255, 136, 0.3);
            backdrop-filter: blur(10px);
            position: relative;
            z-index: 10;
        }
        
        .register-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            margin-bottom: 30px;
            color: var(--primary);
            animation: neon-pulse 2s infinite alternate;
        }
        
        .google-signin {
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .google-signin:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-3px);
        }
        
        .google-icon {
            width: 30px;
            height: 30px;
            background: white;
            border-radius: 50%;
            margin-right: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: #ea4335;
        }
        
        .form-group {
            margin-bottom: 20px;
            text-align: left;
        }
        
        .form-label {
            display: block;
            margin-bottom: 8px;
            color: var(--light);
            font-size: 14px;
        }
        
        .form-input {
            width: 100%;
            padding: 15px;
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(0, 255, 136, 0.3);
            border-radius: 10px;
            color: white;
            font-size: 16px;
            transition: all 0.3s;
        }
        
        .form-input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 10px rgba(0, 255, 136, 0.5);
        }
        
        .vip-options {
            margin: 30px 0;
            text-align: center;
        }
        
        .vip-options h3 {
            color: var(--pink);
            margin-bottom: 20px;
            font-family: 'Orbitron', sans-serif;
        }
        
        .vip-plans {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }
        
        .vip-plan {
            background: rgba(10, 10, 26, 0.7);
            border: 1px solid rgba(138, 43, 226, 0.5);
            border-radius: 15px;
            padding: 20px;
            width: 200px;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }
        
        .vip-plan:hover {
            transform: translateY(-10px);
            border-color: var(--pink);
        }
        
        .vip-plan.popular {
            border: 2px solid var(--pink);
            transform: scale(1.05);
            z-index: 1;
        }
        
        .vip-plan.popular::before {
            content: 'MÁS POPULAR';
            position: absolute;
            top: 10px;
            right: -30px;
            background: var(--pink);
            color: white;
            padding: 5px 30px;
            transform: rotate(45deg);
            font-size: 12px;
            font-weight: bold;
        }
        
        .vip-name {
            font-family: 'Orbitron', sans-serif;
            color: var(--pink);
            font-size: 1.3rem;
            margin-bottom: 15px;
        }
        
        .vip-price {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary);
            margin-bottom: 20px;
        }
        
        .vip-features {
            list-style: none;
            margin-bottom: 20px;
        }
        
        .vip-features li {
            color: var(--light);
            margin-bottom: 10px;
            font-size: 14px;
        }
        
        .vip-features li::before {
            content: '✓';
            color: var(--primary);
            margin-right: 8px;
        }
        
        /* Footer */
        .footer {
            background: rgba(5, 5, 15, 0.8);
            padding: 60px 20px 30px;
            border-top: 1px solid rgba(0, 255, 136, 0.3);
            position: relative;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
        }
        
        .footer-column h3 {
            font-family: 'Orbitron', sans-serif;
            color: var(--primary);
            margin-bottom: 20px;
            font-size: 1.5rem;
            animation: neon-pulse 2s infinite alternate;
        }
        
        .footer-links {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 10px;
        }
        
        .footer-links a {
            color: var(--light);
            text-decoration: none;
            transition: all 0.3s;
            opacity: 0.8;
        }
        
        .footer-links a:hover {
            color: var(--primary);
            opacity: 1;
        }
        
        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }
        
        .social-link {
            width: 40px;
            height: 40px;
            background: rgba(0, 255, 136, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary);
            text-decoration: none;
            transition: all 0.3s;
            border: 1px solid rgba(0, 255, 136, 0.3);
        }
        
        .social-link:hover {
            background: var(--primary);
            color: var(--dark);
            transform: translateY(-5px);
        }
        
        .copyright {
            text-align: center;
            margin-top: 60px;
            padding-top: 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--light);
            opacity: 0.7;
            font-size: 14px;
        }
        
        .credits {
            color: var(--primary);
            font-weight: bold;
        }
        
        /* Background Elements */
        .bg-element {
            position: absolute;
            opacity: 0.1;
            pointer-events: none;
            z-index: 1;
        }
        
        .circle {
            border-radius: 50%;
            background: var(--primary);
        }
        
        .line {
            background: var(--primary);
            transform: rotate(45deg);
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .hero-title {
                font-size: 3rem;
            }
            
            .hero-info {
                flex-direction: column;
                gap: 15px;
            }
            
            .nav {
                display: none;
            }
            
            .header {
                justify-content: center;
            }
            
            .vip-plans {
                flex-direction: column;
                align-items: center;
            }
            
            .vip-plan.popular {
                transform: scale(1);
            }
        }
        
        /* Cursor trail */
        .cursor-trail {
            position: fixed;
            pointer-events: none;
            z-index: 9999;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
        }
        
        .trail-dot {
            position: absolute;
            width: 5px;
            height: 5px;
            background: var(--primary);
            border-radius: 50%;
            pointer-events: none;
            opacity: 0;
        }
    </style>
</head>
<body>
    <!-- Cursor Trail -->
    <div class="cursor-trail" id="cursorTrail"></div>
    
    <!-- Background Elements -->
    <div class="bg-element circle" style="width: 200px; height: 200px; top: 10%; left: 10%;"></div>
    <div class="bg-element circle" style="width: 150px; height: 150px; top: 70%; left: 20%;"></div>
    <div class="bg-element circle" style="width: 100px; height: 100px; top: 30%; right: 15%;"></div>
    <div class="bg-element circle" style="width: 80px; height: 80px; bottom: 20%; left: 30%;"></div>
    <div class="bg-element line" style="width: 200px; height: 2px; top: 50%; right: 10%;"></div>
    <div class="bg-element line" style="width: 150px; height: 2px; bottom: 40%; left: 15%; transform: rotate(60deg);"></div>
    
    <!-- Header -->
    <header class="header">
        <div class="logo">
            <div class="logo-icon"></div>
            <span>AnthZz Berrocal</span>
        </div>
        <nav class="nav">
            <a href="#products" class="nav-item">Productos</a>
            <a href="#features" class="nav-item">Características</a>
            <a href="#vip" class="nav-item">VIP</a>
            <a href="#register" class="nav-item">Registro</a>
        </nav>
    </header>
    
    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <h1 class="hero-title">TECH STORE</h1>
            <p class="hero-subtitle">La tienda definitiva para entusiastas de la tecnología, ciberseguridad y hacking ético. Productos exclusivos para usuarios avanzados.</p>
            
            <div class="hero-info">
                <div class="info-item">
                    <div class="info-label">FUNDADOR</div>
                    <div class="info-value">AnthZz Berrocal</div>
                </div>
                <div class="info-item">
                    <div class="info-label">EMAIL</div>
                    <div class="info-value">antonioberrocal62@gmail.com</div>
                </div>
                <div class="info-item">
                    <div class="info-label">CLIENTES VIP</div>
                    <div class="info-value">2,347+</div>
                </div>
                <div class="info-item">
                    <div class="info-label">PAÍSES</div>
                    <div class="info-value">47+</div>
                </div>
            </div>
            
            <div>
                <a href="#products" class="cta-button">Explorar Productos</a>
                <a href="#register" class="cta-button">Unirse Ahora</a>
            </div>
        </div>
    </section>
    
    <!-- Products Section -->
    <section class="products" id="products">
        <h2 class="section-title">Productos Tecnológicos</h2>
        
        <div class="products-grid">
            <div class="product-card">
                <div class="product-image">🛡️</div>
                <div class="product-content">
                    <h3 class="product-title">Kit de Hacking Ético Pro</h3>
                    <span class="product-category">Ciberseguridad</span>
                    <p class="product-description">Kit profesional para pentesting y auditorías de seguridad, incluye herramientas avanzadas para profesionales de ciberseguridad.</p>
                    <ul class="product-features">
                        <li>Acceso a herramientas premium</li>
                        <li>Actualizaciones mensuales</li>
                        <li>Soporte 24/7</li>
                        <li>Documentación completa</li>
                    </ul>
                </div>
            </div>
            
            <div class="product-card">
                <div class="product-image">💻</div>
                <div class="product-content">
                    <h3 class="product-title">Curso Avanzado de Ciberseguridad</h3>
                    <span class="product-category">Educación</span>
                    <p class="product-description">Curso completo de ciberseguridad con certificación oficial, desde principiante hasta nivel experto.</p>
                    <ul class="product-features">
                        <li>120 horas de contenido</li>
                        <li>Certificación incluida</li>
                        <li>Proyectos reales</li>
                        <li>Acceso vitalicio</li>
                    </ul>
                </div>
            </div>
            
            <div class="product-card">
                <div class="product-image">📡</div>
                <div class="product-content">
                    <h3 class="product-title">Dispositivo de Seguridad IoT</h3>
                    <span class="product-category">Hardware</span>
                    <p class="product-description">Dispositivo de protección para redes IoT, previene ataques y monitorea tráfico en tiempo real.</p>
                    <ul class="product-features">
                        <li>Detección de intrusos</li>
                        <li>Protección en tiempo real</li>
                        <li>Interfaz intuitiva</li>
                        <li>Actualizaciones automáticas</li>
                    </ul>
                </div>
            </div>
            
            <div class="product-card">
                <div class="product-image">🔐</div>
                <div class="product-content">
                    <h3 class="product-title">Sistema de Autenticación Biométrica</h3>
                    <span class="product-category">Seguridad</span>
                    <p class="product-description">Sistema avanzado de autenticación biométrica para proteger tus dispositivos y cuentas personales.</p>
                    <ul class="product-features">
                        <li>Lector de huellas dactilares</li>
                        <li>Reconocimiento facial</li>
                        <li>Encriptación AES-256</li>
                        <li>Resistente al agua</li>
                    </ul>
                </div>
            </div>
            
            <div class="product-card">
                <div class="vip-tag">VIP</div>
                <div class="product-image">⚡</div>
                <div class="product-content">
                    <h3 class="product-title">Acceso VIP a Laboratorios</h3>
                    <span class="product-category">VIP Exclusivo</span>
                    <p class="product-description">Acceso ilimitado a laboratorios virtuales de ciberseguridad con escenarios de ataque realistas.</p>
                    <ul class="product-features">
                        <li>50+ escenarios de prueba</li>
                        <li>Entornos aislados</li>
                        <li>Simulaciones avanzadas</li>
                        <li>Soporte prioritario</li>
                    </ul>
                </div>
            </div>
            
            <div class="product-card">
                <div class="product-image">📱</div>
                <div class="product-content">
                    <h3 class="product-title">Aplicación de Monitoreo de Seguridad</h3>
                    <span class="product-category">Software</span>
                    <p class="product-description">Aplicación móvil para monitorear la seguridad de tus dispositivos y redes en tiempo real.</p>
                    <ul class="product-features">
                        <li>Alertas en tiempo real</li>
                        <li>Dashboard personalizado</li>
                        <li>Protección multiplataforma</li>
                        <li>Integración con APIs</li>
                    </ul>
                </div>
            </div>
            
            <div class="product-card">
                <div class="vip-tag">VIP</div>
                <div class="product-image">🎯</div>
                <div class="product-content">
                    <h3 class="product-title">Curso de Hacking Ético Avanzado</h3>
                    <span class="product-category">VIP Exclusivo</span>
                    <p class="product-description">Curso avanzado de hacking ético con mentoría personalizada y acceso a herramientas profesionales.</p>
                    <ul class="product-features">
                        <li>Mentoría individual</li>
                        <li>Herramientas profesionales</li>
                        <li>Proyectos empresariales</li>
                        <li>Certificación oficial</li>
                    </ul>
                </div>
            </div>
            
            <div class="product-card">
                <div class="product-image">🌐</div>
                <div class="product-content">
                    <h3 class="product-title">Firewall de Nueva Generación</h3>
                    <span class="product-category">Redes</span>
                    <p class="product-description">Firewall inteligente con IA para proteger tus redes contra amenazas avanzadas y ciberataques.</p>
                    <ul class="product-features">
                        <li>Protección contra malware</li>
                        <li>IA de detección</li>
                        <li>Control de acceso</li>
                        <li>Reportes detallados</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Features Section -->
    <section class="features" id="features">
        <h2 class="section-title">Características Destacadas</h2>
        
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">🔐</div>
                <h3 class="feature-title">Seguridad Avanzada</h3>
                <p class="feature-desc">Todas nuestras soluciones cuentan con encriptación de nivel militar y protección contra las últimas amenazas cibernéticas.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🚀</div>
                <h3 class="feature-title">Alto Rendimiento</h3>
                <p class="feature-desc">Nuestros productos están optimizados para ofrecer el mejor rendimiento posible en cualquier entorno tecnológico.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🧠</div>
                <h3 class="feature-title">Inteligencia Artificial</h3>
                <p class="feature-desc">Incorporamos IA en nuestros sistemas para detectar patrones de ataque y prevenir amenazas antes de que ocurran.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🌐</div>
                <h3 class="feature-title">Conexión Global</h3>
                <p class="feature-desc">Infraestructura distribuida en todo el mundo para garantizar baja latencia y alta disponibilidad.</p>
            </div>
        </div>
    </section>
    
    <!-- Registration Section -->
    <section class="registration" id="register">
        <div class="register-container">
            <h2 class="register-title">Regístrate Ahora</h2>
            
            <div class="google-signin">
                <div class="google-icon">G</div>
                <span>Continuar con Google</span>
            </div>
            
            <form id="registrationForm">
                <div class="form-group">
                    <label class="form-label">Nombre Completo</label>
                    <input type="text" class="form-input" placeholder="Ingresa tu nombre completo">
                </div>
                
                <div class="form-group">
                    <label class="form-label">Correo Electrónico</label>
                    <input type="email" class="form-input" placeholder="tu@email.com">
                </div>
                
                <div class="form-group">
                    <label class="form-label">Contraseña</label>
                    <input type="password" class="form-input" placeholder="Mínimo 8 caracteres">
                </div>
                
                <button type="submit" class="cta-button" style="width: 100%;">Crear Cuenta</button>
            </form>
            
            <div class="vip-options">
                <h3>Planes VIP Disponibles</h3>
                <div class="vip-plans">
                    <div class="vip-plan">
                        <h4 class="vip-name">Básico</h4>
                        <div class="vip-price">Gratis</div>
                        <ul class="vip-features">
                            <li>Acceso básico</li>
                            <li>Soporte estándar</li>
                            <li>Actualizaciones</li>
                        </ul>
                        <button class="cta-button" style="width: 100%; padding: 10px;">Seleccionar</button>
                    </div>
                    
                    <div class="vip-plan popular">
                        <h4 class="vip-name">Profesional</h4>
                        <div class="vip-price">$29.99/mes</div>
                        <ul class="vip-features">
                            <li>Acceso completo</li>
                            <li>Soporte prioritario</li>
                            <li>Recursos exclusivos</li>
                            <li>Webinars mensuales</li>
                            <li>Certificación</li>
                        </ul>
                        <button class="cta-button" style="width: 100%; padding: 10px;">Seleccionar</button>
                    </div>
                    
                    <div class="vip-plan">
                        <h4 class="vip-name">Empresarial</h4>
                        <div class="vip-price">$99.99/mes</div>
                        <ul class="vip-features">
                            <li>Acceso total</li>
                            <li>Soporte 24/7</li>
                            <li>Consultoría personal</li>
                            <li>Capacitación en equipo</li>
                            <li>APIs exclusivas</li>
                            <li>Personalización</li>
                        </ul>
                        <button class="cta-button" style="width: 100%; padding: 10px;">Seleccionar</button>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Footer -->
    <footer class="footer">
        <div class="footer-content">
            <div class="footer-column">
                <h3>AnthZz Berrocal</h3>
                <p>La tienda líder en tecnología, ciberseguridad y hacking ético. Fundada por AnthZz Berrocal, experto en seguridad informática y hacking ético.</p>
                <div class="social-links">
                    <a href="#" class="social-link">f</a>
                    <a href="#" class="social-link">t</a>
                    <a href="#" class="social-link">in</a>
                    <a href="#" class="social-link">g</a>
                </div>
            </div>
            
            <div class="footer-column">
                <h3>Productos</h3>
                <ul class="footer-links">
                    <li><a href="#">Ciberseguridad</a></li>
                    <li><a href="#">Hacking Ético</a></li>
                    <li><a href="#">Hardware</a></li>
                    <li><a href="#">Software</a></li>
                    <li><a href="#">Cursos</a></li>
                </ul>
            </div>
            
            <div class="footer-column">
                <h3>Recursos</h3>
                <ul class="footer-links">
                    <li><a href="#">Documentación</a></li>
                    <li><a href="#">Tutoriales</a></li>
                    <li><a href="#">Blog</a></li>
                    <li><a href="#">Soporte</a></li>
                    <li><a href="#">Comunidad</a></li>
                </ul>
            </div>
            
            <div class="footer-column">
                <h3>Contacto</h3>
                <ul class="footer-links">
                    <li>📧 antonioberrocal62@gmail.com</li>
                    <li>📍 Andahuaylas Perú</li>
                    <li>🕒 Lunes a Domingo</li>
                    <li>📞 +51 937 556 459</li>
                </ul>
            </div>
        </div>
        
        <div class="copyright">
            &copy; <span class="credits">AnthZz Berrocal</span> | Todos los derechos reservados | Tienda Virtual de Tecnología y Ciberseguridad
        </div>
    </footer>

    <script>
        // Cursor trail effect
        const cursorTrail = document.getElementById('cursorTrail');
        const trailDots = [];
        const trailLength = 10;
        
        // Create trail dots
        for (let i = 0; i < trailLength; i++) {
            const dot = document.createElement('div');
            dot.className = 'trail-dot';
            cursorTrail.appendChild(dot);
            trailDots.push({
                element: dot,
                x: 0,
                y: 0
            });
        }
        
        // Update trail on mouse move
        document.addEventListener('mousemove', (e) => {
            trailDots.forEach((dot, index) => {
                setTimeout(() => {
                    dot.x = e.clientX;
                    dot.y = e.clientY;
                    dot.element.style.left = `${dot.x}px`;
                    dot.element.style.top = `${dot.y}px`;
                    dot.element.style.opacity = (trailLength - index) / trailLength;
                }, index * 20);
            });
        });
        
        // Form submission
        document.getElementById('registrationForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('¡Registro exitoso! Bienvenido a AnthZz Berrocal Tech Store. Revisa tu correo para activar tu cuenta.');
        });
        
        // Google sign-in simulation
        document.querySelector('.google-signin').addEventListener('click', function() {
            alert('Simulación de inicio de sesión con Google. En una implementación real, redirigiría a la autenticación de Google.');
        });
        
        // VIP plan selection
        document.querySelectorAll('.vip-plan button').forEach(button => {
            button.addEventListener('click', function() {
                const planName = this.parentElement.querySelector('.vip-name').textContent;
                alert(`Has seleccionado el plan ${planName}. Serás redirigido al proceso de pago.`);
            });
        });
        
        // Navigation smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    window.scrollTo({
                        top: target.offsetTop - 100,
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // Animate elements on scroll
        const animateOnScroll = () => {
            const elements = document.querySelectorAll('.product-card, .feature-card, .info-item');
            elements.forEach(element => {
                const position = element.getBoundingClientRect();
                if (position.top < window.innerHeight - 100) {
                    element.style.opacity = '1';
                    element.style.transform = 'translateY(0)';
                }
            });
        };
        
        // Set initial state for animation
        document.querySelectorAll('.product-card, .feature-card, .info-item').forEach(element => {
            element.style.opacity = '0';
            element.style.transform = 'translateY(30px)';
            element.style.transition = 'all 0.6s ease';
        });
        
        // Listen for scroll
        window.addEventListener('scroll', animateOnScroll);
        window.addEventListener('load', animateOnScroll);
        
        // Background animation
        const bgElements = document.querySelectorAll('.bg-element');
        bgElements.forEach((el, index) => {
            setInterval(() => {
                const randomX = Math.random() * 20 - 10;
                const randomY = Math.random() * 20 - 10;
                el.style.transform = `translate(${randomX}px, ${randomY}px) rotate(${Math.random() * 10 - 5}deg)`;
            }, 3000 + index * 1000);
        });
    </script>
</body>
</html>
```
