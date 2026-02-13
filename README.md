# CUENTA REGRESIVA SAN VALENTIN
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>¿Melanny quieres ser mi San Valentín?</title>

<style>
:root{
  --bloodDark:#3a0000;
  --bloodMain:#7a0000;
  --bloodGlow:#b30000;
  --card:#ffffffee;
  --greenECG:#00ff9c;
}

*{box-sizing:border-box}

body{
  margin:0;
  min-height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
  background: radial-gradient(circle at 30% 20%, #7a0000 0%, #3a0000 60%);
  overflow:hidden;
  color:#111;
}

/* Canvas ECG */
#ecgCanvas{
  position:fixed;
  inset:0;
  width:100%;
  height:100%;
  z-index:0;
  pointer-events:none;
  mix-blend-mode:screen;
  opacity:.6;
}

.card{
  width:min(92vw, 560px);
  background:var(--card);
  border-radius:24px;
  padding:28px 22px;
  box-shadow: 0 25px 70px rgba(0,0,0,.5);
  text-align:center;
  position:relative;
  z-index:2;
}

.titulo-rojo{
  color:#b30000;
  font-weight:900;
  text-shadow:0 0 12px rgba(179,0,0,.4);
}

h1{
  margin:10px 0 14px;
  font-size: clamp(26px, 4vw, 34px);
  color:#7a0000;
}

.names{
  font-weight:700;
  color:#3a0000;
}

button{
  border:none;
  border-radius:14px;
  padding:14px 18px;
  font-size:16px;
  font-weight:700;
  cursor:pointer;
  transition:.2s;
}

.yes{
  background: linear-gradient(135deg, #16a34a, #0f7a35);
  color:white;
}

.no{
  background: linear-gradient(135deg, #ef4444, #b91c1c);
  color:white;
  position:relative;
}

.countdown{
  margin:14px 0;
  padding:10px;
  border-radius:16px;
  background:#fff3f3;
  border:1px solid #f5c2c2;
}

.cd-grid{
  display:grid;
  grid-template-columns: repeat(4,1fr);
  gap:8px;
}

.cd-box{
  background:white;
  padding:8px;
  border-radius:12px;
  font-weight:800;
}

.footer{
  margin-top:12px;
  font-size:12px;
  color:#5c0000;
}

/* Corazones reales SVG */
.heart{
  position:fixed;
  bottom:-40px;
  width:24px;
  height:24px;
  pointer-events:none;
  z-index:1;
  animation: floatUp linear forwards;
}

@keyframes floatUp{
  from { transform: translateY(0) scale(1); opacity:1; }
  to   { transform: translateY(-110vh) scale(1.2); opacity:0; }
}

.modal{
  position:fixed; inset:0;
  display:none;
  align-items:center;
  justify-content:center;
  background:rgba(0,0,0,.6);
  z-index:3;
}

.modal.open{display:flex;}

.modal-box{
  background:white;
  padding:22px;
  border-radius:20px;
  text-align:center;
  width:min(90vw,450px);
}
</style>
</head>

<body>

<canvas id="ecgCanvas"></canvas>

<div class="card">

  <div class="titulo-rojo">
    Feliz San Valentín, amor ❤️
  </div>

  <div class="countdown">
    <div><strong>Cuenta regresiva 💘</strong></div>
    <div class="cd-grid">
      <div class="cd-box"><span id="cdDays">0</span><br>Días</div>
      <div class="cd-box"><span id="cdHours">00</span><br>Horas</div>
      <div class="cd-box"><span id="cdMins">00</span><br>Min</div>
      <div class="cd-box"><span id="cdSecs">00</span><br>Seg</div>
    </div>
  </div>

  <h1>¿Quieres ser mi San Valentín? 💘</h1>

  <p>
    <span class="names">Chris</span> ➜ <span class="names">Mi muñeca hermosa</span><br>
    Prometo el mejor 14 de febrero de tu vida.
  </p>

  <button class="yes" id="yesBtn">Sí 💚</button>
  <button class="no" id="noBtn">Obvio sí 🙃</button>

  <div class="footer">
    Ya eres mía 😌
  </div>

</div>

<div class="modal" id="modal">
  <div class="modal-box">
    <h2>🥹💖 ¡Sabía que dirías que sí!</h2>
    <p>Prepárate para un día inolvidable.</p>
    <button onclick="closeModal()">Cerrar</button>
  </div>
</div>

<script>
// Cuenta regresiva 14 febrero 2026
const target = new Date(2026,1,14,0,0,0);

function updateCountdown(){
  const now = new Date();
  const diff = target - now;

  if(diff<=0) return;

  const s = Math.floor(diff/1000);
  const d = Math.floor(s/86400);
  const h = Math.floor((s%86400)/3600);
  const m = Math.floor((s%3600)/60);
  const sec = s%60;

  cdDays.textContent=d;
  cdHours.textContent=h.toString().padStart(2,"0");
  cdMins.textContent=m.toString().padStart(2,"0");
  cdSecs.textContent=sec.toString().padStart(2,"0");
}
setInterval(updateCountdown,1000);
updateCountdown();

// Corazones SVG reales
function spawnHeart(){
  const heart=document.createElement("div");
  heart.className="heart";
  heart.style.left=Math.random()*100+"vw";
  heart.style.animationDuration=4+Math.random()*3+"s";
  heart.innerHTML=`
    <svg viewBox="0 0 24 24" width="100%" height="100%">
      <path fill="#ff4d6d" d="M12 21s-7-4.5-9.5-8.5C.5 9 2 6 5.5 5.5c1.7-.2 3.3.5 4.5 1.8 1.2-1.3 2.8-2 4.5-1.8C18 6 19.5 9 17.5 12.5 15 16.5 12 21 12 21z"/>
    </svg>`;
  document.body.appendChild(heart);
  setTimeout(()=>heart.remove(),6000);
}
setInterval(spawnHeart,400);

// ECG animado
const canvas=document.getElementById("ecgCanvas");
const ctx=canvas.getContext("2d");

function resize(){
  canvas.width=window.innerWidth;
  canvas.height=window.innerHeight;
}
resize();
window.addEventListener("resize",resize);

let offset=0;
function drawECG(){
  ctx.fillStyle="rgba(0,0,0,0.08)";
  ctx.fillRect(0,0,canvas.width,canvas.height);

  ctx.strokeStyle="rgba(0,255,156,.8)";
  ctx.lineWidth=2;
  ctx.beginPath();

  for(let x=0;x<canvas.width;x++){
    const y=canvas.height*0.6 +
      Math.sin((x+offset)*0.02)*5 +
      (Math.sin((x+offset)*0.15)>0.95? -60:0);

    if(x===0) ctx.moveTo(x,y);
    else ctx.lineTo(x,y);
  }
  ctx.stroke();
  offset+=4;
  requestAnimationFrame(drawECG);
}
drawECG();

// Modal
yesBtn.onclick=()=>modal.classList.add("open");
function closeModal(){ modal.classList.remove("open"); }
</script>

</body>
</html>

