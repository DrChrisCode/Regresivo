# CUENTA REGRESIVA SAN VALENTIN
<!-- ⏳ Cuenta regresiva -->
<div class="countdown" id="countdown" aria-live="polite">
  <div class="cd-title">Falta para San Valentín 💘</div>
  <div class="cd-grid">
    <div class="cd-box"><div class="cd-num" id="cdDays">0</div><div class="cd-lbl">Días</div></div>
    <div class="cd-box"><div class="cd-num" id="cdHours">0</div><div class="cd-lbl">Horas</div></div>
    <div class="cd-box"><div class="cd-num" id="cdMins">0</div><div class="cd-lbl">Min</div></div>
    <div class="cd-box"><div class="cd-num" id="cdSecs">0</div><div class="cd-lbl">Seg</div></div>
  </div>
  <div class="cd-note" id="cdNote"></div>
</div>

<style>
  .countdown{
    margin: 14px auto 6px;
    padding: 12px 14px;
    border-radius: 18px;
    border: 1px solid #ffffff80;
    background: #ffffffb0;
    backdrop-filter: blur(8px);
    max-width: 520px;
  }
  .cd-title{
    font-weight: 800;
    font-size: 14px;
    margin-bottom: 10px;
    opacity: .9;
  }
  .cd-grid{
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    gap: 10px;
  }
  .cd-box{
    border-radius: 16px;
    padding: 10px 8px;
    background: #ffffffcc;
    border: 1px solid #ffffff80;
    box-shadow: 0 10px 22px rgba(0,0,0,.10);
  }
  .cd-num{
    font-size: 22px;
    font-weight: 900;
    line-height: 1;
  }
  .cd-lbl{
    margin-top: 6px;
    font-size: 12px;
    opacity: .75;
    font-weight: 700;
  }
  .cd-note{
    margin-top: 10px;
    font-size: 12px;
    opacity: .8;
  }
</style>

<script>
  // 🎯 Objetivo: 14 de febrero de 2026 (inicio del día, hora local del navegador)
  const target = new Date(2026, 1, 14, 0, 0, 0); // Mes 1 = Febrero

  const elDays  = document.getElementById("cdDays");
  const elHours = document.getElementById("cdHours");
  const elMins  = document.getElementById("cdMins");
  const elSecs  = document.getElementById("cdSecs");
  const elNote  = document.getElementById("cdNote");

  function pad2(n){ return String(n).padStart(2, "0"); }

  function updateCountdown(){
    const now = new Date();
    let diff = target - now; // ms

    if (diff <= 0){
      elDays.textContent  = "0";
      elHours.textContent = "00";
      elMins.textContent  = "00";
      elSecs.textContent  = "00";
      elNote.textContent = "¡Ya es 14 de febrero! 💖";
      return;
    }

    const totalSeconds = Math.floor(diff / 1000);
    const days = Math.floor(totalSeconds / (60*60*24));
    const hours = Math.floor((totalSeconds % (60*60*24)) / (60*60));
    const mins = Math.floor((totalSeconds % (60*60)) / 60);
    const secs = totalSeconds % 60;

    elDays.textContent  = String(days);
    elHours.textContent = pad2(hours);
    elMins.textContent  = pad2(mins);
    elSecs.textContent  = pad2(secs);

    // Mensajito opcional
    elNote.textContent = "Preparando el mejor día contigo 😌";
  }

  updateCountdown();
  setInterval(updateCountdown, 1000);
</script>
