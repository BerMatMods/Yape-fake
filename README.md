
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>BerMatMods TECH STORE</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700;900&family=Roboto:wght@300;400;500;700&display=swap');
        
        :root {
            --primary: #00ff88;
            --secondary: #0066ff;
            --dark: #0a0a1a;
            --darker: #05050f;
            --light: #f0f0f0;
            --purple: #8a2be2;
            --pink: #ff00ff;
            --blue: #00ffff;
            --yellow: #ffff00;
            --orange: #ff6b00;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Roboto', sans-serif;
            touch-action: manipulation;
        }
        
        body {
            background: linear-gradient(135deg, var(--darker), var(--dark)) fixed;
            color: var(--light);
            min-height: 100vh;
            overflow-x: hidden;
            background-attachment: fixed;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
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
        
        @keyframes scanline {
            0% { background-position: 0 0; }
            100% { background-position: 100% 100%; }
        }
        
        @keyframes matrix {
            0% { opacity: 0; transform: translateY(-20px); }
            100% { opacity: 1; transform: translateY(0); }
        }
        
        /* Header */
        .header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            background: rgba(10, 10, 26, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(0, 255, 136, 0.3);
            animation: glow 2s infinite alternate;
            transition: all 0.3s;
        }
        
        .header.scrolled {
            padding: 10px 20px;
            background: rgba(10, 10, 26, 0.98);
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
            font-family: 'Orbitron', sans-serif;
            font-weight: 900;
            font-size: 24px;
            color: var(--primary);
            animation: neon-pulse 2s infinite alternate;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s;
        }
        
        .logo:hover {
            transform: scale(1.05);
        }
        
        .logo-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            animation: rotate 8s linear infinite;
            position: relative;
            overflow: hidden;
        }
        
        .logo-icon::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(transparent, rgba(255, 255, 255, 0.2));
        }
        
        .logo-icon::after {
            content: "A";
            color: white;
            font-weight: bold;
            font-size: 18px;
            position: relative;
            z-index: 2;
        }
        
        .nav {
            display: flex;
            gap: 25px;
        }
        
        .nav-item {
            color: var(--light);
            text-decoration: none;
            font-size: 16px;
            position: relative;
            padding: 5px 0;
            transition: all 0.3s;
            font-weight: 500;
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
        
        .menu-toggle {
            display: none;
            background: none;
            border: none;
            color: var(--primary);
            font-size: 24px;
            cursor: pointer;
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
            text-align: center;
        }
        
        .hero-content {
            max-width: 800px;
            z-index: 10;
            animation: matrix 1s ease;
        }
        
        .hero-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 3.5rem;
            font-weight: 900;
            margin-bottom: 15px;
            line-height: 1.2;
            color: white;
            text-shadow: 0 0 20px rgba(0, 255, 136, 0.5);
            animation: neon-pulse 2s infinite alternate;
        }
        
        .hero-subtitle {
            font-size: 1.2rem;
            margin-bottom: 30px;
            color: var(--light);
            opacity: 0.9;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .hero-info {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }
        
        .info-item {
            background: rgba(10, 10, 26, 0.7);
            padding: 12px 20px;
            border-radius: 10px;
            border: 1px solid rgba(0, 255, 136, 0.3);
            backdrop-filter: blur(10px);
            animation: glow 3s infinite alternate;
            min-width: 120px;
        }
        
        .info-label {
            font-size: 12px;
            color: var(--primary);
            margin-bottom: 3px;
        }
        
        .info-value {
            font-size: 16px;
            font-weight: bold;
        }
        
        .cta-button {
            display: inline-block;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: white;
            padding: 12px 30px;
            border-radius: 50px;
            font-size: 16px;
            font-weight: bold;
            text-decoration: none;
            margin: 8px;
            transition: all 0.3s;
            border: none;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            animation: glow 2s infinite alternate;
            min-width: 160px;
            text-align: center;
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
        
        /* Courses Section */
        .courses {
            padding: 80px 20px;
            max-width: 1400px;
            margin: 0 auto;
        }
        
        .section-title {
            text-align: center;
            font-family: 'Orbitron', sans-serif;
            font-size: 2.5rem;
            margin-bottom: 40px;
            color: var(--primary);
            animation: neon-pulse 2s infinite alternate;
            position: relative;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 3px;
            background: var(--primary);
            box-shadow: 0 0 10px var(--primary);
        }
        
        .courses-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }
        
        .course-card {
            background: rgba(10, 10, 26, 0.7);
            border-radius: 15px;
            overflow: hidden;
            transition: all 0.5s;
            border: 1px solid rgba(0, 255, 136, 0.3);
            backdrop-filter: blur(10px);
            position: relative;
            cursor: pointer;
            animation: matrix 0.5s ease;
        }
        
        .course-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0, 255, 136, 0.2);
        }
        
        .course-card::before {
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
        
        .course-card:hover::before {
            opacity: 1;
        }
        
        .course-image {
            height: 160px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 50px;
            position: relative;
            overflow: hidden;
        }
        
        .course-icon-bg {
            position: absolute;
            width: 200%;
            height: 200%;
            top: -50%;
            left: -50%;
            background: conic-gradient(from 0deg, var(--secondary), var(--purple), var(--pink), var(--blue), var(--secondary));
            animation: rotate 10s linear infinite;
            opacity: 0.2;
        }
        
        .course-icon {
            position: relative;
            z-index: 2;
        }
        
        .course-content {
            padding: 20px;
        }
        
        .course-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.3rem;
            margin-bottom: 8px;
            color: var(--primary);
            line-height: 1.3;
        }
        
        .course-category {
            color: var(--blue);
            font-size: 12px;
            margin-bottom: 12px;
            display: inline-block;
            padding: 4px 8px;
            background: rgba(0, 255, 255, 0.1);
            border-radius: 4px;
        }
        
        .course-level {
            color: var(--yellow);
            font-size: 12px;
            margin-bottom: 12px;
            display: inline-block;
            padding: 4px 8px;
            background: rgba(255, 255, 0, 0.1);
            border-radius: 4px;
        }
        
        .course-description {
            color: var(--light);
            opacity: 0.8;
            margin-bottom: 15px;
            font-size: 14px;
            line-height: 1.5;
            display: -webkit-box;
            -webkit-line-clamp: 3;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }
        
        .course-features {
            list-style: none;
            margin-bottom: 15px;
            font-size: 13px;
        }
        
        .course-features li {
            color: var(--light);
            margin-bottom: 6px;
            position: relative;
            padding-left: 18px;
            opacity: 0.9;
        }
        
        .course-features li::before {
            content: '✓';
            color: var(--primary);
            position: absolute;
            left: 0;
            font-weight: bold;
        }
        
        .course-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 20px 20px;
        }
        
        .course-duration {
            color: var(--purple);
            font-size: 14px;
            font-weight: 500;
        }
        
        .course-action {
            color: var(--primary);
            font-size: 14px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .course-action:hover {
            color: var(--yellow);
            text-decoration: underline;
        }
        
        /* Features Section */
        .features {
            padding: 60px 20px;
            background: rgba(5, 5, 15, 0.5);
            margin: 40px 0;
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 25px;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .feature-card {
            text-align: center;
            padding: 25px 20px;
            background: rgba(10, 10, 26, 0.7);
            border-radius: 15px;
            border: 1px solid rgba(0, 255, 136, 0.3);
            transition: all 0.3s;
            animation: matrix 0.5s ease;
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 255, 136, 0.2);
        }
        
        .feature-icon {
            font-size: 40px;
            margin-bottom: 15px;
            color: var(--primary);
            animation: float 3s ease-in-out infinite;
        }
        
        .feature-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.3rem;
            margin-bottom: 12px;
            color: var(--primary);
        }
        
        .feature-desc {
            color: var(--light);
            opacity: 0.8;
            line-height: 1.5;
            font-size: 14px;
        }
        
        /* Registration Section */
        .registration {
            padding: 80px 20px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .register-container {
            max-width: 500px;
            margin: 0 auto;
            background: rgba(10, 10, 26, 0.8);
            border-radius: 20px;
            padding: 30px 20px;
            border: 1px solid rgba(0, 255, 136, 0.3);
            backdrop-filter: blur(10px);
            position: relative;
            z-index: 10;
            animation: matrix 0.5s ease;
        }
        
        .register-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 2rem;
            margin-bottom: 25px;
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
            padding: 12px;
            margin-bottom: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .google-signin:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-3px);
        }
        
        .google-icon {
            width: 25px;
            height: 25px;
            background: white;
            border-radius: 50%;
            margin-right: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: #ea4335;
            font-size: 14px;
        }
        
        .form-group {
            margin-bottom: 18px;
            text-align: left;
        }
        
        .form-label {
            display: block;
            margin-bottom: 6px;
            color: var(--light);
            font-size: 13px;
            font-weight: 500;
        }
        
        .form-input {
            width: 100%;
            padding: 12px 15px;
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(0, 255, 136, 0.3);
            border-radius: 10px;
            color: white;
            font-size: 15px;
            transition: all 0.3s;
        }
        
        .form-input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 10px rgba(0, 255, 136, 0.5);
        }
        
        .vip-options {
            margin: 25px 0;
            text-align: center;
        }
        
        .vip-options h3 {
            color: var(--pink);
            margin-bottom: 18px;
            font-family: 'Orbitron', sans-serif;
            font-size: 1.4rem;
        }
        
        .vip-plans {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .vip-plan {
            background: rgba(10, 10, 26, 0.7);
            border: 1px solid rgba(138, 43, 226, 0.5);
            border-radius: 15px;
            padding: 18px 15px;
            width: 150px;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
            animation: matrix 0.5s ease;
        }
        
        .vip-plan:hover {
            transform: translateY(-8px);
            border-color: var(--pink);
        }
        
        .vip-plan.popular {
            border: 2px solid var(--pink);
            transform: scale(1.08);
            z-index: 1;
        }
        
        .vip-plan.popular::before {
            content: 'POPULAR';
            position: absolute;
            top: 8px;
            right: -25px;
            background: var(--pink);
            color: white;
            padding: 3px 25px;
            transform: rotate(45deg);
            font-size: 10px;
            font-weight: bold;
            font-family: 'Orbitron', sans-serif;
        }
        
        .vip-name {
            font-family: 'Orbitron', sans-serif;
            color: var(--pink);
            font-size: 1.1rem;
            margin-bottom: 12px;
        }
        
        .vip-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        .vip-features {
            list-style: none;
            margin-bottom: 15px;
            font-size: 12px;
        }
        
        .vip-features li {
            color: var(--light);
            margin-bottom: 8px;
        }
        
        .vip-features li::before {
            content: '✓';
            color: var(--primary);
            margin-right: 6px;
        }
        
        /* Footer */
        .footer {
            background: rgba(5, 5, 15, 0.8);
            padding: 50px 20px 25px;
            border-top: 1px solid rgba(0, 255, 136, 0.3);
            position: relative;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 30px;
        }
        
        .footer-column h3 {
            font-family: 'Orbitron', sans-serif;
            color: var(--primary);
            margin-bottom: 18px;
            font-size: 1.3rem;
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
            font-size: 14px;
        }
        
        .footer-links a:hover {
            color: var(--primary);
            opacity: 1;
        }
        
        .social-links {
            display: flex;
            gap: 12px;
            margin-top: 15px;
        }
        
        .social-link {
            width: 35px;
            height: 35px;
            background: rgba(0, 255, 136, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary);
            text-decoration: none;
            transition: all 0.3s;
            border: 1px solid rgba(0, 255, 136, 0.3);
            font-size: 18px;
        }
        
        .social-link:hover {
            background: var(--primary);
            color: var(--dark);
            transform: translateY(-5px);
        }
        
        .contact-info {
            margin-top: 15px;
            font-size: 14px;
            line-height: 1.6;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            margin-bottom: 8px;
            opacity: 0.9;
        }
        
        .contact-icon {
            width: 18px;
            height: 18px;
            background: var(--primary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 10px;
            font-size: 10px;
            flex-shrink: 0;
        }
        
        .copyright {
            text-align: center;
            margin-top: 50px;
            padding-top: 25px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: var(--light);
            opacity: 0.7;
            font-size: 13px;
        }
        
        .credits {
            color: var(--primary);
            font-weight: bold;
        }
        
        /* Background Elements */
        .bg-element {
            position: absolute;
            opacity: 0.08;
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
            width: 4px;
            height: 4px;
            background: var(--primary);
            border-radius: 50%;
            pointer-events: none;
            opacity: 0;
        }
        
        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(5, 5, 15, 0.9);
            backdrop-filter: blur(5px);
            z-index: 2000;
            justify-content: center;
            align-items: center;
            animation: matrix 0.3s ease;
        }
        
        .modal-content {
            background: rgba(10, 10, 26, 0.9);
            border-radius: 15px;
            padding: 30px;
            border: 1px solid rgba(0, 255, 136, 0.3);
            max-width: 500px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
        }
        
        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            background: none;
            border: none;
            color: var(--light);
            font-size: 24px;
            cursor: pointer;
            opacity: 0.7;
            transition: all 0.3s;
        }
        
        .close-modal:hover {
            color: var(--primary);
            opacity: 1;
            transform: rotate(90deg);
        }
        
        .modal-title {
            font-family: 'Orbitron', sans-serif;
            color: var(--primary);
            margin-bottom: 20px;
            font-size: 1.8rem;
        }
        
        .modal-content-text {
            color: var(--light);
            line-height: 1.6;
            margin-bottom: 20px;
            font-size: 14px;
        }
        
        .modal-features {
            list-style: none;
            margin-bottom: 20px;
        }
        
        .modal-features li {
            color: var(--light);
            margin-bottom: 12px;
            display: flex;
            align-items: flex-start;
            gap: 10px;
        }
        
        .modal-features .icon {
            color: var(--primary);
            font-weight: bold;
            min-width: 20px;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .header {
                padding: 12px 15px;
            }
            
            .header.scrolled {
                padding: 10px 15px;
            }
            
            .logo {
                font-size: 20px;
            }
            
            .logo-icon {
                width: 35px;
                height: 35px;
            }
            
            .logo-icon::after {
                font-size: 16px;
            }
            
            .nav {
                display: none;
                position: absolute;
                top: 100%;
                left: 0;
                width: 100%;
                background: rgba(10, 10, 26, 0.95);
                flex-direction: column;
                padding: 15px 0;
                border-bottom: 1px solid rgba(0, 255, 136, 0.3);
                animation: matrix 0.3s ease;
            }
            
            .nav.active {
                display: flex;
            }
            
            .nav-item {
                padding: 12px 20px;
                font-size: 16px;
            }
            
            .menu-toggle {
                display: block;
            }
            
            .hero-title {
                font-size: 2.5rem;
            }
            
            .hero-info {
                gap: 12px;
                flex-direction: column;
                align-items: center;
            }
            
            .info-item {
                min-width: auto;
                width: 100%;
                max-width: 250px;
            }
            
            .section-title {
                font-size: 2rem;
            }
            
            .section-title::after {
                width: 60px;
            }
            
            .courses-grid {
                gap: 20px;
            }
            
            .course-card {
                margin-bottom: 15px;
            }
            
            .cta-button {
                margin: 6px 0;
                font-size: 15px;
                padding: 10px 25px;
            }
            
            .features-grid {
                gap: 20px;
            }
            
            .feature-card {
                padding: 20px 15px;
            }
            
            .feature-icon {
                font-size: 35px;
            }
            
            .feature-title {
                font-size: 1.2rem;
            }
            
            .register-container {
                padding: 25px 15px;
            }
            
            .register-title {
                font-size: 1.8rem;
            }
            
            .vip-plans {
                gap: 10px;
            }
            
            .vip-plan {
                width: 130px;
                padding: 15px 12px;
            }
            
            .vip-plan.popular {
                transform: scale(1.1);
            }
            
            .footer-content {
                gap: 25px;
            }
            
            .footer-column h3 {
                font-size: 1.2rem;
            }
            
            .social-links {
                gap: 10px;
            }
            
            .social-link {
                width: 30px;
                height: 30px;
                font-size: 16px;
            }
            
            .contact-info {
                font-size: 13px;
            }
        }
        
        @media (max-width: 480px) {
            .hero-title {
                font-size: 2rem;
            }
            
            .hero-subtitle {
                font-size: 1rem;
            }
            
            .section-title {
                font-size: 1.8rem;
            }
            
            .courses-grid {
                grid-template-columns: 1fr;
            }
            
            .info-item {
                max-width: 300px;
            }
            
            .vip-plans {
                flex-direction: column;
                align-items: center;
            }
            
            .vip-plan {
                width: 100%;
                max-width: 300px;
            }
            
            .vip-plan.popular {
                transform: scale(1);
            }
            
            .cta-button {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <!-- Cursor Trail -->
    <div class="cursor-trail" id="cursorTrail"></div>
    
    <!-- Background Elements -->
    <div class="bg-element circle" style="width: 150px; height: 150px; top: 10%; left: 10%; opacity: 0.05;"></div>
    <div class="bg-element circle" style="width: 120px; height: 120px; top: 70%; left: 20%; opacity: 0.05;"></div>
    <div class="bg-element circle" style="width: 80px; height: 80px; top: 30%; right: 15%; opacity: 0.05;"></div>
    <div class="bg-element circle" style="width: 60px; height: 60px; bottom: 20%; left: 30%; opacity: 0.05;"></div>
    <div class="bg-element line" style="width: 150px; height: 2px; top: 50%; right: 10%; opacity: 0.05;"></div>
    <div class="bg-element line" style="width: 120px; height: 2px; bottom: 40%; left: 15%; transform: rotate(60deg); opacity: 0.05;"></div>
    
    <!-- Header -->
    <header class="header">
        <div class="logo">
            <div class="logo-icon"></div>
            <span>AnthZz Berrocal</span>
        </div>
        <button class="menu-toggle">☰</button>
        <nav class="nav">
            <a href="#courses" class="nav-item">Cursos</a>
            <a href="#features" class="nav-item">Beneficios</a>
            <a href="#vip" class="nav-item">VIP</a>
            <a href="#register" class="nav-item">Registro</a>
        </nav>
    </header>
    
    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content">
            <h1 class="hero-title">ACADEMIA DE CIBERSEGURIDAD</h1>
            <p class="hero-subtitle">Domina el mundo del hacking ético, recuperación de cuentas y seguridad digital con los cursos más avanzados del mercado. Aprende técnicas profesionales de manera ética y legal.</p>
            
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
                    <div class="info-label">TELÉFONO</div>
                    <div class="info-value">937 55 64 59</div>
                </div>
            </div>
            
            <div>
                <a href="#courses" class="cta-button">Ver Cursos</a>
                <a href="#register" class="cta-button">Unirse Ahora</a>
            </div>
        </div>
    </section>
    
    <!-- Courses Section -->
    <section class="courses" id="courses">
        <h2 class="section-title">Cursos de Hacking Ético</h2>
        
        <div class="courses-grid">
            <div class="course-card" onclick="openModal('whatsapp')">
                <div class="course-image">
                    <div class="course-icon-bg"></div>
                    <div class="course-icon">📱</div>
                </div>
                <div class="course-content">
                    <h3 class="course-title">Clonación Segura de WhatsApp</h3>
                    <span class="course-category">Seguridad Móvil</span>
                    <span class="course-level">Avanzado</span>
                    <p class="course-description">Aprende técnicas avanzadas para la recuperación de cuentas de WhatsApp y comprensión de sus mecanismos de seguridad.</p>
                    <ul class="course-features">
                        <li>Recuperación de cuentas perdidas</li>
                        <li>Protección contra clonación</li>
                        <li>Verificación de autenticidad</li>
                        <li>Seguridad en dispositivos móviles</li>
                    </ul>
                </div>
                <div class="course-footer">
                    <span class="course-duration">40 horas</span>
                    <span class="course-action">Más detalles →</span>
                </div>
            </div>
            
            <div class="course-card" onclick="openModal('gmail')">
                <div class="course-image">
                    <div class="course-icon-bg"></div>
                    <div class="course-icon">📧</div>
                </div>
                <div class="course-content">
                    <h3 class="course-title">Recuperación de Cuentas Gmail</h3>
                    <span class="course-category">Seguridad de Correo</span>
                    <span class="course-level">Experto</span>
                    <p class="course-description">Técnicas profesionales para recuperar el acceso a cuentas de Gmail perdidas o comprometidas de manera ética.</p>
                    <ul class="course-features">
                        <li>Recuperación de contraseñas</li>
                        <li>Verificación de identidad</li>
                        <li>Protección contra phishing</li>
                        <li>Autenticación en dos pasos</li>
                    </ul>
                </div>
                <div class="course-footer">
                    <span class="course-duration">35 horas</span>
                    <span class="course-action">Más detalles →</span>
                </div>
            </div>
            
            <div class="course-card" onclick="openModal('wifi')">
                <div class="course-image">
                    <div class="course-icon-bg"></div>
                    <div class="course-icon">📶</div>
                </div>
                <div class="course-content">
                    <h3 class="course-title">Acceso a Redes Wi-Fi</h3>
                    <span class="course-category">Redes Inalámbricas</span>
                    <span class="course-level">Profesional</span>
                    <p class="course-description">Aprende a auditar redes Wi-Fi, identificar vulnerabilidades y proteger conexiones inalámbricas.</p>
                    <ul class="course-features">
                        <li>Auditoría de redes</li>
                        <li>Protección WPA/WPA2</li>
                        <li>Prevención de ataques</li>
                        <li>Configuración segura</li>
                    </ul>
                </div>
                <div class="course-footer">
                    <span class="course-duration">45 horas</span>
                    <span class="course-action">Más detalles →</span>
                </div>
            </div>
            
            <div class="course-card" onclick="openModal('ethical')">
                <div class="course-image">
                    <div class="course-icon-bg"></div>
                    <div class="course-icon">🛡️</div>
                </div>
                <div class="course-content">
                    <h3 class="course-title">Hacking Ético Profesional</h3>
                    <span class="course-category">Ciberseguridad</span>
                    <span class="course-level">Todos los niveles</span>
                    <p class="course-description">Curso completo de hacking ético, desde principiante hasta experto, con certificación oficial.</p>
                    <ul class="course-features">
                        <li>Pentesting avanzado</li>
                        <li>Metodologías profesionales</li>
                        <li>Certificación CEH</li>
                        <li>Proyectos reales</li>
                    </ul>
                </div>
                <div class="course-footer">
                    <span class="course-duration">120 horas</span>
                    <span class="course-action">Más detalles →</span>
                </div>
            </div>
            
            <div class="course-card" onclick="openModal('social')">
                <div class="course-image">
                    <div class="course-icon-bg"></div>
                    <div class="course-icon">🌐</div>
                </div>
                <div class="course-content">
                    <h3 class="course-title">Ingeniería Social Avanzada</h3>
                    <span class="course-category">Psicología Digital</span>
                    <span class="course-level">Experto</span>
                    <p class="course-description">Técnicas de manipulación psicológica digital y cómo protegerse contra ataques de ingeniería social.</p>
                    <ul class="course-features">
                        <li>Phishing avanzado</li>
                        <li>Manipulación psicológica</li>
                        <li>Protección contra fraudes</li>
                        <li>Detección de estafas</li>
                    </ul>
                </div>
                <div class="course-footer">
                    <span class="course-duration">30 horas</span>
                    <span class="course-action">Más detalles →</span>
                </div>
            </div>
            
            <div class="course-card" onclick="openModal('forensic')">
                <div class="course-image">
                    <div class="course-icon-bg"></div>
                    <div class="course-icon">🔍</div>
                </div>
                <div class="course-content">
                    <h3 class="course-title">Informática Forense</h3>
                    <span class="course-category">Investigación Digital</span>
                    <span class="course-level">Profesional</span>
                    <p class="course-description">Técnicas para recuperar datos eliminados y realizar investigaciones digitales forenses.</p>
                    <ul class="course-features">
                        <li>Recuperación de datos</li>
                        <li>Análisis de dispositivos</li>
                        <li>Evidencia digital</li>
                        <li>Reportes forenses</li>
                    </ul>
                </div>
                <div class="course-footer">
                    <span class="course-duration">10 horas</span>
                    <span class="course-action">Más detalles →</span>
                </div>
            </div>
            
            <div class="course-card" onclick="openModal('mobile')">
                <div class="course-image">
                    <div class="course-icon-bg"></div>
                    <div class="course-icon">📱</div>
                </div>
                <div class="course-content">
                    <h3 class="course-title">Seguridad en Dispositivos Móviles</h3>
                    <span class="course-category">Dispositivos Android/iOS</span>
                    <span class="course-level">Avanzado</span>
                    <p class="course-description">Protección completa para smartphones y tablets contra malware, spyware y ataques móviles.</p>
                    <ul class="course-features">
                        <li>Protección Android/iOS</li>
                        <li>Detección de spyware</li>
                        <li>Encriptación móvil</li>
                        <li>Seguridad en apps</li>
                    </ul>
                </div>
                <div class="course-footer">
                    <span class="course-duration">35 horas</span>
                    <span class="course-action">Más detalles →</span>
                </div>
            </div>
            
            <div class="course-card" onclick="openModal('network')">
                <div class="course-image">
                    <div class="course-icon-bg"></div>
                    <div class="course-icon">💻</div>
                </div>
                <div class="course-content">
                    <h3 class="course-title">Pentesting de Redes</h3>
                    <span class="course-category">Seguridad de Redes</span>
                    <span class="course-level">Experto</span>
                    <p class="course-description">Auditorías completas de redes corporativas y protección contra ataques avanzados.</p>
                    <ul class="course-features">
                        <li>Escaneo de puertos</li>
                        <li>Explotación de vulnerabilidades</li>
                        <li>Protección perimetral</li>
                        <li>Firewalls avanzados</li>
                    </ul>
                </div>
                <div class="course-footer">
                    <span class="course-duration">30 horas</span>
                    <span class="course-action">Más detalles →</span>
                </div>
            </div>
        </div>
    </section>
    
    <!-- Features Section -->
    <section class="features" id="features">
        <h2 class="section-title">Beneficios Exclusivos</h2>
        
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">🎓</div>
                <h3 class="feature-title">Certificación Oficial</h3>
                <p class="feature-desc">Obtén certificaciones reconocidas internacionalmente que acreditan tus habilidades en ciberseguridad.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">👥</div>
                <h3 class="feature-title">Comunidad VIP</h3>
                <p class="feature-desc">Accede a una comunidad exclusiva de hackers éticos para compartir conocimientos y oportunidades.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">💼</div>
                <h3 class="feature-title">Oportunidades Laborales</h3>
                <p class="feature-desc">Conexión directa con empresas que buscan profesionales en ciberseguridad para contratación.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🛡️</div>
                <h3 class="feature-title">Ética y Legalidad</h3>
                <p class="feature-desc">Todos nuestros cursos promueven el uso ético de las habilidades y el cumplimiento de la ley.</p>
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
                    <label class="form-label">Teléfono</label>
                    <input type="tel" class="form-input" placeholder="937 55 64 59">
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
                        <div class="vip-price">S/ 299/mes</div>
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
                        <div class="vip-price">S/ 899/mes</div>
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
                <h3>BerMatMods_Tech store</h3>
                <p>La tienda online líder en ciberseguridad y hacking ético en Perú. Creada  por AnthZz Berrocal, experto en seguridad informática.</p>
                <div class="social-links">
                    <a href="#" class="social-link">f</a>
                    <a href="#" class="social-link">t</a>
                    <a href="#" class="social-link">in</a>
                    <a href="#" class="social-link">g</a>
                </div>
            </div>
            
            <div class="footer-column">
                <h3>Cursos</h3>
                <ul class="footer-links">
                    <li><a href="#">Hacking Ético</a></li>
                    <li><a href="#">Seguridad Móvil</a></li>
                    <li><a href="#">Redes Wi-Fi</a></li>
                    <li><a href="#">Informática Forense</a></li>
                    <li><a href="#">Ingeniería Social</a></li>
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
                <div class="contact-info">
                    <div class="contact-item">
                        <div class="contact-icon">📧</div>
                        <span>antonioberrocal62@gmail.com</span>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">📞</div>
                        <span>937 556 459.    936 651 249</span>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">📍</div>
                        <span>Andahuaylas, Perú</span>
                    </div>
                    <div class="contact-item">
                        <div class="contact-icon">🕒</div>
                        <span>Lunes a Viernes 9:00 - 18:00</span>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="copyright">
            &copy; <span class="credits">AnthZz Berrocal</span> | Todos los derechos reservados | TECH STORE de Ciberseguridad y Hacking Ético
        </div>
    </footer>

    <!-- Course Modals -->
    <div class="modal" id="whatsappModal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('whatsapp')">×</button>
            <h3 class="modal-title">Clonación Segura de WhatsApp</h3>
            <p class="modal-content-text">Curso avanzado que enseña técnicas profesionales para la recuperación de cuentas de WhatsApp perdidas o comprometidas, con un enfoque ético y legal en la seguridad digital.</p>
            
            <ul class="modal-features">
                <li><span class="icon">✓</span> <strong>Módulo 1:</strong> Fundamentos de seguridad en WhatsApp</li>
                <li><span class="icon">✓</span> <strong>Módulo 2:</strong> Recuperación de cuentas perdidas</li>
                <li><span class="icon">✓</span> <strong>Módulo 3:</strong> Verificación de autenticidad de cuentas</li>
                <li><span class="icon">✓</span> <strong>Módulo 4:</strong> Protección contra clonación</li>
                <li><span class="icon">✓</span> <strong>Módulo 5:</strong> Seguridad en dispositivos móviles</li>
                <li><span class="icon">✓</span> <strong>Módulo 6:</strong> Prevención de ataques</li>
                <li><span class="icon">✓</span> <strong>Módulo 7:</strong> Casos prácticos reales</li>
                <li><span class="icon">✓</span> <strong>Módulo 8:</strong> Ética y legalidad en el hacking</li>
            </ul>
            
            <p class="modal-content-text">Duración: 40 horas | Nivel: Avanzado | Certificación incluida</p>
            <button class="cta-button" style="width: 100%;">Inscribirse en el Curso</button>
        </div>
    </div>

    <div class="modal" id="gmailModal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('gmail')">×</button>
            <h3 class="modal-title">Recuperación de Cuentas Gmail</h3>
            <p class="modal-content-text">Aprende técnicas profesionales para recuperar el acceso a cuentas de Gmail perdidas o comprometidas de manera ética, con un enfoque en la seguridad y la protección de datos personales.</p>
            
            <ul class="modal-features">
                <li><span class="icon">✓</span> <strong>Módulo 1:</strong> Arquitectura de seguridad de Gmail</li>
                <li><span class="icon">✓</span> <strong>Módulo 2:</strong> Recuperación de contraseñas</li>
                <li><span class="icon">✓</span> <strong>Módulo 3:</strong> Verificación de identidad</li>
                <li><span class="icon">✓</span> <strong>Módulo 4:</strong> Protección contra phishing</li>
                <li><span class="icon">✓</span> <strong>Módulo 5:</strong> Autenticación en dos pasos</li>
                <li><span class="icon">✓</span> <strong>Módulo 6:</strong> Seguridad en dispositivos</li>
                <li><span class="icon">✓</span> <strong>Módulo 7:</strong> Casos de estudio avanzados</li>
                <li><span class="icon">✓</span> <strong>Módulo 8:</strong> Prevención de fraudes digitales</li>
            </ul>
            
            <p class="modal-content-text">Duración: 35 horas | Nivel: Experto | Certificación incluida</p>
            <button class="cta-button" style="width: 100%;">Inscribirse en el Curso</button>
        </div>
    </div>

    <div class="modal" id="wifiModal">
        <div class="modal-content">
            <button class="close-modal" onclick="closeModal('wifi')">×</button>
            <h3 class="modal-title">Acceso a Redes Wi-Fi</h3>
            <p class="modal-content-text">Curso completo sobre auditoría de redes Wi-Fi, identificación de vulnerabilidades y protección contra ataques inalámbricos, con un enfoque ético y profesional.</p>
            
            <ul class="modal-features">
                <li><span class="icon">✓</span> <strong>Módulo 1:</strong> Fundamentos de redes inalámbricas</li>
                <li><span class="icon">✓</span> <strong>Módulo 2:</strong> Auditoría de redes Wi-Fi</li>
                <li><span class="icon">✓</span> <strong>Módulo 3:</strong> Protección WPA/WPA2/WPA3</li>
                <li><span class="icon">✓</span> <strong>Módulo 4:</strong> Prevención de ataques</li>
                <li><span class="icon">✓</span> <strong>Módulo 5:</strong> Configuración segura</li>
                <li><span class="icon">✓</span> <strong>Módulo 6:</strong> Detección de intrusos</li>
                <li><span class="icon">✓</span> <strong>Módulo 7:</strong> Hardening de redes</li>
                <li><span class="icon">✓</span> <strong>Módulo 8:</strong> Casos prácticos empresariales</li>
            </ul>
            
            <p class="modal-content-text">Duración: 45 horas | Nivel: Profesional | Certificación incluida</p>
            <button class="cta-button" style="width: 100%;">Inscribirse en el Curso</button>
        </div>
    </div>

    <script>
        // Cursor trail effect
        const cursorTrail = document.getElementById('cursorTrail');
        const trailDots = [];
        const trailLength = 8;
        
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
                    dot.element.style.opacity = (trailLength - index) / trailLength * 0.7;
                }, index * 25);
            });
        });
        
        // Touch support for mobile
        document.addEventListener('touchmove', (e) => {
            if (e.touches.length > 0) {
                const touch = e.touches[0];
                trailDots.forEach((dot, index) => {
                    setTimeout(() => {
                        dot.x = touch.clientX;
                        dot.y = touch.clientY;
                        dot.element.style.left = `${dot.x}px`;
                        dot.element.style.top = `${dot.y}px`;
                        dot.element.style.opacity = (trailLength - index) / trailLength * 0.7;
                    }, index * 25);
                });
            }
        });
        
        // Form submission
        document.getElementById('registrationForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('¡Registro exitoso! Bienvenido a AnthZz Berrocal Academia. Revisa tu correo para activar tu cuenta y recibir más información sobre nuestros cursos.');
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
        
        // Navigation smooth scroll and menu toggle
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    window.scrollTo({
                        top: target.offsetTop - 80,
                        behavior: 'smooth'
                    });
                    
                    // Close mobile menu
                    document.querySelector('.nav').classList.remove('active');
                }
            });
        });
        
        // Mobile menu toggle
        document.querySelector('.menu-toggle').addEventListener('click', function() {
            document.querySelector('.nav').classList.toggle('active');
        });
        
        // Header scroll effect
        window.addEventListener('scroll', function() {
            const header = document.querySelector('.header');
            if (window.scrollY > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        });
        
        // Modal functions
        function openModal(course) {
            document.getElementById(course + 'Modal').style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }
        
        function closeModal(course) {
            document.getElementById(course + 'Modal').style.display = 'none';
            document.body.style.overflow = 'auto';
        }
        
        // Close modal when clicking outside
        document.querySelectorAll('.modal').forEach(modal => {
            modal.addEventListener('click', function(e) {
                if (e.target === this) {
                    this.style.display = 'none';
                    document.body.style.overflow = 'auto';
                }
            });
        });
        
        // Close modal with escape key
        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                document.querySelectorAll('.modal').forEach(modal => {
                    modal.style.display = 'none';
                });
                document.body.style.overflow = 'auto';
            }
        });
        
        // Animate elements on scroll
        const animateOnScroll = () => {
            const elements = document.querySelectorAll('.course-card, .feature-card, .info-item');
            elements.forEach(element => {
                const position = element.getBoundingClientRect();
                if (position.top < window.innerHeight - 100) {
                    element.style.opacity = '1';
                    element.style.transform = 'translateY(0)';
                }
            });
        };
        
        // Set initial state for animation
        document.querySelectorAll('.course-card, .feature-card, .info-item').forEach(element => {
            element.style.opacity = '0';
            element.style.transform = 'translateY(30px)';
            element.style.transition = 'all 0.6s ease';
        });
        
        // Listen for scroll
        window.addEventListener('scroll', animateOnScroll);
        window.addEventListener('load', animateOnScroll);
        
        // Add click feedback to course cards
        document.querySelectorAll('.course-card').forEach(card => {
            card.addEventListener('click', function() {
                this.style.transform = 'scale(0.98)';
                setTimeout(() => {
                    this.style.transform = '';
                }, 150);
            });
        });
    </script>
</body>
</html>
```
