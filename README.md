<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Will you marry me? 💍</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;700;800;900&display=swap" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.9.2/dist/confetti.browser.min.js"></script>
<style>
  * { box-sizing: border-box; }
 
  body {
    margin: 0;
    background-color: #FFE4E8;
    font-family: 'Nunito', sans-serif;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    background-image:
      radial-gradient(circle at 15% 85%, #ffb3c1 0%, transparent 40%),
      radial-gradient(circle at 85% 15%, #ff8fa3 0%, transparent 40%),
      radial-gradient(circle at 50% 50%, #fff0f3 0%, transparent 60%);
    position: relative;
  }
 
  .hearts-bg {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
    overflow: hidden;
  }
  .hearts-bg span {
    position: absolute;
    top: 110%;
    font-size: 20px;
    opacity: 0.75;
    animation: floatUp linear infinite;
  }
  @keyframes floatUp {
    0% { transform: translateY(0) rotate(0deg); opacity: 0; }
    10% { opacity: 0.8; }
    100% { transform: translateY(-115vh) rotate(360deg); opacity: 0; }
  }
 
  .container {
    position: relative;
    z-index: 2;
    background: #fffaf9;
    border-radius: 28px;
    padding: 40px 30px 34px;
    max-width: 440px;
    width: 90%;
    text-align: center;
    box-shadow: 0 20px 50px rgba(255, 111, 145, 0.3), 0 0 0 6px rgba(255,255,255,0.6) inset;
    border: 3px dashed #ff6f91;
    animation: cardPop 0.8s cubic-bezier(.26,1.4,.4,1) both;
  }
  @keyframes cardPop {
    0% { transform: scale(0.6) rotate(-6deg); opacity: 0; }
    100% { transform: scale(1) rotate(0deg); opacity: 1; }
  }
  .container.fading-out {
    opacity: 0;
    transform: scale(0.85);
    transition: opacity 0.5s ease, transform 0.5s ease;
    pointer-events: none;
  }
 
  h1 {
    font-size: 1.7rem;
    font-weight: 900;
    color: #ff6f91;
    margin: 6px 0 4px;
  }
  .sub {
    color: #a15c72;
    font-weight: 700;
    font-size: 0.95rem;
    margin-bottom: 14px;
  }
 
  .scene {
    position: relative;
    height: 160px;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    gap: 6px;
    margin: 6px auto 4px;
  }
  .bear {
    font-size: 62px;
    display: inline-block;
    filter: drop-shadow(0 6px 6px rgba(0,0,0,0.15));
  }
  .bear.groom { animation: bounceLeft 2.2s ease-in-out infinite; }
  .bear.bride { animation: bounceRight 2.2s ease-in-out infinite; animation-delay: 0.15s; }
  @keyframes bounceLeft {
    0%, 100% { transform: translateY(0) rotate(-4deg); }
    50% { transform: translateY(-10px) rotate(2deg); }
  }
  @keyframes bounceRight {
    0%, 100% { transform: translateY(0) rotate(4deg); }
    50% { transform: translateY(-10px) rotate(-2deg); }
  }
  .ring-emoji {
    position: absolute;
    top: 4px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 28px;
    animation: sparkle 1.6s ease-in-out infinite;
  }
  @keyframes sparkle {
    0%, 100% { transform: translateX(-50%) scale(1) rotate(0deg); }
    50% { transform: translateX(-50%) scale(1.25) rotate(15deg); }
  }
 
  .funny-line {
    font-size: 0.85rem;
    font-weight: 700;
    color: #c47a8f;
    margin: 4px 0 16px;
    min-height: 18px;
  }
 
  .buttons {
    display: flex;
    gap: 14px;
    justify-content: center;
    align-items: center;
    margin: 8px auto 0;
    position: relative;
    width: 100%;
    max-width: 360px;
    height: 78px;
    overflow: hidden;
  }
  button {
    font-family: 'Nunito', sans-serif;
    font-size: 1.05rem;
    font-weight: 800;
    padding: 12px 26px;
    border-radius: 999px;
    border: none;
    cursor: pointer;
    transition: transform 0.15s ease;
  }
  #yesBtn {
    background: linear-gradient(135deg, #ff6f91, #f5c451);
    color: white;
    box-shadow: 0 8px 18px rgba(255,111,145,0.5);
  }
  #yesBtn:hover { transform: scale(1.08); }
  #yesBtn.locked { opacity: 0.85; filter: saturate(0.7); }
  #yesBtn.shake { animation: shake 0.5s ease; }
  @keyframes shake {
    0%, 100% { transform: translateX(0) scale(1); }
    20% { transform: translateX(-8px) scale(1.03); }
    40% { transform: translateX(8px) scale(1.03); }
    60% { transform: translateX(-6px) scale(1.03); }
    80% { transform: translateX(6px) scale(1.03); }
  }
 
  #noBtn {
    transform: translateY(-45px);
    background: #fff;
    color: #ff6f91;
    border: 2px solid #ff6f91;
    position: absolute;
    left: 58%;
    top: 50%;
    transform: translate(-50%, -50%);
    z-index: 5;
    white-space: nowrap;
  }
 
  .yes-size-1 { font-size: 1.05rem; padding: 12px 26px; }
  .yes-size-2 { font-size: 1.25rem; padding: 15px 32px; }
  .yes-size-3 { font-size: 1.5rem; padding: 18px 40px; }
  .yes-size-4 { font-size: 1.85rem; padding: 22px 50px; }
  .yes-size-5 { font-size: 2rem; padding: 20px 34px; }
 
  .nudge-msg {
    font-size: 0.85rem;
    color: #ff6f91;
    font-weight: 800;
    margin-top: 12px;
    min-height: 18px;
    opacity: 0;
    transition: opacity 0.3s ease;
  }
  .nudge-msg.show { opacity: 1; }
 
  .tap-hint {
    font-size: 0.75rem;
    font-weight: 700;
    color: #c98da2;
    margin-top: 14px;
    opacity: 0.8;
  }
 
  /* ---------- YES PAGE (matches original structure) ---------- */
  .yes-container {
    display: none;
  }
  .yes-container.show {
    display: block;
  }
  .yes-title {
    font-size: 1.8rem;
    font-weight: 900;
    color: #ff6f91;
    margin: 4px 0 18px;
  }
  .gif-container {
    width: 100%;
    max-width: 320px;
    margin: 0 auto 18px;
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 10px 25px rgba(255,111,145,0.35);
  }
  .gif-container img {
    width: 100%;
    display: block;
  }
  .yes-message {
    font-size: 1.05rem;
    font-weight: 800;
    color: #a15c72;
    line-height: 1.5;
    margin: 0;
  }
  .small-note {
    font-size: 0.8rem;
    font-weight: 700;
    color: #c98da2;
    margin-top: 16px;
  }
 
  #music-toggle {
    position: fixed;
    bottom: 20px;
    right: 20px;
    z-index: 30;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    border: none;
    background: #ff6f91;
    color: white;
    font-size: 1.3rem;
    cursor: pointer;
    box-shadow: 0 6px 16px rgba(255,111,145,0.5);
    display: flex;
    align-items: center;
    justify-content: center;
  }
  @media (max-width: 480px) {
    .container {
      width: calc(100% - 24px);
      padding: 30px 18px 26px;
    }
    h1 { font-size: 1.5rem; }
    .sub { font-size: 0.85rem; }
    .buttons {
      max-width: 320px;
      height: 82px;
      gap: 8px;
    }
    .yes-size-4 { font-size: 1.55rem; padding: 16px 24px; }
    .yes-size-5 { font-size: 1.7rem; padding: 17px 26px; }
    #noBtn {
      font-size: 0.95rem;
      padding: 10px 20px;
    }
  }
