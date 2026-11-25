# HTML-CSS-UNI
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Fluxo · Energia e água sob controle</title>
<script>try{document.documentElement.dataset.theme=localStorage.getItem('tema')||(matchMedia('(prefers-color-scheme:dark)').matches?'dark':'light')}catch(e){document.documentElement.dataset.theme='dark'}</script>
<link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin><link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<link rel="stylesheet" href="style.css">
</head>
<body>
<div class="fundo" aria-hidden="true"><i></i><i></i></div>

<header class="topo">
  <a class="marca" href="#inicio">
    <div class="logo"><svg viewBox="0 0 24 24"><path d="M3 12h4l3-8 4 16 3-8h4" /></svg></div>
    <div><h1>Fluxo</h1></div>
  </a>
  <nav class="nav" id="nav"><a href="#inicio">Início</a><a href="#painel">Painel</a><a href="#recursos">Recursos</a></nav>
  <div class="direita">
    <div class="status"><span id="ponto" class="ponto"></span><span id="statusTxt">Conectando…</span></div>
    <div class="relogio" id="relogio">--:--:--</div>
    <button class="tema" id="tema" aria-label="Alternar tema"><svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M2 12h2M20 12h2M5 5l1.5 1.5M17.5 17.5L19 19M5 19l1.5-1.5M17.5 6.5L19 5"/></svg></button>
    <button class="menu" id="menu" aria-label="Abrir menu"><svg viewBox="0 0 24 24"><path d="M4 7h16M4 12h16M4 17h16"/></svg></button>
  </div>
</header>

<section class="hero" id="inicio">
  <div class="hero-txt">
    <h2>Energia e água, <em>sob controle.</em></h2>
    <p>Veja o seu consumo em tempo real e receba um alerta no instante em que algo sai do normal.</p>
    <div class="hero-bt"><a class="btn" href="#painel">Ver painel</a><a class="btn sec" href="#recursos">Conhecer recursos</a></div>
  </div>
  <div class="hero-vis">
    <div class="vidro flut">
      <small><span class="ponto on" style="display:inline-block;margin-right:.4rem"></span>Ao vivo</small>
      <div class="lin"><span class="ic e">⚡</span><div><b id="heroE">–</b> A<small>Energia</small></div></div>
      <div class="lin"><span class="ic a">💧</span><div><b id="heroA">–</b> %<small>Água</small></div></div>
      <svg viewBox="0 0 200 40" class="onda"><path d="M0 22 Q15 4 30 20 T60 20 T90 18 T120 22 T150 14 T200 20" /></svg>
    </div>
  </div>
</section>

<main>
<section class="secao grade" id="painel">
  <div class="cab"><h2>Seu consumo agora</h2><p>Acompanhe ao vivo ou teste cenários no modo simulação.</p></div>
  <div class="banner" id="banner" hidden><span class="pulso"></span><b id="bannerTxt"></b></div>

  <nav class="abas" role="tablist">
    <div class="deslize" id="deslize"></div>
    <button class="aba ativa" data-modo="real">Ao vivo</button>
    <button class="aba" data-modo="simulacao">Simulação</button>
  </nav>

  <section class="cards">
    <article class="card energia" id="cardE">
      <div class="card-topo">
        <div class="icone"><svg viewBox="0 0 24 24"><path d="M13 2L4 14h7l-1 8 9-12h-7z"/></svg></div>
        <div><h2>Energia</h2><small>Corrente elétrica</small></div>
        <span class="selo" id="selE">Normal</span>
      </div>
      <div class="corpo">
        <svg class="anel" viewBox="0 0 120 120"><circle class="trilho" cx="60" cy="60" r="52"/><circle class="prog" id="anelE" cx="60" cy="60" r="52"/></svg>
        <div class="centro"><span class="pct" id="pctE">0%</span><span class="peq">do limite</span></div>
        <div class="num"><div class="valor"><span id="valE">0.0</span><em>A</em></div><div class="tend" id="tendE">—</div><p class="info">Limite <b id="limE">–</b> A</p></div>
      </div>
    </article>

    <article class="card agua" id="cardA">
      <div class="card-topo">
        <div class="icone"><svg viewBox="0 0 24 24"><path d="M12 2.5S5 10 5 15a7 7 0 0014 0c0-5-7-12.5-7-12.5z"/></svg></div>
        <div><h2>Água</h2><small>Umidade / fluxo</small></div>
        <span class="selo" id="selA">Normal</span>
      </div>
      <div class="corpo">
        <svg class="anel" viewBox="0 0 120 120"><circle class="trilho" cx="60" cy="60" r="52"/><circle class="prog" id="anelA" cx="60" cy="60" r="52"/></svg>
        <div class="centro"><span class="pct" id="pctA">0%</span><span class="peq">do limite</span></div>
        <div class="num"><div class="valor"><span id="valA">0.0</span><em>%</em></div><div class="tend" id="tendA">—</div><p class="info">Limite <b id="limA">–</b> %</p></div>
      </div>
    </article>
  </section>

  <section class="graficos">
    <article class="painel"><h3>Histórico de energia <small>últimas 15 leituras</small></h3><div id="grE" class="grafico"></div></article>
    <article class="painel"><h3>Histórico de água <small>últimas 15 leituras</small></h3><div id="grA" class="grafico"></div></article>
  </section>

  <section class="painel sim" id="painelSim" hidden>
    <h3>Teste um cenário <small>não altera o banco real</small></h3>
    <div class="botoes">
      <button class="btn perigo" data-sim="anomalia">⚡ Gerar anomalia</button>
      <button class="btn" data-sim="resetar">↺ Normalizar</button>
      <button class="btn sec" data-sim="semana">Projeção 1 semana</button>
      <button class="btn sec" data-sim="mes">Projeção 1 mês</button>
    </div>
    <div id="proj" class="proj" hidden></div>
  </section>

  <section class="painel">
    <h3>Resumo do consumo <small>leituras reais</small></h3>
    <div class="tabela-wrap"><table>
      <thead><tr><th>Sensor</th><th>Leituras</th><th>Média</th><th>Pico</th><th>Anomalias</th></tr></thead>
      <tbody id="rel"><tr><td colspan="5"><div class="esqueleto"></div></td></tr></tbody>
    </table></div>
    <p class="nota" id="relData"></p>
  </section>
</section>
</main>

<section class="secao rev" id="recursos">
  <div class="cab"><h2>Tudo o que você precisa</h2><p>Simples de usar, rápido de entender.</p></div>
  <div class="trio">
    <article class="painel"><div class="ic e">📊</div><h3>Tempo real</h3><p>Os números se atualizam sozinhos, sem precisar recarregar a página.</p></article>
    <article class="painel"><div class="ic r">🚨</div><h3>Alertas na hora</h3><p>Se o consumo passa do limite, o painel avisa imediatamente.</p></article>
    <article class="painel"><div class="ic a">🧪</div><h3>Teste cenários</h3><p>Simule picos e projeções de custo sem mexer nos dados reais.</p></article>
  </div>
</section>

<footer class="rodape"><p class="copy">© 2026 Fluxo · Monitoramento de energia e água</p></footer>

<div class="toast" id="toast" hidden></div>
<script src="app.js"></script>
</body>
</html>
