# Tu-p-gina.-Com
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Acceso privado</title>
<style>
  * { margin:0; padding:0; box-sizing:border-box; }
  body {
    background:#050505; color:#f5f5f5;
    font-family:'Segoe UI', system-ui, sans-serif;
    min-height:100vh; display:flex; align-items:center; justify-content:center;
    padding:20px; overflow-x:hidden; position:relative;
  }
  .fondo-animado { position:fixed; inset:0; z-index:-2; overflow:hidden; background:#050505; }
  .aurora { position:absolute; width:60vw; height:60vw; border-radius:50%; filter:blur(80px); opacity:.4; animation:flotar 14s ease-in-out infinite; }
  .aurora.roja { background:radial-gradient(circle,#e01b24 0%,transparent 70%); top:-15%; left:-10%; }
  .aurora.azul { background:radial-gradient(circle,#1b6ee0 0%,transparent 70%); bottom:-20%; right:-15%; animation-delay:-5s; }
  .aurora.morada { background:radial-gradient(circle,#7a1be0 0%,transparent 70%); top:40%; left:45%; width:45vw; height:45vw; opacity:.25; animation-delay:-9s; }
  @keyframes flotar {
    0%,100%{transform:translate(0,0) scale(1);} 25%{transform:translate(8vw,6vh) scale(1.15);}
    50%{transform:translate(-5vw,10vh) scale(.9);} 75%{transform:translate(10vw,-8vh) scale(1.1);}
  }
  .particulas { position:fixed; inset:0; z-index:-1; pointer-events:none; overflow:hidden; }
  .particula { position:absolute; width:3px; height:3px; border-radius:50%; background:#fff; opacity:0; animation:subir linear infinite; }
  @keyframes subir {
    0%{transform:translateY(100vh) scale(0); opacity:0;} 10%{opacity:.9;}
    90%{opacity:.6;} 100%{transform:translateY(-10vh) scale(1.3); opacity:0;}
  }

  /* ====== PANTALLA DE CONTRASEÑA ====== */
  .pantalla-clave {
    display:flex; flex-direction:column; align-items:center; justify-content:center;
    width:100%; max-width:420px; text-align:center;
  }
  .escorpion-svg {
    width:110px; height:110px; margin-bottom:15px;
    filter: drop-shadow(0 0 25px rgba(224,27,36,.8)) drop-shadow(0 0 45px rgba(27,110,224,.4));
    animation: latidoEscorpion 2.5s ease-in-out infinite;
  }
  @keyframes latidoEscorpion {
    0%,100%{ transform:scale(1) rotate(0deg); }
    50%{ transform:scale(1.06) rotate(-3deg); }
  }
  .titulo-clave {
    font-size:1.6rem; letter-spacing:3px; margin-bottom:6px;
    background:linear-gradient(90deg,#e01b24,#f7e08a,#1b6ee0,#e01b24);
    background-size:300% auto;
    -webkit-background-clip:text; background-clip:text; color:transparent;
    animation:textoBrillo 5s linear infinite;
    text-transform:uppercase;
  }
  @keyframes textoBrillo { 0%{background-position:0% center;} 100%{background-position:300% center;} }
  .sub-clave { font-size:.85rem; color:#8a8a9a; margin-bottom:25px; letter-spacing:1px; }
  .input-clave {
    width:100%; max-width:300px; padding:14px 18px;
    background:rgba(15,15,18,.9); border:1px solid rgba(224,27,36,.5);
    border-radius:12px; color:#f5f5f5; font-size:1rem; text-align:center;
    letter-spacing:4px; margin-bottom:15px; outline:none;
    transition: border .2s, box-shadow .2s;
  }
  .input-clave:focus {
    border-color:#e01b24;
    box-shadow:0 0 25px rgba(224,27,36,.5);
  }
  .input-clave.error { border-color:#e74c3c; animation: shake 0.4s; }
  .btn-clave {
    background:linear-gradient(90deg,#e01b24,#1b6ee0);
    background-size:200% auto;
    color:#fff; border:none; padding:14px 40px; border-radius:50px;
    font-size:1rem; font-weight:700; cursor:pointer; letter-spacing:1px;
    transition:transform .2s, box-shadow .2s, background-position .4s;
    box-shadow:0 4px 25px rgba(224,27,36,.4);
  }
  .btn-clave:hover {
    transform:translateY(-2px) scale(1.03);
    background-position:right center;
    box-shadow:0 6px 35px rgba(27,110,224,.6);
  }
  .msg-error {
    font-size:.88rem; color:#e74c3c; margin-top:14px; min-height:20px;
    font-weight:600;
  }
  @keyframes shake {
    0%,100%{transform:translateX(0);} 25%{transform:translateX(-6px);} 75%{transform:translateX(6px);}
  }

  /* ====== CAJA PRINCIPAL ====== */
  .card {
    background:rgba(12,12,14,.82); backdrop-filter:blur(14px); -webkit-backdrop-filter:blur(14px);
    border:1px solid rgba(224,27,36,.35); border-radius:22px; padding:35px 28px;
    max-width:480px; width:100%;
    box-shadow:0 0 60px rgba(224,27,36,.15),0 0 100px rgba(27,110,224,.12),inset 0 0 40px rgba(0,0,0,.6);
    text-align:center; animation:fadeIn .6s ease; position:relative; overflow:hidden;
  }
  .card::before {
    content:""; position:absolute; inset:-2px; border-radius:24px;
    background:linear-gradient(120deg,transparent,rgba(224,27,36,.5),rgba(27,110,224,.5),transparent);
    background-size:300% 300%; animation:bordeAnimado 6s linear infinite; z-index:-1; opacity:.6;
  }
  @keyframes bordeAnimado { 0%{background-position:0% 50%;} 100%{background-position:300% 50%;} }
  @keyframes fadeIn { from{opacity:0; transform:translateY(15px);} to{opacity:1; transform:translateY(0);} }
  h1 {
    font-size:1.8rem; background:linear-gradient(90deg,#e01b24,#f7e08a,#1b6ee0,#e01b24);
    background-size:300% auto; -webkit-background-clip:text; background-clip:text; color:transparent;
    margin-bottom:12px; animation:textoBrillo 5s linear infinite;
  }
  h2 { font-size:1.2rem; color:#f0f0f0; margin-bottom:14px; }
  p { font-size:1rem; line-height:1.6; color:#d5d5d5; margin-bottom:18px; }

  .escorpion-portada {
    width:100px; height:100px; margin:0 auto 10px;
    filter: drop-shadow(0 0 20px rgba(224,27,36,.7)) drop-shadow(0 0 35px rgba(27,110,224,.3));
    animation: latidoEscorpion 2.5s ease-in-out infinite;
  }

  /* ====== CAJITA DE PREGUNTA — ESTILO MISTERIOSO ESCORPIO ====== */
  .cajita {
    background: linear-gradient(160deg, rgba(18,10,12,.98), rgba(8,10,18,.98));
    border: 1px solid rgba(224,27,36,.5);
    border-radius: 16px;
    padding: 24px 18px;
    margin-top: 10px;
    animation: abrirCajita .6s ease;
    box-shadow:
      inset 0 0 40px rgba(224,27,36,.08),
      inset 0 0 60px rgba(27,110,224,.06),
      0 0 30px rgba(224,27,36,.2);
    position: relative;
    overflow: hidden;
  }
  .cajita::before {
    content:"🦂";
    position:absolute;
    top:-12px; right:10px;
    font-size:1.4rem;
    opacity:.35;
    animation: latidoEscorpion 3s infinite;
  }
  .cajita::after {
    content:"";
    position:absolute;
    inset:0;
    background: radial-gradient(circle at 50% 0%, rgba(224,27,36,.08), transparent 60%);
    pointer-events:none;
  }
  @keyframes abrirCajita { from{transform:scale(.88); opacity:0;} to{transform:scale(1); opacity:1;} }
  .cajita .icono { font-size:1.8rem; display:block; margin-bottom:8px; filter: drop-shadow(0 0 10px rgba(224,27,36,.6)); }

  .progress {
    font-size:.72rem; color:#e01b24; margin-bottom:14px; letter-spacing:3px;
    text-transform: uppercase; font-weight:700;
    text-shadow: 0 0 10px rgba(224,27,36,.6);
  }
  .timer { font-size:.85rem; color:#f7e08a; margin-bottom:12px; font-weight:700; letter-spacing:1px; }
  .timer.urgente { color:#e01b24; animation:pulsoTimer .5s infinite; text-shadow:0 0 15px rgba(224,27,36,.8); }
  @keyframes pulsoTimer { 0%,100%{transform:scale(1);} 50%{transform:scale(1.1);} }

  .cajita h2 {
    font-size:1.15rem; color:#fff; margin-bottom:16px;
    text-shadow: 0 0 20px rgba(224,27,36,.4);
    line-height:1.4;
  }

  .btn {
    background:linear-gradient(90deg,#e01b24,#1b6ee0); background-size:200% auto;
    color:#fff; border:none; padding:14px 30px; border-radius:50px;
    font-size:1rem; font-weight:700; cursor:pointer;
    transition:transform .2s, box-shadow .2s, background-position .4s; margin:8px 4px;
    box-shadow:0 4px 20px rgba(224,27,36,.3);
  }
  .btn:hover { transform:translateY(-2px) scale(1.03); background-position:right center; box-shadow:0 6px 30px rgba(27,110,224,.5); }

  .btn-option {
    display:block; width:100%;
    background: rgba(20,15,20,.95);
    color:#f5f5f5;
    border: 1px solid rgba(224,27,36,.35);
    padding:14px 18px; border-radius:12px; margin:9px 0;
    font-size:.97rem; cursor:pointer; transition:all .25s; text-align:left;
    position:relative; overflow:hidden;
  }
  .btn-option::before {
    content:""; position:absolute; left:0; top:0; bottom:0; width:0;
    background:linear-gradient(90deg,rgba(224,27,36,.35),rgba(27,110,224,.35));
    transition:width .3s; z-index:0;
  }
  .btn-option:hover::before { width:100%; }
  .btn-option:hover { border-color:#e01b24; transform:translateX(5px); box-shadow:0 0 20px rgba(224,27,36,.4); }
  .btn-option span { position:relative; z-index:1; }
  .btn-option.correct { background:rgba(30,58,30,.95); border-color:#4caf50; box-shadow:0 0 25px rgba(76,175,80,.5); }
  .btn-option.wrong { background:rgba(58,30,30,.95); border-color:#e74c3c; box-shadow:0 0 25px rgba(231,76,60,.5); }
  .btn-option:disabled { cursor:default; }
  .btn-option:disabled:hover { transform:none; box-shadow:none; }
  .btn-option:disabled:hover::before { width:0; }

  .feedback { font-size:.98rem; margin-top:14px; min-height:24px; font-weight:600; line-height:1.5; }
  .feedback.ok { color:#4caf50; text-shadow:0 0 10px rgba(76,175,80,.5); }
  .feedback.no { color:#e74c3c; text-shadow:0 0 10px rgba(231,76,60,.5); }
  .feedback.broma { color:#f7e08a; text-shadow:0 0 10px rgba(247,224,138,.5); }

  .btn-continuar {
    display:inline-block; margin-top:18px;
    background:linear-gradient(90deg,#e01b24,#1b6ee0); background-size:200% auto;
    color:#fff; border:none; padding:12px 26px; border-radius:50px;
    font-size:.95rem; font-weight:700; cursor:pointer;
    transition:transform .2s, box-shadow .2s, background-position .4s;
    box-shadow:0 4px 20px rgba(224,27,36,.3); animation:fadeIn .4s ease;
  }
  .btn-continuar:hover { transform:translateY(-2px) scale(1.03); background-position:right center; box-shadow:0 6px 30px rgba(27,110,224,.5); }

  /* ====== TARJETA FINAL ====== */
  .tarjeta {
    background:linear-gradient(160deg,rgba(25,15,18,.97),rgba(10,12,20,.97));
    border:1px solid rgba(224,27,36,.6); border-radius:18px; padding:28px 22px; margin-top:12px;
    position:relative;
    box-shadow:0 0 50px rgba(224,27,36,.2),0 0 80px rgba(27,110,224,.15);
    animation:abrirCajita .8s ease;
  }
  .tarjeta::before {
    content:"🦂"; position:absolute; top:-18px; left:50%; transform:translateX(-50%);
    font-size:1.8rem; background:#050505; padding:0 10px;
  }
  .tarjeta h2 {
    font-size:1.3rem; margin-bottom:12px;
    background:linear-gradient(90deg,#e01b24,#f7e08a,#1b6ee0); background-size:200% auto;
    -webkit-background-clip:text; background-clip:text; color:transparent;
    animation:textoBrillo 4s linear infinite;
  }
  .tarjeta p { font-size:.95rem; color:#e8e2cf; }
  .verse {
    font-style:italic; color:#f7e08a; font-size:.88rem;
    border-left:3px solid #e01b24; padding-left:12px;
    text-align:left; margin:16px 0; line-height:1.5;
  }
  .firma {
    font-weight:700; margin-top:10px;
    background:linear-gradient(90deg,#e01b24,#1b6ee0);
    -webkit-background-clip:text; background-clip:text; color:transparent;
  }
  .sparkle { font-size:2.2rem; margin-bottom:8px; display:block; }
  .shake { animation:shake .4s; }
  .emoji-rain { position:fixed; font-size:1.6rem; pointer-events:none; animation:fall 1.8s linear forwards; z-index:999; }
  @keyframes fall { from{transform:translateY(-30px) rotate(0); opacity:1;} to{transform:translateY(100vh) rotate(360deg); opacity:0;} }
</style>
</head>
<body>

<div class="fondo-animado">
  <div class="aurora roja"></div>
  <div class="aurora azul"></div>
  <div class="aurora morada"></div>
</div>
<div class="particulas" id="particulas"></div>

<!-- PANTALLA DE CONTRASEÑA -->
<div class="pantalla-clave" id="pantallaClave">
  <svg class="escorpion-svg" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
    <ellipse cx="50" cy="55" rx="22" ry="14" fill="#e01b24" opacity="0.95"/>
    <ellipse cx="50" cy="45" rx="14" ry="10" fill="#e01b24" opacity="0.95"/>
    <ellipse cx="50" cy="38" rx="8" ry="6" fill="#e01b24" opacity="0.95"/>
    <path d="M50 32 Q65 20 75 28 Q82 35 78 45" stroke="#e01b24" stroke-width="4" fill="none" stroke-linecap="round"/>
    <circle cx="78" cy="47" r="4" fill="#e01b24"/>
    <path d="M40 40 L30 30 L25 35" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
    <path d="M40 50 L28 50 L22 56" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
    <path d="M40 60 L30 70 L25 65" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
    <path d="M60 40 L70 30 L75 35" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
    <path d="M60 50 L72 50 L78 56" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
    <path d="M60 60 L70 70 L75 65" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
  </svg>
  <div class="titulo-clave">Acceso Privado</div>
  <div class="sub-clave">Solo para Yeferson 🦂</div>
  <input type="password" class="input-clave" id="inputClave" placeholder="••••••••" maxlength="20" autocomplete="off">
  <button class="btn-clave" onclick="verificarClave()">Entrar</button>
  <div class="msg-error" id="msgError"></div>
</div>

<!-- CONTENIDO DEL JUEGO -->
<div class="card" id="app" style="display:none;"></div>

<script>
/* ============================================================
   CONTRASEÑA
   ============================================================ */
const CLAVE_SECRETA = "yefer123";

/* ===== PARTÍCULAS ===== */
(function crearParticulas() {
  const cont = document.getElementById('particulas');
  const colores = ['#e01b24','#1b6ee0','#f7e08a','#ffffff','#7a1be0'];
  for (let i = 0; i < 35; i++) {
    const p = document.createElement('div');
    p.className = 'particula';
    p.style.left = Math.random() * 100 + 'vw';
    p.style.background = colores[Math.floor(Math.random() * colores.length)];
    p.style.animationDuration = (8 + Math.random() * 12) + 's';
    p.style.animationDelay = (Math.random() * 15) + 's';
    p.style.width = p.style.height = (2 + Math.random() * 4) + 'px';
    p.style.boxShadow = `0 0 8px ${p.style.background}`;
    cont.appendChild(p);
  }
})();

const state = { current: 0, aciertos: 0, timerId: null, tiempoRestante: 0 };

/* ===== VERIFICAR CLAVE ===== */
function verificarClave() {
  const input = document.getElementById('inputClave');
  const msg = document.getElementById('msgError');
  const valor = input.value.trim().toLowerCase();

  if (valor === CLAVE_SECRETA.toLowerCase()) {
    document.getElementById('pantallaClave').style.display = 'none';
    document.getElementById('app').style.display = 'block';
    portada();
  } else {
    input.classList.add('error');
    msg.textContent = "Clave incorrecta. Inténtalo de nuevo 🦂";
    setTimeout(() => input.classList.remove('error'), 500);
    input.value = '';
    input.focus();
  }
}

document.getElementById('inputClave').addEventListener('keypress', (e) => {
  if (e.key === 'Enter') verificarClave();
});

/* ============================================================
   AUDIO — SOLO EFECTOS Y MELODÍA FINAL
   ============================================================ */
let audioCtx = null;
let masterGain = null;
let nodosActivos = [];
let loopTimeout = null;

function initAudio() {
  if (!audioCtx) {
    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    masterGain = audioCtx.createGain();
    masterGain.gain.value = 0.6;
    masterGain.connect(audioCtx.destination);
  }
  if (audioCtx.state === 'suspended') audioCtx.resume();
}

function registrarNodo(n) { nodosActivos.push(n); return n; }

function nota(freq, dur, cuando, tipo='triangle', vol=0.15) {
  const osc = audioCtx.createOscillator();
  const g = audioCtx.createGain();
  osc.type = tipo;
  osc.frequency.value = freq;
  g.gain.setValueAtTime(0, cuando);
  g.gain.linearRampToValueAtTime(vol, cuando + 0.02);
  g.gain.exponentialRampToValueAtTime(0.001, cuando + dur - 0.03);
  osc.connect(g); g.connect(masterGain);
  osc.start(cuando); osc.stop(cuando + dur);
  registrarNodo(osc);
  osc.onended = () => { const i = nodosActivos.indexOf(osc); if (i > -1) nodosActivos.splice(i, 1); };
}

/* ---- SONIDO DE ACIERTO (arpegio alegre) ---- */
function sonidoAcierto() {
  initAudio();
  const t = audioCtx.currentTime;
  [523.25, 659.25, 783.99, 1046.50].forEach((f, i) => {
    nota(f, 0.2, t + i * 0.08, 'triangle', 0.18);
  });
}

/* ---- SONIDO DE FALLO (descenso grave) ---- */
function sonidoFallo() {
  initAudio();
  const t = audioCtx.currentTime;
  nota(300, 0.25, t, 'sawtooth', 0.12);
  nota(200, 0.3, t + 0.15, 'sawtooth', 0.12);
  nota(120, 0.4, t + 0.35, 'sawtooth', 0.12);
}

/* ---- SONIDO DE BROMA (travieso) ---- */
function sonidoBroma() {
  initAudio();
  const t = audioCtx.currentTime;
  nota(800, 0.1, t, 'square', 0.1);
  nota(600, 0.1, t + 0.1, 'square', 0.1);
  nota(900, 0.15, t + 0.2, 'square', 0.1);
}

/* ---- MELODÍA DE CUMPLEAÑOS (solo al final) ---- */
const N = {
  C4:261.63,D4:293.66,E4:329.63,F4:349.23,G4:392.00,A4:440.00,B4:493.88,
  C5:523.25,D5:587.33,E5:659.25,F5:698.46,G5:783.99
};

function melodiaCumple() {
  initAudio();
  const tempo = 0.42;
  const mel = [
    [N.G4,.75],[N.G4,.25],[N.A4,1],[N.G4,1],[N.C5,1],[N.B4,2],
    [N.G4,.75],[N.G4,.25],[N.A4,1],[N.G4,1],[N.D5,1],[N.C5,2],
    [N.G4,.75],[N.G4,.25],[N.G5,1],[N.E5,1],[N.C5,1],[N.B4,1],[N.A4,2],
    [N.F5,.75],[N.F5,.25],[N.E5,1],[N.C5,1],[N.D5,1],[N.C5,2]
  ];
  let t = audioCtx.currentTime + 0.1;
  mel.forEach(([freq, beats]) => { nota(freq, beats * tempo, t, 'triangle', 0.14); t += beats * tempo; });
  const dur = (t - audioCtx.currentTime) * 1000;
  loopTimeout = setTimeout(() => { melodiaCumple(); }, dur + 2000);
}

function detenerMelodia() {
  clearTimeout(loopTimeout);
  loopTimeout = null;
}

function render(html) {
  const app = document.getElementById('app');
  app.innerHTML = html;
  app.style.animation = 'none'; void app.offsetWidth;
  app.style.animation = 'fadeIn 0.6s ease';
}

function lluviaEmojis(emojis) {
  for (let i = 0; i < 12; i++) {
    const el = document.createElement('div');
    el.className = 'emoji-rain';
    el.textContent = emojis[Math.floor(Math.random() * emojis.length)];
    el.style.left = Math.random() * 100 + 'vw';
    el.style.animationDelay = Math.random() * 0.6 + 's';
    document.body.appendChild(el);
    setTimeout(() => el.remove(), 2500);
  }
}

/* ===== PREGUNTAS ===== */
const preguntas = [
  { pregunta:"¿Qué prefiere Yeferson tomar?",
    opciones:["Café bien cargado","Té ☕","Chocolate caliente","Bebida energética"],
    correcta:1, ok:"¡Exacto! Té. Ahora lo tengo bien presente 😌",
    no:"¿En serio? Pensé que te gustaba el té ☕", broma:true, icono:"☕", tiempo:20 },
  { pregunta:"¿Cuál es su color favorito?",
    opciones:["El azul cielo","El negro 🖤","El rojo","El verde"],
    correcta:1, ok:"¡Correcto! El negro, como su estilo 🖤",
    no:"¿En serio? Pensé que te gustaba el negro 🖤", broma:false, icono:"🖤", tiempo:18 },
  { pregunta:"¿Qué prefiere Yeferson: montaña o playa?",
    opciones:["Playa con sol","Montaña 🏔️","Las dos por igual","Ni una ni otra"],
    correcta:1, ok:"¡Bien! La montaña, tranquilo y en su espacio 🏔️",
    no:"¿En serio? Pensé que te gustaba la montaña 🏔️", broma:true, icono:"🏔️", tiempo:18 },
  { pregunta:"¿Qué plan le gana a Yeferson?",
    opciones:["Fiesta hasta tarde","Quedarse en casa, tranquilo 🏠","Centro comercial lleno","Salir a caminar"],
    correcta:1, ok:"¡Exacto! Quedarse en casa, en calma 🏠",
    no:"¿En serio? Pensé que te gustaba quedarte en casa 🏠", broma:false, icono:"🏠", tiempo:18 },
  { pregunta:"Si te digo 'todo lo puedo en Cristo que me fortalece', ¿de dónde es?",
    opciones:["Filipenses 4:13","Un anuncio de TV","Una canción de moda","Salmos 23"],
    correcta:0, ok:"¡Correcto! Filipenses 4:13 🙌 Se nota que sabes.",
    no:"¿En serio? Pensé que sabías que es Filipenses 4:13 📖", broma:true, icono:"📖", tiempo:20 },
  { pregunta:"¿Qué es lo que más admira de una persona?",
    opciones:["Que hable mucho","Que sea sincera y calmada","Que tenga dinero","Que sea famosa"],
    correcta:1, ok:"¡Exacto! La sinceridad y la calma, como tú 😌",
    no:"¿En serio? Pensé que valorabas la sinceridad y la calma", broma:false, icono:"🤝", tiempo:18 },
  { pregunta:"¿Qué hace Yeferson cuando hay problemas?",
    opciones:["Grita y se altera","Los evita y observa con calma","Se ríe","Se va corriendo"],
    correcta:1, ok:"¡Correcto! Observa, calla y aprende. Muy tú 🧠",
    no:"¿En serio? Pensé que eras de observar con calma", broma:true, icono:"🧠", tiempo:20 }
];

const bromasFalsas = ["Ay, perdón… perdiste 😈","No, mentira 😂 ¡Sigue!","Uy, casi. Pero no.","Te la creíste, ¿verdad? 😏"];
const elogios = ["¡Uy, ese! 🔥","Vas bien… sospechosamente bien 👀","Eso, eso. Se nota que pones atención 😏","¡Correcto! ¿Tienes ayuda de alguien? 😂"];

const svgEscorpion = `
<svg class="escorpion-portada" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <ellipse cx="50" cy="55" rx="22" ry="14" fill="#e01b24" opacity="0.95"/>
  <ellipse cx="50" cy="45" rx="14" ry="10" fill="#e01b24" opacity="0.95"/>
  <ellipse cx="50" cy="38" rx="8" ry="6" fill="#e01b24" opacity="0.95"/>
  <path d="M50 32 Q65 20 75 28 Q82 35 78 45" stroke="#e01b24" stroke-width="4" fill="none" stroke-linecap="round"/>
  <circle cx="78" cy="47" r="4" fill="#e01b24"/>
  <path d="M40 40 L30 30 L25 35" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
  <path d="M40 50 L28 50 L22 56" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
  <path d="M40 60 L30 70 L25 65" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
  <path d="M60 40 L70 30 L75 35" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
  <path d="M60 50 L72 50 L78 56" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
  <path d="M60 60 L70 70 L75 65" stroke="#1b6ee0" stroke-width="3" fill="none" stroke-linecap="round"/>
</svg>`;

function limpiarTimer() {
  if (state.timerId) { clearInterval(state.timerId); state.timerId = null; }
}

// PORTADA
function portada() {
  limpiarTimer();
  detenerMelodia();
  render(`
    ${svgEscorpion}
    <h1>Feliz cumpleaños, Yeferson</h1>
    <p>Hice esto yo misma para ti. Un jueguito de unos minutos… con misterio, con trampas y con cariño de verdad. 🦂</p>
    <p style="font-size:0.82rem;color:#8a8a9a;letter-spacing:1px;">SOLO TÚ PUEDES ESTAR AQUÍ</p>
    <div class="caja" id="caja" onclick="abrirCaja()">🎁</div>
    <p style="font-size:0.85rem;color:#8a8a9a;">Pulsa la caja para abrir tu regalo</p>
  `);
}

function abrirCaja() {
  const caja = document.getElementById('caja');
  caja.classList.add('abriendo');
  lluviaEmojis(['🎉','✨','🎊','🖤','💛','🔴','🔵','🦂']);
  initAudio();
  setTimeout(() => { state.current = 0; state.aciertos = 0; mostrarPregunta(); }, 850);
}

// PREGUNTAS
function mostrarPregunta() {
  limpiarTimer();
  if (state.current >= preguntas.length) { tarjetaFinal(); return; }
  const p = preguntas[state.current];
  state.tiempoRestante = p.tiempo;
  const opcionesHTML = p.opciones.map((op,i) =>
    `<button class="btn-option" onclick="responder(${i})"><span>${op}</span></button>`).join('');
  render(`
    <div class="cajita">
      <span class="icono">${p.icono}</span>
      <div class="progress">PRUEBA ${state.current+1} DE ${preguntas.length}</div>
      <div class="timer" id="timer">⏱️ ${state.tiempoRestante}s</div>
      <h2>${p.pregunta}</h2>
      ${opcionesHTML}
      <div class="feedback" id="feedback"></div>
      <div id="zonaContinuar"></div>
    </div>
  `);
  iniciarTimer(p.tiempo);
}

function iniciarTimer(segundos) {
  const el = document.getElementById('timer');
  state.timerId = setInterval(() => {
    state.tiempoRestante--;
    if (!el) return;
    el.textContent = `⏱️ ${state.tiempoRestante}s`;
    if (state.tiempoRestante <= 5) el.classList.add('urgente');
    if (state.tiempoRestante <= 0) {
      clearInterval(state.timerId); state.timerId = null;
      tiempoAgotado();
    }
  }, 1000);
}

function tiempoAgotado() {
  const p = preguntas[state.current];
  const fb = document.getElementById('feedback');
  const botones = document.querySelectorAll('.btn-option');
  botones.forEach(b => { b.disabled = true; });
  botones[p.correcta].classList.add('correct');
  fb.textContent = "¡Se acabó el tiempo! ⏰ La respuesta era: " + p.opciones[p.correcta];
  fb.className = 'feedback no';
  sonidoFallo();
  mostrarContinuar();
}

function mostrarContinuar() {
  setTimeout(() => {
    const zona = document.getElementById('zonaContinuar');
    if (zona) zona.innerHTML = `<button class="btn-continuar" onclick="siguiente()">Continuar ➜</button>`;
  }, 1000);
}

function responder(i) {
  limpiarTimer();
  const p = preguntas[state.current];
  const fb = document.getElementById('feedback');
  const botones = document.querySelectorAll('.btn-option');
  botones.forEach(b => b.disabled = true);

  if (i === p.correcta) {
    botones[i].classList.add('correct');
    if (p.broma && Math.random() < 0.55) {
      // Broma: primero "pierde" y luego "gana"
      fb.textContent = bromasFalsas[Math.floor(Math.random()*bromasFalsas.length)];
      fb.className = 'feedback broma';
      sonidoBroma();
      document.getElementById('app').classList.add('shake');
      setTimeout(() => {
        document.getElementById('app').classList.remove('shake');
        fb.textContent = "No, mentira 😂 ¡ERA CORRECTO! " + elogios[Math.floor(Math.random()*elogios.length)];
        fb.className = 'feedback ok';
        state.aciertos++;
        sonidoAcierto();
        lluviaEmojis(['🎉','✨','🖤','🔥','🔵']);
      }, 1200);
    } else {
      fb.textContent = p.ok + " " + elogios[Math.floor(Math.random()*elogios.length)];
      fb.className = 'feedback ok';
      state.aciertos++;
      sonidoAcierto();
      lluviaEmojis(['🎉','✨','🖤','🔴']);
    }
  } else {
    botones[i].classList.add('wrong');
    botones[p.correcta].classList.add('correct');
    sonidoFallo();
    if (Math.random() < 0.4) {
      fb.textContent = "¡Correcto! 🎉 … mentira 😈 Perdiste.";
      fb.className = 'feedback broma';
      setTimeout(() => { fb.textContent = p.no; fb.className = 'feedback no'; }, 1300);
    } else {
      fb.textContent = p.no; fb.className = 'feedback no';
    }
  }
  mostrarContinuar();
}

function siguiente() {
  limpiarTimer();
  state.current++;
  mostrarPregunta();
}

// TARJETA FINAL
function tarjetaFinal() {
  limpiarTimer();
  const tramposo = state.aciertos >= 5;
  // Melodía de cumpleaños al final
  melodiaCumple();
  render(`
    <div class="tarjeta">
      <h2>🎂 Feliz cumpleaños, Yeferson</h2>
      <p>No tengo fotos ni videos que regalarte, así que te regalo esto: un ratito hecho por mí, con mi cariño especial (y con trampas, ya viste 😏).</p>
      <div class="verse">"Jehová te bendiga y te guarde; Jehová haga resplandecer su rostro sobre ti y tenga de ti misericordia." — Números 6:24-25</div>
      <p>Eres una persona que me cae muy bien y a la que le tengo mucha confianza. Admiro tu calma, tu paciencia y esa forma tuya de observar y callar, de aprender de la vida y seguir con madurez. Quería desearte un año lleno de paz, propósito y cosas buenas. Que Dios te sorprenda.</p>
      <p style="font-size:0.9rem; color:#f7e08a;">Acertaste <strong>${state.aciertos} de ${preguntas.length}</strong>. ${tramposo ? 'Demasiado bien… ¿me hackeaste? 😂' : 'Tendrás que seguir descubriéndome 😌'}</p>
      <div class="verse">"Todo lo puedo en Cristo que me fortalece." — Filipenses 4:13</div>
      <p>Gracias por ser una persona tan especial para mí. Que este año te traiga cosas buenas, y que sigas siendo esa persona calmada, sincera y curiosa que eres. 🖤</p>
      <p class="firma">— Con cariño 💛</p>
    </div>
    <button class="btn" onclick="detenerMelodia(); portada();" style="margin-top:18px;">Volver a abrir la caja 🔁</button>
  `);
  lluviaEmojis(['🎉','🎂','✨','🖤','💛','🔴','🔵','🦂']);
}
</script>
</body>
</html>
