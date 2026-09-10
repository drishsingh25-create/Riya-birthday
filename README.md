# Riya-birthday<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday Riya ❤️</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
      -webkit-tap-highlight-color: transparent;
    }

    body {
      background-color: #0b030e;
      color: #f1e4f3;
      min-height: 100vh;
      overflow-x: hidden;
      position: relative;
    }

    /* Important Fix: pointer-events: none ensures canvas never blocks clicks */
    #fxCanvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      pointer-events: none !important;
      z-index: 1;
    }

    .bg-glow {
      position: fixed;
      width: 300px;
      height: 300px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(230, 57, 107, 0.15) 0%, rgba(0,0,0,0) 70%);
      pointer-events: none;
      z-index: 0;
    }
    .glow-1 { top: -50px; left: -50px; }
    .glow-2 { bottom: -50px; right: -50px; }

    .container {
      width: 100%;
      max-width: 800px;
      margin: 0 auto;
      padding: 20px;
      position: relative;
      z-index: 10;
    }

    .subtitle {
      text-transform: uppercase;
      letter-spacing: 3px;
      font-size: 0.85rem;
      color: #ff7597;
      margin-bottom: 8px;
      font-weight: 600;
    }

    .main-title {
      font-size: 2.2rem;
      font-weight: 700;
      color: #ffffff;
      text-shadow: 0 0 20px rgba(255, 105, 180, 0.3);
      margin-bottom: 15px;
      line-height: 1.2;
    }

    .section-title {
      font-size: 1.8rem;
      color: #fff;
      text-align: center;
      margin: 50px 0 25px 0;
      text-shadow: 0 0 10px rgba(255, 117, 151, 0.3);
    }

    p {
      line-height: 1.7;
      color: #d8c3dd;
      font-size: 1rem;
    }

    /* Button Styling with click priority */
    .btn-romantic {
      background: linear-gradient(135deg, #e6396b, #981d4a);
      color: white;
      border: none;
      padding: 16px 36px;
      font-size: 1.05rem;
      font-weight: 600;
      border-radius: 50px;
      cursor: pointer;
      box-shadow: 0 0 20px rgba(230, 57, 107, 0.4);
      display: inline-block;
      outline: none;
      margin-top: 20px;
      position: relative;
      z-index: 9999 !important;
      pointer-events: auto !important;
    }

    .btn-romantic:hover, .btn-romantic:active {
      transform: translateY(-2px) scale(1.02);
      box-shadow: 0 0 30px rgba(230, 57, 107, 0.7);
    }

    /* SCREEN 1: INTRO */
    #screen-intro {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      text-align: center;
      padding: 20px;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 100;
      background: #0b030e;
    }

    /* SCREEN 2-6: MAIN CONTENT */
    #main-content {
      display: none;
      opacity: 0;
      transition: opacity 0.5s ease-in-out;
    }

    .hero-section {
      text-align: center;
      padding: 60px 20px 40px 20px;
    }

    .countdown-box {
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      border-radius: 16px;
      padding: 20px;
      margin-top: 30px;
    }

    .countdown-title {
      font-size: 0.8rem;
      letter-spacing: 2px;
      color: #ff7597;
      margin-bottom: 12px;
    }

    .timer {
      display: flex;
      justify-content: center;
      gap: 12px;
    }

    .timer-unit {
      display: flex;
      flex-direction: column;
      align-items: center;
      min-width: 55px;
    }

    .timer-val {
      font-size: 1.8rem;
      font-weight: 700;
      color: #fff;
    }

    .timer-lbl {
      font-size: 0.65rem;
      color: #a48ca8;
      text-transform: uppercase;
      margin-top: 4px;
    }

    .cards-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 16px;
      margin-top: 20px;
    }

    .card {
      background: rgba(255, 255, 255, 0.02);
      border: 1px solid rgba(255, 117, 151, 0.15);
      border-radius: 12px;
      padding: 20px;
    }

    .card-title {
      font-size: 1.1rem;
      color: #ff7597;
      margin-bottom: 8px;
      font-weight: 600;
    }

    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 15px;
    }

    .photo-card {
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid rgba(255, 255, 255, 0.08);
      border-radius: 12px;
      overflow: hidden;
      aspect-ratio: 4/5;
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .photo-card img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
    }

    .photo-placeholder {
      padding: 20px;
      text-align: center;
      color: #7a637f;
      font-size: 0.85rem;
    }

    .letter-card {
      background: linear-gradient(180deg, rgba(255,255,255,0.03) 0%, rgba(255,117,151,0.02) 100%);
      border: 1px solid rgba(255, 117, 151, 0.2);
      border-radius: 16px;
      padding: 30px 25px;
      margin-top: 20px;
    }

    .letter-card p {
      margin-bottom: 18px;
      text-align: justify;
    }

    .signature {
      margin-top: 25px;
      font-weight: 700;
      color: #ff7597;
      font-size: 1.1rem;
      text-align: right;
    }

    .final-section {
      text-align: center;
      padding: 80px 20px 60px 20px;
      margin-top: 40px;
      border-top: 1px solid rgba(255,255,255,0.05);
    }

    .huge-text {
      font-size: 2.8rem;
      font-weight: 800;
      color: #ffffff;
      text-shadow: 0 0 25px rgba(230, 57, 107, 0.6);
      line-height: 1.2;
      margin: 15px 0;
    }
  </style>
