<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>F1 Fantasy League - 2026</title>
    <style>
        :root {
            --f1-red: #e10600;
            --dark-bg: #15151e;
            --card-bg: #1f1f2b;
            --border-color: #38384f;
            --text-main: #ffffff;
            --text-muted: #a0a0b8;
            --green: #00d26a;
            --gold: #ffd700;
        }
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: var(--dark-bg); color: var(--text-main); line-height: 1.5; }
        .hidden { display: none !important; }
        .container { max-width: 1100px; margin: 0 auto; padding: 15px; }

        .auth-box { max-width: 420px; margin: 30px auto; background: var(--card-bg); padding: 25px; border-radius: 12px; border-top: 4px solid var(--f1-red); box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
        .logo-header { text-align: center; margin-bottom: 20px; }
        .f1-tag { background: var(--f1-red); color: white; font-weight: 900; padding: 3px 8px; border-radius: 4px; font-style: italic; }
        .logo-header h1 { margin-top: 10px; font-size: 1.5rem; letter-spacing: 1px; }
        .logo-header p { color: var(--text-muted); font-size: 0.9rem; }

        .tabs { display: flex; margin-bottom: 20px; border-bottom: 1px solid var(--border-color); }
        .tabs button { flex: 1; padding: 10px; background: none; border: none; color: var(--text-muted); cursor: pointer; font-weight: bold; }
        .tabs button.active { color: white; border-bottom: 3px solid var(--f1-red); }

        .input-group { margin-bottom: 15px; }
        .input-group label { display: block; font-size: 0.85rem; margin-bottom: 5px; color: var(--text-muted); }
        .input-group input { width: 100%; padding: 12px; border-radius: 6px; border: 1px solid var(--border-color); background: #12121a; color: white; font-size: 1rem; }

        .btn-primary { width: 100%; padding: 14px; background: var(--f1-red); color: white; border: none; border-radius: 6px; font-weight: bold; cursor: pointer; font-size: 1rem; }
        .btn-secondary { padding: 10px 14px; background: #2e2e42; color: white; border: 1px solid var(--border-color); border-radius: 6px; cursor: pointer; }
        .btn-large { margin-top: 20px; font-size: 1.1rem; }
        .btn-logout { background: transparent; border: 1px solid var(--f1-red); color: var(--f1-red); padding: 5px 10px; border-radius: 4px; cursor: pointer; margin-left: 8px; font-size: 0.8rem; }

        .navbar { background: #0f0f15; padding: 12px 15px; display: flex; justify-content: space-between; align-items: center; border-bottom: 2px solid var(--f1-red); flex-wrap: wrap; gap: 8px; }
        .badge { padding: 3px 6px; border-radius: 4px; font-size: 0.7rem; font-weight: bold; margin-right: 5px; text-transform: uppercase; }
        .badge-supreme { background: var(--gold); color: black; }
        .badge-admin { background: var(--f1-red); color: white; }
        .badge-serie-a { background: #0077ff; color: white; }
        .badge-serie-b { background: #55556e; color: white; }

        .main-menu { background: var(--card-bg); display: flex; justify-content: center; gap: 6px; padding: 8px; flex-wrap: wrap; }
        .menu-btn { background: transparent; border: none; color: var(--text-muted); padding: 8px 12px; cursor: pointer; font-weight: bold; border-radius: 6px; font-size: 0.85rem; }
        .menu-btn.active { background: #2c2c3e; color: white; }

        .gp-banner { background: linear-gradient(90deg, #252536, #1b1b26); padding: 15px; border-radius: 10px; border-left: 5px solid var(--f1-red); display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; flex-wrap: wrap; gap: 10px; }
        .gp-label { font-size: 0.7rem; color: var(--f1-red); font-weight: bold; letter-spacing: 1px; }
        .status-open { background: rgba(0, 210, 106, 0.2); color: var(--green); padding: 5px 10px; border-radius: 20px; font-weight: bold; font-size: 0.8rem; }

        .instruction { color: var(--text-muted); margin-bottom: 12px; font-size: 0.9rem; }
        .grid-form { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 10px; }
        .pos-row { background: var(--card-bg); padding: 10px; border-radius: 8px; display: flex; align-items: center; justify-content: space-between; border: 1px solid var(--border-color); }
        .pos-number { font-weight: 900; width: 38px; color: var(--f1-red); }
        .pos-pts { font-size: 0.75rem; color: var(--text-muted); margin-right: 8px; }
        .pos-row select { flex: 1; padding: 8px; background: #12121a; color: white; border: 1px solid var(--border-color); border-radius: 5px; font-size: 0.9rem; }

        .cycle-info { background: var(--card-bg); padding: 15px; border-radius: 8px; margin-bottom: 15px; text-align: center; border: 1px solid var(--border-color); }
        .divisions-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 15px; }
        @media (max-width: 768px) { .divisions-grid { grid-template-columns: 1fr; } }

        .division-card { background: var(--card-bg); padding: 15px; border-radius: 10px; overflow-x: auto; }
        .serie-a { border-top: 4px solid var(--gold); }
        .serie-b { border-top: 4px solid #8a8aa3; }
        table { width: 100%; border-collapse: collapse; margin-top: 10px; }
        th, td { padding: 8px; text-align: left; border-bottom: 1px solid var(--border-color); font-size: 0.9rem; }
        th { color: var(--text-muted); font-size: 0.8rem; }
        .zone-up { border-left: 4px solid var(--green); }
        .zone-down { border-left: 4px solid var(--f1-red); }

        .points-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(120px, 1fr)); gap: 8px; margin-top: 12px; }
        .point-box { background: var(--card-bg); padding: 10px; border-radius: 8px; text-align: center; border: 1px solid var(--border-color); }
        .admin-card { background: var(--card-bg); padding: 15px; border-radius: 10px; margin-bottom: 15px; border: 1px solid var(--border-color); }
        .admin-card h3 { margin-bottom: 10px; color: var(--gold); font-size: 1.1rem; }
        .admin-row { display: flex; gap: 8px; flex-wrap: wrap; }
        .admin-row input { flex: 1; min-width: 200px; padding: 10px; background: #12121a; border: 1px solid var(--border-color); color: white; border-radius: 6px; }
        .user-manage-row { display: flex; justify-content: space-between; align-items: center; padding: 10px 0; border-bottom: 1px solid var(--border-color); }

        .error-msg { color: #ff4d4d; margin-top: 10px; text-align: center; font-size: 0.9rem; }
        .success-msg { color: var(--green); margin-top: 12px; text-align: center; font-weight: bold; }
    </style>
</head>
<body>
    <div id="auth-screen" class="container auth-box">
        <div class="logo-header">
            <span class="f1-tag">F1</span>
            <h1>FANTASY GRID 2026</h1>
            <p>Aposte no grid, suba para a Série A e conquiste o campeonato.</p>
        </div>

        <div class="tabs">
            <button id="tab-login" class="active" onclick="switchAuthTab('login')">Entrar</button>
            <button id="tab-register" onclick="switchAuthTab('register')">Criar Conta</button>
        </div>

        <form id="login-form" onsubmit="handleLogin(event)">
            <div class="input-group">
                <label>Usuário</label>
                <input type="text" id="login-user" required placeholder="Seu nome de usuário">
            </div>
            <div class="input-group">
                <label>Senha</label>
                <input type="password" id="login-pass" required placeholder="Sua senha">
            </div>
            <button type="submit" class="btn-primary">Entrar no Paddock</button>
        </form>

        <form id="register-form" class="hidden" onsubmit="handleRegister(event)">
            <div class="input-group">
                <label>Escolha um Usuário</label>
                <input type="text" id="reg-user" required placeholder="Ex: SennaForever">
            </div>
            <div class="input-group">
                <label>Crie uma Senha</label>
                <input type="password" id="reg-pass" required placeholder="Mínimo 4 caracteres">
            </div>
            <button type="submit" class="btn-primary">Registrar Piloto (Início na Série B)</button>
        </form>
        <p id="auth-error" class="error-msg"></p>
    </div>

    <div id="app-screen" class="hidden">
        <header class="navbar">
            <div class="nav-brand">
                <span class="f1-tag">F1</span> <strong>FANTASY 2026</strong>
            </div>
            <div class="nav-user-info">
                <span id="user-badge" class="badge"></span>
                <span id="user-display-name"></span>
                <button onclick="logout()" class="btn-logout">Sair</button>
            </div>
        </header>

        <nav class="main-menu">
            <button class="menu-btn active" onclick="showSection('bet-section', this)">🏎️ Apostar</button>
            <button class="menu-btn" onclick="showSection('ranking-section', this)">🏆 Ranking</button>
            <button class="menu-btn" onclick="showSection('rules-section', this)">📊 Pontos</button>
            <button id="admin-menu-btn" class="menu-btn hidden" onclick="showSection('admin-section', this)">⚙️ Admin</button>
        </nav>

        <main class="container">
            <section id="bet-section">
                <div class="gp-banner">
                    <div>
                        <span class="gp-label">PRÓXIMO GRANDE PRÊMIO</span>
                        <h2 id="current-gp-title">GP de Las Vegas</h2>
                        <p id="current-gp-date">Data: 22 de Novembro de 2026</p>
                    </div>
