
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub HTTP Injector Bot</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        }
        
        body {
            background: #0d1117;
            color: #c9d1d9;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            background: #161b22;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
            border: 1px solid #30363d;
            height: 90vh;
            display: flex;
            flex-direction: column;
        }
        
        .header {
            background: #0d1117;
            padding: 16px 20px;
            display: flex;
            align-items: center;
            border-bottom: 1px solid #30363d;
            justify-content: space-between;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        .logo-icon {
            width: 32px;
            height: 32px;
            background: #238636;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: white;
            font-size: 18px;
        }
        
        .logo-text {
            color: white;
            font-size: 20px;
            font-weight: 600;
        }
        
        .status {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .status-indicator {
            width: 10px;
            height: 10px;
            background: #238636;
            border-radius: 50%;
        }
        
        .status-text {
            color: #238636;
            font-size: 14px;
        }
        
        .main-content {
            display: flex;
            flex: 1;
            overflow: hidden;
        }
        
        .sidebar {
            width: 280px;
            background: #161b22;
            border-right: 1px solid #30363d;
            padding: 16px;
            overflow-y: auto;
        }
        
        .section-title {
            color: #f78166;
            font-size: 14px;
            margin-bottom: 12px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            font-weight: 600;
        }
        
        .repo-list {
            list-style: none;
        }
        
        .repo-item {
            padding: 10px 12px;
            margin-bottom: 6px;
            background: #21262d;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.2s;
            color: #c9d1d9;
            font-size: 14px;
            border: 1px solid #30363d;
        }
        
        .repo-item:hover {
            background: #30363d;
            transform: translateX(4px);
        }
        
        .repo-item.active {
            background: #238636;
            color: white;
            border-color: #238636;
        }
        
        .chat-container {
            flex: 1;
            display: flex;
            flex-direction: column;
            overflow: hidden;
        }
        
        .chat-header {
            padding: 12px 16px;
            background: #161b22;
            border-bottom: 1px solid #30363d;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .chat-header h3 {
            color: #c9d1d9;
            font-size: 16px;
            font-weight: 500;
        }
        
        .chat-messages {
            flex: 1;
            padding: 16px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        
        .message {
            max-width: 80%;
            padding: 12px 16px;
            border-radius: 12px;
            line-height: 1.5;
            position: relative;
            animation: fadeIn 0.3s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .bot-message {
            background: #21262d;
            color: #c9d1d9;
            align-self: flex-start;
            border-bottom-left-radius: 4px;
            border: 1px solid #30363d;
        }
        
        .user-message {
            background: #238636;
            color: white;
            align-self: flex-end;
            border-bottom-right-radius: 4px;
        }
        
        .message-header {
            font-size: 12px;
            opacity: 0.7;
            margin-bottom: 6px;
            display: flex;
            align-items: center;
            gap: 4px;
        }
        
        .bot-icon {
            width: 14px;
            height: 14px;
            background: #238636;
            border-radius: 50%;
            display: inline-block;
            margin-right: 4px;
        }
        
        .user-icon {
            width: 14px;
            height: 14px;
            background: #2ea44f;
            border-radius: 50%;
            display: inline-block;
            margin-right: 4px;
        }
        
        .message-content {
            font-size: 14px;
            line-height: 1.4;
        }
        
        .code-block {
            background: #0d1117;
            border: 1px solid #30363d;
            border-radius: 6px;
            padding: 10px;
            margin: 8px 0;
            font-family: 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
            font-size: 13px;
            color: #c9d1d9;
            overflow-x: auto;
            line-height: 1.4;
        }
        
        .chat-input {
            padding: 16px;
            background: #161b22;
            border-top: 1px solid #30363d;
        }
        
        .input-group {
            display: flex;
            gap: 8px;
            background: #21262d;
            border-radius: 6px;
            padding: 2px;
            border: 1px solid #30363d;
        }
        
        .input-field {
            flex: 1;
            background: transparent;
            border: none;
            padding: 10px 12px;
            color: #c9d1d9;
            font-size: 14px;
            outline: none;
        }
        
        .send-btn {
            background: #238636;
            color: white;
            border: none;
            width: 36px;
            height: 36px;
            border-radius: 6px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            transition: all 0.2s;
        }
        
        .send-btn:hover {
            background: #2ea44f;
        }
        
        .controls {
            display: flex;
            gap: 8px;
            margin-top: 12px;
        }
        
        .control-btn {
            flex: 1;
            padding: 8px 12px;
            background: #21262d;
            color: #c9d1d9;
            border: 1px solid #30363d;
            border-radius: 6px;
            cursor: pointer;
            font-size: 13px;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
        }
        
        .control-btn:hover {
            background: #30363d;
        }
        
        .control-btn.primary {
            background: #238636;
            color: white;
            border-color: #238636;
        }
        
        .control-btn.primary:hover {
            background: #2ea44f;
            border-color: #2ea44f;
        }
        
        .loading {
            display: flex;
            align-items: center;
            gap: 8px;
            color: #238636;
            font-size: 14px;
        }
        
        .dots {
            display: flex;
            gap: 2px;
        }
        
        .dot {
            width: 6px;
            height: 6px;
            background: #238636;
            border-radius: 50%;
            animation: pulse 1.5s infinite ease-in-out;
        }
        
        .dot:nth-child(2) {
            animation-delay: 0.2s;
        }
        
        .dot:nth-child(3) {
            animation-delay: 0.4s;
        }
        
        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 0.7; }
            50% { transform: scale(1.2); opacity: 1; }
        }
        
        .command-suggestions {
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
            margin-top: 12px;
        }
        
        .suggestion {
            background: #21262d;
            color: #c9d1d9;
            padding: 6px 10px;
            border-radius: 12px;
            font-size: 12px;
            cursor: pointer;
            transition: all 0.2s;
            border: 1px solid #30363d;
        }
        
        .suggestion:hover {
            background: #30363d;
            border-color: #238636;
        }
        
        .metrics {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
            margin-top: 12px;
        }
        
        .metric {
            background: #21262d;
            padding: 12px;
            border-radius: 8px;
            text-align: center;
            border: 1px solid #30363d;
        }
        
        .metric-value {
            font-size: 18px;
            font-weight: 600;
            color: #238636;
            margin-bottom: 4px;
        }
        
        .metric-label {
            font-size: 11px;
            color: #8b949e;
        }
        
        /* GitHub style alerts */
        .alert {
            padding: 12px;
            border-radius: 6px;
            margin: 8px 0;
            font-size: 14px;
            border: 1px solid;
        }
        
        .alert-success {
            background-color: #1f6e34;
            border-color: #238636;
            color: #aff5b4;
        }
        
        .alert-warning {
            background-color: #5a4102;
            border-color: #8c6b07;
            color: #f5e8c0;
        }
        
        .alert-error {
            background-color: #5a2020;
            border-color: #932626;
            color: #f8aba6;
        }
        
        @media (max-width: 768px) {
            .main-content {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                max-height: 180px;
            }
            
            .message {
                max-width: 90%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="logo">
                <div class="logo-icon">AI</div>
                <div class="logo-text">GitHub HTTP Injector</div>
            </div>
            <div class="status">
                <div class="status-indicator"></div>
                <span class="status-text">Conectado a GitHub</span>
            </div>
        </div>
        
        <div class="main-content">
            <div class="sidebar">
                <h3 class="section-title">Repositorios GitHub</h3>
                <ul class="repo-list">
                    <li class="repo-item active">anthzz-berrocal/portfolio</li>
                    <li class="repo-item">anthzz-berrocal/chat-bot</li>
                    <li class="repo-item">anthzz-berrocal/api-injector</li>
                    <li class="repo-item">anthzz-berrocal/data-science</li>
                    <li class="repo-item">anthzz-berrocal/web-security</li>
                </ul>
                
                <h3 class="section-title">Comandos GitHub</h3>
                <div class="command-suggestions">
                    <div class="suggestion">/inject http</div>
                    <div class="suggestion">/scan repo</div>
                    <div class="suggestion">/analyze security</div>
                    <div class="suggestion">/generate token</div>
                </div>
                
                <h3 class="section-title">Estadísticas</h3>
                <div class="metrics">
                    <div class="metric">
                        <div class="metric-value">98.7%</div>
                        <div class="metric-label">Éxito</div>
                    </div>
                    <div class="metric">
                        <div class="metric-value">2.3s</div>
                        <div class="metric-label">Respuesta</div>
                    </div>
                    <div class="metric">
                        <div class="metric-value">1,247</div>
                        <div class="metric-label">Inyecciones</div>
                    </div>
                    <div class="metric">
                        <div class="metric-value">4.9</div>
                        <div class="metric-label">Calificación</div>
                    </div>
                </div>
            </div>
            
            <div class="chat-container">
                <div class="chat-header">
                    <h3>anthzz-berrocal/portfolio</h3>
                </div>
                
                <div class="chat-messages" id="chatMessages">
                    <div class="message bot-message">
                        <div class="message-header">
                            <div class="bot-icon"></div>
                            GitHub Injector Bot • Ahora
                        </div>
                        <div class="message-content">
                            🔧 <strong>Conectado a GitHub</strong><br>
                            Usuario: <strong>anthzz-berrocal</strong><br>
                            Repositorio: <strong>anthzz-berrocal/portfolio</strong><br>
                            Permisos: <strong>Admin</strong><br>
                            
                            <div class="alert alert-success">
                                ✅ Conexión SSH establecida<br>
                                ✅ Token de acceso válido<br>
                                ✅ Permisos de escritura confirmados
                            </div>
                            
                            Puedo ayudarte con operaciones de GitHub:
                            <div class="code-block">
# Comandos disponibles:<br>
/inject http [url]      - Inyectar código HTTP<br>
/scan vulnerabilities   - Escanear vulnerabilidades<br>
/analyze repo           - Analizar repositorio<br>
/generate token         - Generar token seguro<br>
/push changes           - Subir cambios<br>
/deploy site            - Desplegar sitio
                            </div>
                            ¿Qué acción deseas realizar?
                        </div>
                    </div>
                </div>
                
                <div class="chat-input">
                    <div class="input-group">
                        <input type="text" class="input-field" id="userInput" placeholder="Escribe un comando GitHub..." autofocus>
                        <button class="send-btn" id="sendBtn">➤</button>
                    </div>
                    
                    <div class="controls">
                        <button class="control-btn" id="scanBtn">
                            🔍 Escanear
                        </button>
                        <button class="control-btn primary" id="injectBtn">
                            ➕ Inyectar
                        </button>
                        <button class="control-btn" id="clearBtn">
                            🗑️ Limpiar
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Element references
        const chatMessages = document.getElementById('chatMessages');
        const userInput = document.getElementById('userInput');
        const sendBtn = document.getElementById('sendBtn');
        const scanBtn = document.getElementById('scanBtn');
        const injectBtn = document.getElementById('injectBtn');
        const clearBtn = document.getElementById('clearBtn');
        const repoItems = document.querySelectorAll('.repo-item');
        
        // Current repository
        let currentRepo = 'anthzz-berrocal/portfolio';
        let userToken = 'ghp_' + Math.random().toString(36).substring(2, 15) + Math.random().toString(36).substring(2, 15);
        
        // Add message to chat
        function addMessage(content, isUser = false) {
            const messageDiv = document.createElement('div');
            messageDiv.className = isUser ? 'message user-message' : 'message bot-message';
            
            const now = new Date();
            const timeString = now.getHours().toString().padStart(2, '0') + ':' + 
                              now.getMinutes().toString().padStart(2, '0');
            
            messageDiv.innerHTML = `
                <div class="message-header">
                    <div class="${isUser ? 'user-icon' : 'bot-icon'}"></div>
                    ${isUser ? 'Tú' : 'GitHub Injector Bot'} • ${timeString}
                </div>
                <div class="message-content">${content}</div>
            `;
            
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
        
        // Show loading indicator
        function showLoading() {
            const loadingDiv = document.createElement('div');
            loadingDiv.className = 'message bot-message';
            loadingDiv.innerHTML = `
                <div class="message-header">
                    <div class="bot-icon"></div>
                    GitHub Injector Bot • Ahora
                </div>
                <div class="message-content loading">
                    Procesando solicitud GitHub
                    <div class="dots">
                        <div class="dot"></div>
                        <div class="dot"></div>
                        <div class="dot"></div>
                    </div>
                </div>
            `;
            chatMessages.appendChild(loadingDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
            return loadingDiv;
        }
        
        // Remove loading indicator
        function removeLoading(loadingDiv) {
            if (loadingDiv && loadingDiv.parentNode) {
                loadingDiv.remove();
            }
        }
        
        // Process user input
        function processInput() {
            const input = userInput.value.trim();
            if (!input) return;
            
            // Add user message
            addMessage(input, true);
            userInput.value = '';
            
            // Show loading
            const loadingDiv = showLoading();
            
            // Process command after delay
            setTimeout(() => {
                removeLoading(loadingDiv);
                
                if (input.toLowerCase().includes('/scan') || input.toLowerCase().includes('escanear')) {
                    simulateGitHubScan();
                } else if (input.toLowerCase().includes('/inject') || input.toLowerCase().includes('inyectar')) {
                    simulateGitHubInjection(input);
                } else if (input.toLowerCase().includes('/analyze') || input.toLowerCase().includes('analizar')) {
                    simulateRepoAnalysis();
                } else if (input.toLowerCase().includes('/generate token') || input.toLowerCase().includes('generar token')) {
                    generateGitHubToken();
                } else if (input.toLowerCase().includes('/push') || input.toLowerCase().includes('subir')) {
                    simulatePushChanges();
                } else if (input.toLowerCase().includes('/deploy') || input.toLowerCase().includes('desplegar')) {
                    simulateDeploy();
                } else {
                    addMessage(`Comando no reconocido: "${input}"<br><br><strong>Comandos GitHub disponibles:</strong><br><div class="code-block">/scan repo - Escanear repositorio<br>/inject http [url] - Inyectar código HTTP<br>/analyze repo - Analizar repositorio<br>/generate token - Generar token seguro<br>/push changes - Subir cambios<br>/deploy site - Desplegar sitio</div>`);
                }
            }, 1500);
        }
        
        // Simulate GitHub scan
        function simulateGitHubScan() {
            addMessage(`🔍 Escaneando repositorio <strong>${currentRepo}</strong> en GitHub...<br><br>
            <div class="alert alert-warning">
                ⚠️ ADVERTENCIA DE SEGURIDAD<br>
                Se encontraron posibles vulnerabilidades:
                <div class="code-block">
• 2 vulnerabilidades XSS detectadas<br>
• 1 posible vector de inyección SQL<br>
• Headers de seguridad faltantes<br>
• Posible exposición de credenciales
                </div>
            </div>
            
            <div class="code-block">
RESULTADOS DEL ESCANEO:<br>
Repositorio: ${currentRepo}<br>
Último commit: ${new Date().toLocaleString()}<br>
Número de archivos: 47<br>
Líneas de código: 2,348<br>
<br>
NIVEL DE RIESGO: MEDIO<br>
RECOMENDACIÓN: Aplicar parches de seguridad
            </div>`);
        }
        
        // Simulate GitHub injection
        function simulateGitHubInjection(command) {
            const urlMatch = command.match(/https?:\/\/[^\s]+/);
            const targetUrl = urlMatch ? urlMatch[0] : 'https://api.github.com/repos/' + currentRepo + '/contents';
            
            addMessage(`🚀 Inyectando código HTTP en <strong>${currentRepo}</strong>...<br><br>
            <div class="alert alert-success">
                ✅ Inyección HTTP completada con éxito<br>
                Cambios aplicados al repositorio
            </div>
            
            <div class="code-block">
PAYLOAD INYECTADO:<br>
POST ${targetUrl} HTTP/1.1<br>
Host: api.github.com<br>
Authorization: Bearer ${userToken}<br>
Content-Type: application/json<br>
<br>
{"message":"Update via HTTP Injector","content":"${btoa('<script>console.log("Injected via GitHub API")</script>')}"}
            </div><br>
            🔧 Archivos modificados: 3<br>
            📦 Commits creados: 1<br>
            🚀 Despliegue iniciado...`);
        }
        
        // Simulate repo analysis
        function simulateRepoAnalysis() {
            addMessage(`📊 Analizando repositorio <strong>${currentRepo}</strong>...<br><br>
            <div class="code-block">
ANÁLISIS DEL REPOSITORIO:<br>
Nombre: ${currentRepo.split('/')[1]}<br>
Propietario: ${currentRepo.split('/')[0]}<br>
Estrellas: 142<br>
Forks: 89<br>
Issues abiertos: 12<br>
Último commit: 2 horas ago<br>
<br>
TECNOLOGÍAS DETECTADAS:<br>
• HTML5<br>
• CSS3<br>
• JavaScript<br>
• React<br>
• Node.js<br>
<br>
TAMAÑO: 4.2 MB<br>
ARCHIVOS: 47<br>
LÍNEAS DE CÓDIGO: 2,348
            </div>`);
        }
        
        // Generate GitHub token
        function generateGitHubToken() {
            addMessage(`🔐 Generando token de acceso personal para <strong>${currentRepo}</strong>...<br><br>
            <div class="alert alert-success">
                ✅ Token generado con éxito<br>
                Permisos: repo, admin:org, workflow
            </div>
            
            <div class="code-block">
TOKEN DE ACCESO:<br>
${userToken}<br>
<br>
EXPIRACIÓN: Nunca<br>
PERMISOS:<br>
• repo - Control total de repositorios<br>
• admin:org - Administración de organización<br>
• workflow - Administración de flujos de trabajo<br>
• delete_repo - Eliminación de repositorios
            </div><br>
            <div class="alert alert-warning">
                ⚠️ ADVERTENCIA: Este token tiene permisos elevados.<br>
                Guárdalo en un lugar seguro y revócalo cuando no lo necesites.
            </div>`);
        }
        
        // Simulate push changes
        function simulatePushChanges() {
            addMessage(`📤 Subiendo cambios al repositorio <strong>${currentRepo}</strong>...<br><br>
            <div class="code-block">
git add .<br>
git commit -m "Update via HTTP Injector Bot"<br>
git push origin main
            </div><br>
            <div class="alert alert-success">
                ✅ Cambios subidos con éxito<br>
                Commit: <a href="#" style="color:#58a6ff">b3f8d2a</a><br>
                Rama: main<br>
                Archivos modificados: 5
            </div><br>
            🔄 Sincronizando con GitHub...<br>
            ✅ Repositorio actualizado`);
        }
        
        // Simulate deploy
        function simulateDeploy() {
            addMessage(`🚀 Desplegando sitio desde <strong>${currentRepo}</strong>...<br><br>
            <div class="code-block">
1. Clonando repositorio...<br>
2. Instalando dependencias...<br>
3. Construyendo proyecto...<br>
4. Desplegando en servidor...
            </div><br>
            <div class="alert alert-success">
                ✅ Despliegue completado con éxito<br>
                Sitio disponible en: <a href="https://${currentRepo.split('/')[1]}.github.io" style="color:#58a6ff">https://${currentRepo.split('/')[1]}.github.io</a>
            </div><br>
            🌐 URL: https://${currentRepo.split('/')[1]}.github.io<br>
            📊 Tiempo de despliegue: 42s<br>
            🚀 Versión: 2.3.1`);
        }
        
        // Event listeners
        sendBtn.addEventListener('click', processInput);
        
        userInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                processInput();
            }
        });
        
        scanBtn.addEventListener('click', () => {
            userInput.value = '/scan repo';
            processInput();
        });
        
        injectBtn.addEventListener('click', () => {
            userInput.value = '/inject http https://api.github.com';
            processInput();
        });
        
        clearBtn.addEventListener('click', () => {
            chatMessages.innerHTML = '';
            addMessage('Chat limpiado. ¿Qué acción de GitHub deseas realizar?');
        });
        
        // Repository selection
        repoItems.forEach(item => {
            item.addEventListener('click', () => {
                repoItems.forEach(i => i.classList.remove('active'));
                item.classList.add('active');
                currentRepo = item.textContent;
                addMessage(`Repositorio GitHub cambiado a: <strong>${currentRepo}</strong>. ¿Qué acción deseas realizar?`);
            });
        });
        
        // Suggestion buttons
        document.querySelectorAll('.suggestion').forEach(suggestion => {
            suggestion.addEventListener('click', () => {
                userInput.value = suggestion.textContent;
                userInput.focus();
            });
        });
        
        // Initial welcome message
        setTimeout(() => {
            addMessage(`🔐 <strong>Conexión establecida con GitHub</strong><br>
            Usuario: <strong>anthzz-berrocal</strong><br>
            Email: <strong>antonioberrocal62@gmail.com</strong><br>
            Estado: <span style="color:#238636">●</span> Conectado<br>
            Token: <span style="font-family:monospace">${userToken.substring(0, 10)}...</span><br><br>
            ¿Listo para gestionar tu repositorio?`);
        }, 1000);
    </script>
</body>
</html>
```