</style>
</head>
<body>
 
<div class="hearts-bg" id="heartsBg"></div>
 
<div class="container" id="mainCard">
  <div class="scene">
    <span class="ring-emoji">💍</span>
    <span class="bear groom">🐻</span>
    <span class="bear bride">🐻‍❄️</span>
  </div>
 
  <h1>Will you marry me?</h1>
  <div class="sub">(the bears already said yes to each other, you're just next 🐾)</div>
  <div class="funny-line" id="funnyLine">Warning: saying yes means unlimited hugs, forever.</div>
 
  <div class="buttons">
    <button id="yesBtn" class="yes-size-1 locked" onclick="tryYes()">Yes 💍</button>
    <button id="noBtn" onclick="dodge()" onmouseover="dodge()" ontouchstart="dodgeTouch(event)">No</button>
  </div>
 
  <div class="nudge-msg" id="nudgeMsg"></div>
  <div class="tap-hint" id="tapHint">psst... try tapping No first 👀</div>
</div>
 
<div class="container yes-container" id="yesContainer">
  <h1 class="yes-title">Knew you'd say yes! 🎉</h1>
  <div class="gif-container">
    <img id="bear-gif" src="https://media1.tenor.com/m/EYU_t75LldAAAAAd/cute-bear-hug.gif" alt="bears hugging">
  </div>
  <p class="yes-message">I love you 💘<br>You just made me the happiest person alive.</p>
  <div class="small-note">forever + always + matching pajamas 🐾</div>
</div>
 
<audio id="bg-music" loop preload="auto">
  <source src="music/beabadoobee - Glue Song (Lyrics).mp3" type="audio/mpeg">
</audio>
<button id="music-toggle" onclick="toggleMusic()" title="Toggle music">🔊</button>
 
<script>
  // floating hearts background
  const heartsEmojis = ['💗','💖','💕','💞','🩷','💍','✨'];
  const heartsBg = document.getElementById('heartsBg');
  function spawnHeart() {
    const h = document.createElement('span');
    h.textContent = heartsEmojis[Math.floor(Math.random() * heartsEmojis.length)];
    h.style.left = Math.random() * 100 + 'vw';
    const duration = 6 + Math.random() * 6;
    h.style.animationDuration = duration + 's';
    h.style.fontSize = (16 + Math.random() * 18) + 'px';
    heartsBg.appendChild(h);
    setTimeout(() => h.remove(), duration * 1000 + 500);
  }
  setInterval(spawnHeart, 450);
  for (let i = 0; i < 10; i++) setTimeout(spawnHeart, i * 150);
 
  // funny rotating lines
  const funnyLines = [
    "Warning: saying yes means unlimited hugs, forever.",
    "Side effects may include: matching pajamas.",
    "No refunds, no returns, only cuddles.",
    "The bears already booked the venue.",
    "This offer will NOT expire. We are very patient.",
    "Terms & Conditions: you're stuck with me. Happily."
  ];
  let flIndex = 0;
  setInterval(() => {
    flIndex = (flIndex + 1) % funnyLines.length;
    const el = document.getElementById('funnyLine');
    el.style.transition = 'opacity 0.4s ease';
    el.style.opacity = 0;
    setTimeout(() => {
      el.textContent = funnyLines[flIndex];
      el.style.opacity = 1;
    }, 350);
  }, 3200);
 
  // No button dodges far + Yes button locked until excuses run out
  const noBtn = document.getElementById('noBtn');
  const yesBtn = document.getElementById('yesBtn');
  const nudgeMsg = document.getElementById('nudgeMsg');
  let dodgeCount = 0;
  let yesUnlocked = false;
  const noExcuses = ["No", "Nope", "Are you sure?", "Really?", "Think again!", "Nuh-uh", "Catch me first", "Too slow!", "Last chance to say yes", "I'm just a button, say yes already"];
  const nudgeLines = [
    "hey, try tapping No for a sec 👀",
    "come on, chase the No button a little",
    "keep going, it's more fun this way",
    "almost there... a few more tries",
    "so close, don't give up on No yet",
    "one more No tap and I'm all yours"
  ];
 
  function moveNoFarAway() {
    // Keep the No button inside the buttons area.
    // This prevents it from leaving the frame or blocking other page content.
    const zone = document.querySelector('.buttons');
    const zoneRect = zone.getBoundingClientRect();
    const btnRect = noBtn.getBoundingClientRect();
    const yesRect = yesBtn.getBoundingClientRect();
 
    const padding = 6;
    const halfW = btnRect.width / 2;
    const halfH = btnRect.height / 2;
 
    const minX = halfW + padding;
    const maxX = zoneRect.width - halfW - padding;
    const minY = halfH + padding;
    const maxY = zoneRect.height - halfH - padding;
 
    if (maxX <= minX || maxY <= minY) return;
 
    const yesCenterX = yesRect.left - zoneRect.left + yesRect.width / 2;
    const yesCenterY = yesRect.top - zoneRect.top + yesRect.height / 2;
 
    let x, y, dist;
    let attempts = 0;
    const minDistance = Math.min(zoneRect.width, zoneRect.height) * 0.30;
 
    do {
      x = minX + Math.random() * (maxX - minX);
      y = minY + Math.random() * (maxY - minY);
 
      const dx = x - yesCenterX;
      const dy = y - yesCenterY;
      dist = Math.sqrt(dx * dx + dy * dy);
      attempts++;
    } while (dist < minDistance && attempts < 30);
 
    noBtn.style.left = x + 'px';
    noBtn.style.top = y + 'px';
    noBtn.style.transform = 'translate(-50%, -50%)';
  }
 
  function tryYes() {
    if (yesUnlocked) { sayYes(); return; }
    yesBtn.classList.add('shake');
    setTimeout(() => yesBtn.classList.remove('shake'), 500);
    const line = nudgeLines[Math.min(dodgeCount, nudgeLines.length - 1)];
    nudgeMsg.textContent = line;
    nudgeMsg.classList.add('show');
    setTimeout(() => nudgeMsg.classList.remove('show'), 1800);
  }
 
  function dodge() {
    dodgeCount++;
    moveNoFarAway();
    noBtn.textContent = noExcuses[Math.min(dodgeCount, noExcuses.length - 1)];
    const growLevel = Math.min(dodgeCount, 5);
    yesBtn.className = 'yes-size-' + (growLevel === 0 ? 1 : growLevel) + (yesUnlocked ? '' : ' locked');
 
    if (dodgeCount >= noExcuses.length - 1 && !yesUnlocked) {
      // Final No button: place it above the bear image / scene.
      const scene = document.querySelector('.scene');
      const sceneRect = scene.getBoundingClientRect();
      const btnRect = noBtn.getBoundingClientRect();
 
      noBtn.style.left = Math.max(
        10,
        Math.min(
          window.innerWidth - btnRect.width - 10,
          sceneRect.left + (sceneRect.width - btnRect.width) / 2
        )
      ) + 'px';
 
      noBtn.style.top = Math.max(
        10,
        sceneRect.top - btnRect.height - 12
      ) + 'px';
 
      yesUnlocked = true;
      yesBtn.classList.remove('locked');
      document.getElementById('tapHint').textContent = "okay okay, the Yes button is all yours now 💍";
      nudgeMsg.textContent = "alright, you've earned it — tap Yes!";
      nudgeMsg.classList.add('show');
      setTimeout(() => nudgeMsg.classList.remove('show'), 2200);
    } else {
      document.getElementById('tapHint').textContent = "the No button ran away again 🏃‍♂️💨";
    }
  }
  function dodgeTouch(e) { e.preventDefault(); dodge(); }
 
  function sayYes() {
    // Start music immediately, synchronously, inside the click handler.
    // If this is deferred (e.g. inside a setTimeout), browsers like Safari/iOS
    // no longer treat play() as tied to a user gesture and silently block it.
    playMusic();
 
    fireConfetti();
 
    const mainCard = document.getElementById('mainCard');
    mainCard.classList.add('fading-out');
    noBtn.style.transition = 'opacity 0.4s ease';
    noBtn.style.opacity = '0';
 
    setTimeout(() => {
      mainCard.style.display = 'none';
      noBtn.style.display = 'none';
      document.getElementById('yesContainer').classList.add('show');
      fireConfetti();
    }, 550);
  }
 
  function fireConfetti() {
    if (typeof confetti === 'function') {
      confetti({
        particleCount: 140,
        spread: 90,
        origin: { y: 0.6 },
        colors: ['#ff6f91', '#f5c451', '#ffb6c1', '#ff9ecb', '#ffd97d', '#ffffff']
      });
      setTimeout(() => confetti({
        particleCount: 80,
        angle: 60,
        spread: 70,
        origin: { x: 0 }
      }), 250);
      setTimeout(() => confetti({
        particleCount: 80,
        angle: 120,
        spread: 70,
        origin: { x: 1 }
      }), 250);
    }
  }
 
  // background music
  const bgMusic = document.getElementById('bg-music');
  const musicToggle = document.getElementById('music-toggle');
  let musicPlaying = false;
 
  function playMusic() {
    bgMusic.volume = 1;
    bgMusic.currentTime = 0;
    const playPromise = bgMusic.play();
    if (playPromise !== undefined) {
      playPromise.then(() => {
        musicPlaying = true;
        musicToggle.textContent = '🔊';
      }).catch((err) => {
        // Autoplay blocked, or the file path/name doesn't match what's on the server.
        // The toggle button below still lets the user start it manually.
        console.warn('Music failed to autoplay:', err);
        musicPlaying = false;
        musicToggle.textContent = '🔇';
      });
    }
  }
 
  function toggleMusic() {
    if (musicPlaying) {
      bgMusic.pause();
      musicPlaying = false;
      musicToggle.textContent = '🔇';
    } else {
      bgMusic.play().then(() => {
        musicPlaying = true;
        musicToggle.textContent = '🔊';
      }).catch((err) => {
        console.warn('Music failed to play:', err);
      });
    }
  }
</script>
 
</body>
</html>
