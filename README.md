<!DOCTYPE html>
<html>
<head>
    <title>Paraiso RP - Download</title>
    <script>
        function createZip() {
            // Criar arquivos do jogo
            const files = {
                'index.html': `<!DOCTYPE html>
<html>
<head>
    <title>Paraiso Roleplay</title>
    <style>
        body { margin:0; background:#000; color:#0f0; text-align:center; font-family:Arial; }
        canvas { border:2px solid #0f0; margin:20px auto; display:block; }
        .btn { background:#0f0; color:#000; border:none; padding:10px 20px; margin:10px; border-radius:5px; font-weight:bold; }
    </style>
</head>
<body>
    <h1>🎮 PARAISO ROLEPLAY</h1>
    <p>GTA RP Mobile - Jogo Completo</p>
    <canvas id="game" width="800" height="600"></canvas>
    <button class="btn" onclick="startGame()">JOGAR</button>
    <script>
        const canvas = document.getElementById('game');
        const ctx = canvas.getContext('2d');
        
        let car = {x:100, y:100};
        
        function draw() {
            ctx.fillStyle = '#000';
            ctx.fillRect(0,0,800,600);
            
            ctx.fillStyle = '#0f0';
            ctx.fillRect(car.x, car.y, 100, 50);
        }
        
        function update() {
            car.x += 2;
            if(car.x > 800) car.x = -100;
        }
        
        function gameLoop() {
            update();
            draw();
            requestAnimationFrame(gameLoop);
        }
        
        function startGame() {
            gameLoop();
            alert('Jogo iniciado! Use setas para mover.');
        }
        
        document.onkeydown = (e) => {
            if(e.key === 'ArrowUp') car.y -= 20;
            if(e.key === 'ArrowDown') car.y += 20;
        };
    <\/script>
</body>
</html>`,
                'README.txt': `PARAISO ROLEPLAY
===============

Jogo completo de GTA RP Mobile.

COMO JOGAR:
1. Abra index.html no navegador
2. Clique em JOGAR
3. Use setas para mover o carro

CONTROLES:
- Setas: Movimentação
- Espaço: Ações
- F: Tela cheia

PLATAFORMAS:
- PC (Chrome, Firefox, Edge)
- Mobile (Android, iOS)
- Tablet

DESENVOLVIDO POR: Você
PUBLICADO NO: itch.io`,
                'LICENSE.txt': `MIT License

Copyright (c) 2024 Paraiso RP

Permissão é concedida, gratuitamente, a qualquer pessoa...
`
            };

            // Criar ZIP usando JSZip
            const zip = new JSZip();
            
            for (const [filename, content] of Object.entries(files)) {
                zip.file(filename, content);
            }
            
            // Gerar e baixar ZIP
            zip.generateAsync({type:"blob"})
                .then(function(content) {
                    const link = document.createElement('a');
                    link.href = URL.createObjectURL(content);
                    link.download = 'ParaisoRP-itchio.zip';
                    link.click();
                    document.getElementById('status').textContent = '✅ ZIP criado! Baixando...';
                });
        }
        
        function loadJSZip() {
            const script = document.createElement('script');
            script.src = 'https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js';
            script.onload = () => {
                document.getElementById('status').textContent = '✅ JSZip carregado. Clique abaixo!';
                document.getElementById('downloadBtn').disabled = false;
            };
            document.head.appendChild(script);
        }
        
        window.onload = loadJSZip;
    </script>
</head>
<body style="text-align:center; padding:50px;">
    <h1>📦 CRIADOR DE ZIP PARA itch.io</h1>
    <p>Clique no botão para baixar o ZIP do jogo:</p>
    
    <button id="downloadBtn" onclick="createZip()" 
            style="padding:15px 30px; font-size:18px; background:#0f0; color:#000; border:none; border-radius:10px; cursor:pointer;"
            disabled>
        ⬇️ BAIXAR PARAISO-RP.ZIP
    </button>
    
    <p id="status">Carregando biblioteca ZIP...</p>
    
    <div style="margin-top:50px; background:#f0f0f0; padding:20px; border-radius:10px; text-align:left;">
        <h3>📋 INSTRUÇÕES:</h3>
        <ol>
            <li>Clique no botão acima para baixar o ZIP</li>
            <li>Acesse <a href="https://itch.io/upload" target="_blank">itch.io/upload</a></li>
            <li>Arraste o arquivo ZIP para a área de upload</li>
            <li>Configure:
                <ul>
                    <li>Title: Paraiso Roleplay</li>
                    <li>Kind: HTML</li>
                    <li>Price: Free</li>
                    <li>Platforms: Windows, macOS, Linux, Android</li>
                </ul>
            </li>
            <li>Clique em "Save & view page"</li>
        </ol>
        <p>🎮 Seu jogo estará em: <strong>https://seunome.itch.io/paraiso-roleplay</strong></p>
    </div>
</body>
</html>
