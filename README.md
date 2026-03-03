# TWEB25.1
<!doctype html>
<html lang="ro">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Lucrarea de laborator №2 — CSS — Real Madrid CF</title>

  <style>
    /* =========================
       0) RESET / BASE
    ========================== */
    *{ box-sizing: border-box; }
    html{ scroll-behavior: smooth; }
    body{
      margin:0;
      font-family: Arial, Helvetica, sans-serif;
      background: #0b1020;
      color:#eef2ff;
      line-height: 1.65;
    }
    img{ max-width:100%; display:block; }
    .muted{ color:#b8c4ea; }
    .small{ font-size: 12px; color:#b8c4ea; }

    /* =========================
       1) STRUCTURĂ (DIV-uri)
    ========================== */
    .page{
      max-width: 1100px;
      margin: 0 auto;
      padding: 0 16px 24px;
    }

    .header{
      margin: 16px 0 12px;
      padding: 18px 16px;
      border-radius: 16px;
      border: 1px solid rgba(255,255,255,.12);
      background:
        radial-gradient(520px 260px at 15% 10%, rgba(212,175,55,.28), transparent 60%),
        radial-gradient(520px 260px at 85% 80%, rgba(90,160,255,.22), transparent 60%),
        linear-gradient(180deg, rgba(255,255,255,.08), rgba(255,255,255,.03));
      box-shadow: 0 12px 30px rgba(0,0,0,.35);
    }

    .title{
      margin:0;
      font-size: 30px;
      letter-spacing: .2px;
    }

    .subtitle{
      margin: 6px 0 0;
      color:#b8c4ea;
    }

    /* layout: cuprins + conținut */
    .layout{
      display: grid;
      grid-template-columns: 320px 1fr;
      gap: 12px;
      align-items: start;
    }
    @media (max-width: 900px){
      .layout{ grid-template-columns: 1fr; }
    }

    .sidebar, .content{
      border-radius: 16px;
      border: 1px solid rgba(255,255,255,.12);
      background: rgba(255,255,255,.05);
      box-shadow: 0 10px 26px rgba(0,0,0,.25);
    }

    .sidebar{
      padding: 14px;
      position: sticky;
      top: 12px;
    }
    @media (max-width: 900px){
      .sidebar{ position: static; }
    }

    .content{
      padding: 14px;
    }

    .box{
      padding: 12px;
      border-radius: 14px;
      border: 1px solid rgba(255,255,255,.10);
      background: rgba(255,255,255,.04);
      margin: 12px 0;
    }

    /* =========================
       2) CUPRINS (LISTĂ LINKURI)
          + PSEUDO-CLASE
    ========================== */
    .tocTitle{
      margin:0 0 10px;
      font-size: 16px;
      color: #d4af37;
      letter-spacing: .3px;
    }

    .toc{
      margin:0;
      padding-left: 18px;
    }
    .toc li{ margin: 6px 0; }

    /* pseudo-clase pentru link-uri */
    .toc a:link{
      color:#b8c4ea;
      text-decoration: none;
      padding: 6px 8px;
      border-radius: 10px;
      display:inline-block;
      border:1px solid transparent;
    }
    .toc a:visited{
      color:#98a6d8;
    }
    .toc a:hover{
      color:#ffffff;
      background: rgba(255,255,255,.08);
      border-color: rgba(255,255,255,.14);
      transform: translateY(-1px);
    }
    .toc a:active{
      background: rgba(212,175,55,.20);
      border-color: rgba(212,175,55,.40);
      color:#fff;
    }

    /* efect vizual la secțiunea țintă (când dai click în cuprins) */
    .section:target{
      outline: 2px solid rgba(212,175,55,.55);
      box-shadow: 0 0 0 6px rgba(212,175,55,.12);
      scroll-margin-top: 14px;
    }

    /* =========================
       3) FORMATAREA TEXTULUI
    ========================== */
    h2{
      margin: 10px 0 6px;
      color: #d4af37;
      font-size: 22px;
    }
    h3{
      margin: 10px 0 6px;
      font-size: 16px;
    }
    p{ margin: 8px 0; }
    ul{ margin: 8px 0; }

    /* „first letter” + „first line” (efect / formatare) */
    .lead::first-letter{
      font-size: 42px;
      font-weight: bold;
      color: #d4af37;
      float:left;
      line-height: 1;
      padding-right: 8px;
      padding-top: 4px;
    }
    .lead::first-line{
      letter-spacing: .3px;
    }

    /* =========================
       4) EFECTE VIZUALE (extra)
    ========================== */
    .btnTop{
      display:inline-block;
      margin-top: 8px;
      padding: 8px 10px;
      border-radius: 12px;
      border: 1px solid rgba(255,255,255,.16);
      background: rgba(255,255,255,.06);
      color:#eef2ff;
      text-decoration:none;
    }
    .btnTop:hover{
      background: rgba(255,255,255,.10);
      transform: translateY(-1px);
    }

    /* carduri (trofee) */
    .grid{
      display:grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
    }
    @media (max-width: 900px){
      .grid{ grid-template-columns: 1fr; }
    }
    .card{
      padding: 12px;
      border-radius: 14px;
      border: 1px solid rgba(255,255,255,.12);
      background: rgba(17,26,51,.55);
      transition: transform .15s, background .15s, border-color .15s;
    }
    .card:hover{
      transform: translateY(-2px);
      background: rgba(17,26,51,.75);
      border-color: rgba(212,175,55,.30);
    }
    .num{
      font-size: 26px;
      font-weight: 900;
      color:#d4af37;
      margin-bottom: 4px;
    }

    /* tabel simplu */
    table{
      width:100%;
      border-collapse: collapse;
      border-radius: 12px;
      overflow:hidden;
      border: 1px solid rgba(255,255,255,.12);
      margin-top: 8px;
    }
    th, td{
      padding:10px;
      border-bottom:1px solid rgba(255,255,255,.08);
      text-align:left;
    }
    th{
      background: rgba(255,255,255,.06);
      color:#b8c4ea;
    }
    tr:hover{ background: rgba(255,255,255,.04); }

    /* footer */
    .footer{
      margin-top: 12px;
      padding: 10px;
      text-align:center;
      color:#b8c4ea;
      border-top: 1px solid rgba(255,255,255,.12);
    }
  </style>
</head>

<body>
  <div class="page" id="top">
    <!-- HEADER -->
    <div class="header">
      <h1 class="title">Lucrarea de laborator №2 — CSS</h1>
      <p class="subtitle">Tema: Real Madrid CF — pagină cu structură (DIV) + cuprins (link-uri) + pseudo-clase + efecte vizuale</p>
    </div>

    <!-- LAYOUT: SIDEBAR + CONTENT -->
    <div class="layout">
      <!-- SIDEBAR / CUPRINS -->
      <div class="sidebar">
        <div class="tocTitle">Cuprins</div>
        <ol class="toc">
          <li><a href="#despre">Despre club</a></li>
          <li><a href="#istorie">Istorie (pe scurt)</a></li>
          <li><a href="#stadion">Stadion</a></li>
          <li><a href="#palmares">Palmares</a></li>
          <li><a href="#lot">Lot (exemplu)</a></li>
          <li><a href="#concluzie">Concluzie</a></li>
        </ol>

        <div class="box">
          <div class="small"><b>Cerințe bifate:</b></div>
          <ul class="small" style="margin:8px 0 0;line-height:1.6">
            <li>Structură cu <b>div</b></li>
            <li>CSS pentru layout & text</li>
            <li>Cuprins ca listă de link-uri</li>
            <li>Pseudo-clase: <b>:link :visited :hover :active</b></li>
            <li>Efecte: shadow, hover, gradient, :target, ::first-letter</li>
          </ul>
        </div>

        <a class="btnTop" href="#top">↑ Sus</a>
      </div>

      <!-- CONTENT -->
      <div class="content">
        <!-- 1 -->
        <div class="box section" id="despre">
          <h2>Despre club</h2>
          <p class="lead">
            Real Madrid Club de Fútbol este un club de fotbal din Madrid, cunoscut pentru tradiție,
            performanțe și o cultură puternică a competiției. Clubul are o bază globală de suporteri
            și este asociat cu identitatea „Los Blancos”.
          </p>
          <p class="muted small">Textul îl înlocuiești cu cel din Lucrarea №1 (cerința 1).</p>
          <a class="btnTop" href="#top">↑ Sus</a>
        </div>

        <!-- 2 -->
        <div class="box section" id="istorie">
          <h2>Istorie (pe scurt)</h2>
          <p>
            Aici inserezi paragrafele despre istorie din prima lucrare: fondare, perioade importante,
            jucători legendari, momente memorabile.
          </p>
          <ul>
            <li>Fondare (data + context)</li>
            <li>Perioade / ere importante</li>
            <li>Realizări majore în competiții</li>
          </ul>
          <a class="btnTop" href="#top">↑ Sus</a>
        </div>

        <!-- 3 -->
        <div class="box section" id="stadion">
          <h2>Stadion</h2>
          <p>
            Secțiunea despre stadion: nume, capacitate, modernizări, importanță pentru club și suporteri.
          </p>

          <!-- imagine web (efect vizual simplu) -->
          <div class="box">
            <img
              style="border-radius:12px;border:1px solid rgba(255,255,255,.12)"
              src="https://images.unsplash.com/photo-1508098682722-e99c43a406b2?auto=format&fit=crop&w=1600&q=70"
              alt="Imagine stadion (ilustrativ)"
            />
            <div class="small" style="margin-top:6px">Imagine web (ilustrativă) — Unsplash</div>
          </div>

          <a class="btnTop" href="#top">↑ Sus</a>
        </div>

        <!-- 4 -->
        <div class="box section" id="palmares">
          <h2>Palmares</h2>
          <p>Exemplu de prezentare tip „carduri” (efect vizual la hover):</p>

          <div class="grid">
            <div class="card">
              <div class="num">36</div>
              <div><b>La Liga</b></div>
              <div class="small">exemplu (editează cu datele tale)</div>
            </div>
            <div class="card">
              <div class="num">15</div>
              <div><b>UEFA Champions League</b></div>
              <div class="small">exemplu (editează cu datele tale)</div>
            </div>
            <div class="card">
              <div class="num">20</div>
              <div><b>Copa del Rey</b></div>
              <div class="small">exemplu (editează cu datele tale)</div>
            </div>
          </div>

          <a class="btnTop" href="#top">↑ Sus</a>
        </div>

        <!-- 5 -->
        <div class="box section" id="lot">
          <h2>Lot (exemplu)</h2>
          <p class="muted small">
            Dacă în prima lucrare ai avut un tabel sau o listă cu jucători, o pui aici.
            Mai jos e un exemplu de tabel formatat cu CSS.
          </p>

          <table>
            <thead>
              <tr>
                <th>#</th>
                <th>Nume</th>
                <th>Poziție</th>
                <th>Țară</th>
              </tr>
            </thead>
            <tbody>
              <tr><td>1</td><td>Thibaut Courtois</td><td>GK</td><td>BEL</td></tr>
              <tr><td>2</td><td>Dani Carvajal</td><td>DF</td><td>ESP</td></tr>
              <tr><td>5</td><td>Jude Bellingham</td><td>MF</td><td>ENG</td></tr>
            </tbody>
          </table>

          <a class="btnTop" href="#top">↑ Sus</a>
        </div>

        <!-- 6 -->
        <div class="box section" id="concluzie">
          <h2>Concluzie</h2>
          <p>
            În această lucrare am creat o pagină HTML folosind structura cu <b>div</b> și am aplicat CSS
            pentru layout și formatare text. Cuprinsul este realizat ca o listă de link-uri și folosește
            pseudo-clasele <b>:link</b>, <b>:visited</b>, <b>:hover</b>, <b>:active</b>. Pentru efecte vizuale
            am utilizat: umbre, hover pe carduri, fundal gradient, <b>:target</b> la secțiunea selectată și
            <b>::first-letter</b>.
          </p>
          <a class="btnTop" href="#top">↑ Sus</a>
        </div>

        <div class="footer">
          © 2026 — Lucrarea de laborator №2 (CSS) — Prototip educațional
        </div>
      </div>
    </div>
  </div>
</body>
</html>
