<html lang="pt-br">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Nosso Amor 💖</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    a[href="https://github.com/oliveirosvic"] {
    display: none;
    }
    :root{
      --bg:#0f0f14; --card:#171721; --accent:#ff6aa2; --text:#f6f7fb; --sub:#b8bbcf;
    }
    *{box-sizing:border-box}
    body{margin:0; font-family:Poppins,system-ui,-apple-system,Segoe UI,Roboto; color:var(--text); background:radial-gradient(1200px 800px at 20% 0%, #1b1b28, #0f0f14);}    
    .wrap{max-width:980px; margin:0 auto; padding:24px;}
    header{display:flex; gap:18px; align-items:center; justify-content:center; flex-wrap:wrap; text-align:center;}
    .avatar{width:110px; aspect-ratio:1/1; border-radius:50%; object-fit:cover; border:3px solid var(--accent); box-shadow:0 8px 24px rgba(255,106,162,.25)}
    h1{font-size:clamp(28px,4vw,42px); margin:8px 0 0}
    p.lead{color:var(--sub); margin:6px 0 0}

    .card{background:var(--card); border:1px solid rgba(255,255,255,.06); box-shadow:0 12px 32px rgba(0,0,0,.35); border-radius:18px; padding:18px;}

    /* Contador */
    .counter{display:grid; grid-template-columns:repeat(6, minmax(110px,1fr)); gap:10px; margin-top:18px}
    .tile{background:#141420; border:1px solid rgba(255,255,255,.06); border-radius:16px; padding:16px; text-align:center}
    .value{font-size:clamp(24px,4vw,36px); font-weight:700}
    .label{font-size:12px; letter-spacing:.1em; text-transform:uppercase; color:var(--sub)}

    /* Galeria */
    .gallery{display:grid; grid-template-columns:repeat(auto-fill, minmax(160px,1fr)); gap:10px; margin-top:18px}
    .gallery img{width:100%; aspect-ratio:1/1; object-fit:cover; border-radius:14px; transition:transform .2s ease, box-shadow .2s ease; cursor:zoom-in}
    .gallery img:hover{transform:translateY(-2px); box-shadow:0 10px 24px rgba(0,0,0,.35)}

    /* Player */
    .player{display:flex; gap:12px; align-items:center; flex-wrap:wrap; margin-top:8px}
    .btn{background:var(--accent); color:#101014; border:0; border-radius:999px; padding:10px 16px; font-weight:700; cursor:pointer; box-shadow:0 10px 24px rgba(255,106,162,.35)}
    .btn:active{transform:translateY(1px)}
    .hint{color:var(--sub); font-size:13px}

    footer{opacity:.8; text-align:center; font-size:12px; margin:28px 0 12px}

    @media (max-width:760px){ .counter{grid-template-columns:repeat(3,1fr);} }
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <!-- Substitua as imagens abaixo por fotos de vocês (mantenha os nomes/pastas ou ajuste os src) -->
      <img class="avatar" src="images/nos-1.jpg" alt="Foto 1 do casal">
      <div>
        <h1>Guilherme ❤ Viviane</h1>
        <p class="lead">Juntos desde <span id="sinceText"></span></p>
      </div>
    </header>

    <section class="card" aria-labelledby="contador-title">
      <h2 id="contador-title" style="margin:6px 0 4px">Quanto tempo estamos namorando</h2>
      <div class="counter" id="counter">
        <div class="tile"><div class="value" id="years">0</div><div class="label">anos</div></div>
        <div class="tile"><div class="value" id="months">0</div><div class="label">meses</div></div>
        <div class="tile"><div class="value" id="days">0</div><div class="label">dias</div></div>
        <div class="tile"><div class="value" id="hours">0</div><div class="label">horas</div></div>
        <div class="tile"><div class="value" id="minutes">0</div><div class="label">min</div></div>
        <div class="tile"><div class="value" id="seconds">0</div><div class="label">seg</div></div>
      </div>
    </section>

    <section class="card" aria-labelledby="fotos-title">
      <h2 id="fotos-title" style="margin:6px 0 10px">Nossas fotos</h2>
      <div class="gallery">
        <!-- Coloque suas fotos na pasta images e ajuste os nomes abaixo -->
        <img src="images/nos-1.jpg" alt="nós 1">
        <img src="images/nos-2.jpg" alt="nós 2">
        <img src="images/nos-3.jpg" alt="nós 3">
        <img src="images/nos-4.jpg" alt="nós 4">
        <img src="images/nos-5.jpg" alt="nós 5">
        <img src="images/nos-6.jpg" alt="nós 6">
        <img src="images/nos-7.jpg" alt="nós 7">
        <img src="images/nos-8.jpg" alt="nós 8">
      </div>
    </section>

    <section class="card" aria-labelledby="musica-title">
      <h2 id="musica-title" style="margin:6px 0 8px">Nossa música</h2>
      <div class="player">
        <button class="btn" id="playBtn">▶️ Tocar</button>
        <audio id="song" src="music/nossa-musica.mp3" preload="auto"></audio>
        <span class="hint">Dica: por política dos navegadores, o som só toca após você clicar em "Tocar".</span>
      </div>
    </section>

    <footer>
      Feito com 💖 – personalize este arquivo e hospede grátis (GitHub Pages / Netlify).
    </footer>
  </div>

  <script>
    // ======= CONFIGURAÇÃO RÁPIDA =======
    // 1) Coloque a data/hora do início do namoro (AAAA-MM-DDTHH:MM:SS)
    const START_ISO = '2024-05-05T00:00:00';
    // 2) Troque o título/nome lá no <h1> se quiser ;)

    // Mostra a data bonitinha
    const sinceText = document.getElementById('sinceText');
    sinceText.textContent = new Date(START_ISO).toLocaleString('pt-BR', {
      year:'numeric', month:'2-digit', day:'2-digit', hour:'2-digit', minute:'2-digit'
    });

    // Cálculo preciso em anos/meses/dias/horas/min/seg respeitando meses variáveis e anos bissextos
    function diffYMDHMS(startDate, now){
      let years = now.getFullYear() - startDate.getFullYear();
      // Se ainda não chegou o "aniversário" neste ano (considerando hora/min/seg), tira 1
      const beforeAnniv = () => {
        if (now.getMonth() !== startDate.getMonth()) return now.getMonth() < startDate.getMonth();
        if (now.getDate() !== startDate.getDate()) return now.getDate() < startDate.getDate();
        if (now.getHours() !== startDate.getHours()) return now.getHours() < startDate.getHours();
        if (now.getMinutes() !== startDate.getMinutes()) return now.getMinutes() < startDate.getMinutes();
        return now.getSeconds() < startDate.getSeconds();
      }
      if (beforeAnniv()) years--;

      const anniv = new Date(startDate);
      anniv.setFullYear(startDate.getFullYear() + years);

      let months = now.getMonth() - anniv.getMonth();
      if (months < 0) months += 12;

      const monthAnchor = new Date(anniv);
      monthAnchor.setMonth(anniv.getMonth() + months);

      let ms = now - monthAnchor;
      let days = Math.floor(ms / 86400000); ms -= days*86400000;
      let hours = Math.floor(ms / 3600000); ms -= hours*3600000;
      let minutes = Math.floor(ms / 60000); ms -= minutes*60000;
      let seconds = Math.floor(ms / 1000);

      return {years, months, days, hours, minutes, seconds};
    }

    const ids = ['years','months','days','hours','minutes','seconds'];
    function tick(){
      const start = new Date(START_ISO);
      const now = new Date();
      const d = diffYMDHMS(start, now);
      ids.forEach(id => document.getElementById(id).textContent = d[id]);
    }
    tick();
    setInterval(tick, 1000);

    // Player
    const playBtn = document.getElementById('playBtn');
    const audio = document.getElementById('song');
    let playing = false;
    playBtn.addEventListener('click', async () => {
      try{
        if(!playing){ await audio.play(); playing = true; playBtn.textContent = '⏸️ Pausar'; }
        else{ audio.pause(); playing = false; playBtn.textContent = '▶️ Tocar'; }
      }catch(e){ alert('Não foi possível iniciar o áudio automaticamente. Verifique o arquivo em music/nossa-musica.mp3'); }
    });
  </script>
</body>
</html>
