# CUENTA REGRESIVA SAN VALENTIN

<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Cuenta Regresiva San Valentín</title>

<style>
:root{
  --bloodDark:#2b0000;
  --bloodMain:#7a0000;
  --bloodGlow:#b30000;
  --softWhite:#fff5f5;
}

*{box-sizing:border-box}

body{
  margin:0;
  height:100vh;
  display:flex;
  align-items:center;
  justify-content:center;
  font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
  background: radial-gradient(circle at 30% 20%, var(--bloodMain), var(--bloodDark));
  color:white;
}

.container{
  text-align:center;
  background: rgba(255,255,255,0.06);
  padding:40px 30px;
  border-radius:28px;
  backdrop-filter: blur(14px);
  box-shadow: 0 30px 80px rgba(0,0,0,.55);
  width:min(92vw,520px);
}

.title{
  font-size:30px;
  font-weight:900;
  margin-bottom:8px;
  color:#ff4d6d;
  text-shadow:0 0 18px rgba(255,77,109,.5);
}

.subtitle{
  font-size:14px;
  opacity:.85;
  margin-bottom:28px;
}

.grid{
  display:grid;
  grid-template-columns: repeat(4,1fr);
  gap:14px;
}

.box{
  background: rgba(255,255,255,0.1);
  padding:18px 10px;
  border-radius:18px;
  box-shadow: inset 0 0 15px rgba(255,255,255,0.05);
}

.number{
  font-size:28px;
  font-weight:900;
}

.label{
  font-size:12px;
  margin-top:6px;
  opacity:.8;
}

.footer{
  margin-top:24px;
  font-size:13px;
  opacity:.75;
}
</style>
</head>

<body>

<div class="container">
  <div class="title">14 de Febrero ❤️</div>
  <div class="subtitle">Cuenta regresiva para el Día de San Valentín</div>

  <div class="grid">
    <div class="box">
      <div class="number" id="days">0</div>
      <div class="label">Días</div>
    </div>
    <div class="box">
      <div class="number" id="hours">00</div>
      <div class="label">Horas</div>
    </div>
    <div class="box">
      <div class="number" id="minutes">00</div>
      <div class="label">Minutos</div>
    </div>
    <div class="box">
      <div class="number" id="seconds">00</div>
      <div class="label">Segundos</div>
    </div>
  </div>

  <div class="footer" id="message"></div>
</div>

<script>
// 🎯 14 de febrero 2026 (hora local del navegador)
const targetDate = new Date(2026, 1, 14, 0, 0, 0);

function updateCountdown(){
  const now = new Date();
  const diff = targetDate - now;

  if(diff <= 0){
    document.getElementById("days").textContent = "0";
    document.getElementById("hours").textContent = "00";
    document.getElementById("minutes").textContent = "00";
    document.getElementById("seconds").textContent = "00";
    document.getElementById("message").textContent = "¡Ya es 14 de febrero! 💖";
    return;
  }

  const totalSeconds = Math.floor(diff / 1000);

  const days = Math.floor(totalSeconds / 86400);
  const hours = Math.floor((totalSeconds % 86400) / 3600);
  const minutes = Math.floor((totalSeconds % 3600) / 60);
  const seconds = totalSeconds % 60;

  document.getElementById("days").textContent = days;
  document.getElementById("hours").textContent = hours.toString().padStart(2,"0");
  document.getElementById("minutes").textContent = minutes.toString().padStart(2,"0");
  document.getElementById("seconds").textContent = seconds.toString().padStart(2,"0");

  document.getElementById("message").textContent = "El amor se acerca... ❤️";
}

updateCountdown();
setInterval(updateCountdown, 1000);
</script>

</body>
</html>