</head>
<body>

  <canvas id="fxCanvas"></canvas>
  <div class="bg-glow glow-1"></div>
  <div class="bg-glow glow-2"></div>

  <!-- INTRO SCREEN -->
  <div id="screen-intro">
    <div class="subtitle">A little surprise for you</div>
    <h1 class="main-title">Hey, Riya ❤️</h1>
    <p style="max-width: 400px; margin: 0 auto 10px auto;">
      I made this little corner of the internet just for you.
    </p>
    <button type="button" class="btn-romantic" id="btnSurprise">
      OPEN YOUR SURPRISE ✨
    </button>
  </div>

  <!-- MAIN SURPRISE CONTENT -->
  <div id="main-content">
    <div class="container">

      <!-- SCREEN 2 — BIRTHDAY REVEAL -->
      <section class="hero-section">
        <div class="subtitle">Today is all about you</div>
        <h1 class="main-title">HAPPY BIRTHDAY, RIYA 🎂❤️</h1>
        <p>May this new chapter bring you the kind of happiness you deserve.</p>

        <div class="countdown-box">
          <div class="countdown-title">COUNTING DOWN TO MIDNIGHT</div>
          <div class="timer">
            <div class="timer-unit">
              <span class="timer-val" id="td-days">00</span>
              <span class="timer-lbl">Days</span>
            </div>
            <div class="timer-unit">
              <span class="timer-val" id="td-hours">00</span>
              <span class="timer-lbl">Hours</span>
            </div>
            <div class="timer-unit">
              <span class="timer-val" id="td-mins">00</span>
              <span class="timer-lbl">Mins</span>
            </div>
            <div class="timer-unit">
              <span class="timer-val" id="td-secs">00</span>
              <span class="timer-lbl">Secs</span>
            </div>
          </div>
        </div>
      </section>

      <!-- SCREEN 3 — WHY YOU -->
      <section>
        <h2 class="section-title">Why You? ❤️</h2>
        <div class="cards-grid">
          <div class="card"><div class="card-title">1. Your Smile</div><p>It has a way of making ordinary moments feel special.</p></div>
          <div class="card"><div class="card-title">2. Your Eyes</div><p>There is something about them that is impossible to forget.</p></div>
          <div class="card"><div class="card-title">3. Your Heart</div><p>The way you care makes you more beautiful than you realize.</p></div>
          <div class="card"><div class="card-title">4. Your Presence</div><p>Even a simple conversation with you can change my whole day.</p></div>
          <div class="card"><div class="card-title">5. Your Little Things</div><p>Your tiny habits, moods, laughs and moments mean so much.</p></div>
          <div class="card"><div class="card-title">6. Simply You</div><p>I do not need a perfect reason. I just love you for being you.</p></div>
        </div>
      </section>

      <!-- SCREEN 4 — PHOTO GALLERY -->
      <section>
        <h2 class="section-title">Moments I Want To Keep ❤️</h2>
        <div class="gallery-grid">
          <!-- IMAGE SLOT 1 -->
          <div class="photo-card">
            <img src="photo1.jpg" alt="Riya memory 1" onerror="this.style.display='none'; this.nextElementSibling.style.display='block';">
            <div class="photo-placeholder" style="display:none;">Photo 1 (photo1.jpg)</div>
          </div>

          <!-- IMAGE SLOT 2 -->
          <div class="photo-card">
            <img src="photo2.jpg" alt="Riya memory 2" onerror="this.style.display='none'; this.nextElementSibling.style.display='block';">
            <div class="photo-placeholder" style="display:none;">Photo 2 (photo2.jpg)</div>
          </div>

          <!-- IMAGE SLOT 3 -->
          <div class="photo-card">
            <img src="photo3.jpg" alt="Riya memory 3" onerror="this.style.display='none'; this.nextElementSibling.style.display='block';">
            <div class="photo-placeholder" style="display:none;">Photo 3 (photo3.jpg)</div>
          </div>

          <!-- IMAGE SLOT 4 -->
          <div class="photo-card">
            <img src="photo4.jpg" alt="Riya memory 4" onerror="this.style.display='none'; this.nextElementSibling.style.display='block';">
            <div class="photo-placeholder" style="display:none;">Photo 4 (photo4.jpg)</div>
          </div>

          <!-- IMAGE SLOT 5 -->
          <div class="photo-card">
            <img src="photo5.jpg" alt="Riya memory 5" onerror="this.style.display='none'; this.nextElementSibling.style.display='block';">
            <div class="photo-placeholder" style="display:none;">Photo 5 (photo5.jpg)</div>
          </div>

          <!-- IMAGE SLOT 6 -->
          <div class="photo-card">
            <img src="photo6.jpg" alt="Riya memory 6" onerror="this.style.display='none'; this.nextElementSibling.style.display='block';">
            <div class="photo-placeholder" style="display:none;">Photo 6 (photo6.jpg)</div>
          </div>
        </div>
      </section>

      <!-- SCREEN 5 — HEARTFELT MESSAGE -->
      <section>
        <h2 class="section-title">A Letter For Riya</h2>
        <div class="letter-card">
          <p>Riya, if I could give you one thing on your birthday, it would be the ability to see yourself through my eyes for just a moment — because then you would understand how incredibly precious you are to me.</p>
          <p>You are not just someone I talk to. Somehow, you became someone my heart looks for. Your smile, your eyes, your little moods, the way you care, the way you get angry, the random conversations and even the smallest things about you have found a place in my heart.</p>
          <p>I know you may sometimes doubt yourself or feel that you are not beautiful enough. Please never let those thoughts win. To me, your beauty has never been about being perfect. It is in the way you are you — completely, naturally and beautifully. I wish you could see what I see when I look at you.</p>
          <p>On your birthday, I want you to promise me one thing: be a little kinder to yourself. Choose yourself, smile more, chase everything that makes you happy, and never forget that you deserve to be loved gently and completely.</p>
          <p>I do not know what every tomorrow will look like, but I know one thing — I am genuinely grateful that you became such a beautiful part of my life. You mean more to me than a simple birthday message could ever explain.</p>
          <p>So today, forget every insecurity for a while, look at yourself and smile. Somewhere, there is a person who looks at you and thinks, 'How did I get so lucky to have you in my life?'</p>
          <div class="signature">Happy Birthday, Riya. ❤️</div>
        </div>
      </section>

      <!-- SCREEN 6 — FINAL REVEAL -->
      <section class="final-section">
        <div class="subtitle">One last thing...</div>
        <h1 class="huge-text">I LOVE YOU<br>RIYA ❤️</h1>
        <p style="max-width: 500px; margin: 0 auto 25px auto;">
          You are one of the most beautiful chapters I never want to stop reading.
        </p>
        <button type="button" class="btn-romantic" id="btnCelebrate">
          CELEBRATE AGAIN 🎉
        </button>
      </section>

    </div>
  </div>

  <script>
    // Direct click binding ensuring no script delays
    var btnSurprise = document.getElementById("btnSurprise");
    var btnCelebrate = document.getElementById("btnCelebrate");
    var screenIntro = document.getElementById("screen-intro");
    var mainContent = document.getElementById("main-content");

    function revealSurprise() {
      screenIntro.style.display = "none";
      mainContent.style.display = "block";
      setTimeout(function() {
        mainContent.style.opacity = "1";
      }, 50);
      if(window.fireConfetti) window.fireConfetti();
    }

    btnSurprise.onclick = revealSurprise;

    btnCelebrate.onclick = function() {
      if(window.fireConfetti) window.fireConfetti();
    };

    // Countdown
    function updateCountdown() {
      var now = new Date();
      var target = new Date(now.getFullYear(), 8, 11, 0, 0, 0); // Sept 11
      if (now.getTime() > target.getTime() + (24 * 60 * 60 * 1000)) {
        target.setFullYear(now.getFullYear() + 1);
      }

      var diff = target.getTime() - now.getTime();
      if (diff <= 0) {
        document.getElementById("td-days").innerText = "00";
        document.getElementById("td-hours").innerText = "00";
        document.getElementById("td-mins").innerText = "00";
        document.getElementById("td-secs").innerText = "00";
        return;
      }

      var days = Math.floor(diff / (1000 * 60 * 60 * 24));
      var hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
      var mins = Math.floor((diff / 1000 / 60) % 60);
      var secs = Math.floor((diff / 1000) % 60);

      document.getElementById("td-days").innerText = days < 10 ? "0" + days : days;
      document.getElementById("td-hours").innerText = hours < 10 ? "0" + hours : hours;
      document.getElementById("td-mins").innerText = mins < 10 ? "0" + mins : mins;
      document.getElementById("td-secs").innerText = secs < 10 ? "0" + secs : secs;
    }

    setInterval(updateCountdown, 1000);
    updateCountdown();

    // Canvas Background
    var canvas = document.getElementById("fxCanvas");
    var ctx = canvas.getContext("2d");

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    window.addEventListener("resize", resizeCanvas);
    resizeCanvas();

    var hearts = [];
    for (var i = 0; i < 25; i++) {
      hearts.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        size: Math.random() * 12 + 8,
        speedY: Math.random() * 0.7 + 0.3,
        opacity: Math.random() * 0.5 + 0.2
      });
    }

    var confetti = [];
    window.fireConfetti = function() {
      for (var i = 0; i < 90; i++) {
        confetti.push({
          x: canvas.width / 2,
          y: canvas.height / 2,
          vx: (Math.random() - 0.5) * 14,
          vy: (Math.random() - 0.7) * 14,
          size: Math.random() * 8 + 4,
          color: ["#ff7597", "#e6396b", "#ffffff", "#ffd1dc"][Math.floor(Math.random() * 4)],
          alpha: 1
        });
      }
    };

    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      for (var i = 0; i < hearts.length; i++) {
        var h = hearts[i];
        h.y -= h.speedY;
        if (h.y < -20) {
          h.y = canvas.height + 20;
          h.x = Math.random() * canvas.width;
        }
        ctx.globalAlpha = h.opacity;
        ctx.fillStyle = "#ff7597";
        ctx.beginPath();
        ctx.arc(h.x, h.y, h.size/2, 0, Math.PI * 2);
        ctx.fill();
      }

      for (var j = confetti.length - 1; j >= 0; j--) {
        var c = confetti[j];
        c.x += c.vx;
        c.y += c.vy;
        c.vy += 0.25;
        c.alpha -= 0.015;

        ctx.globalAlpha = Math.max(c.alpha, 0);
        ctx.fillStyle = c.color;
        ctx.fillRect(c.x, c.y, c.size, c.size);

        if (c.alpha <= 0) confetti.splice(j, 1);
      }

      requestAnimationFrame(animate);
    }
    animate();
  </script>
</body>
</html>