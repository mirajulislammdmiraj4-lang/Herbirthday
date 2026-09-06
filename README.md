<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Happy Birthday Juthii!</title>
  <!-- Confetti/Sparkles Library -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }

    body {
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #a1c4fd 0%, #c2e9fb 100%);
      overflow: hidden;
      position: relative;
    }

    /* main container */
    .card {
      background: rgba(255, 255, 255, 0.9);
      padding: 35px 25px;
      border-radius: 24px;
      box-shadow: 0 15px 35px rgba(0,0,0,0.1);
      text-align: center;
      max-width: 380px;
      width: 88%;
      backdrop-filter: blur(10px);
      z-index: 10;
      border: 1px solid rgba(255, 255, 255, 0.6);
    }

    h1 {
      color: #334155;
      font-size: 22px;
      margin-bottom: 20px;
      font-weight: 700;
    }

    /* Screen 1: Date Input Section */
    .date-section {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .date-section input {
      padding: 12px;
      font-size: 16px;
      border-radius: 12px;
      border: 1px solid #cbd5e1;
      outline: none;
      margin-bottom: 20px;
      width: 85%;
      text-align: center;
    }

    .btn {
      padding: 12px 28px;
      font-size: 15px;
      font-weight: bold;
      background: linear-gradient(135deg, #8b5cf6, #7c3aed);
      color: white;
      border: none;
      border-radius: 25px;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(124, 58, 237, 0.3);
      transition: all 0.3s ease;
    }

    .btn:hover {
      transform: scale(1.05);
    }

    /* Screen 2: Cake Section */
    .cake-section {
      display: none;
      flex-direction: column;
      align-items: center;
    }

    .cake-container {
      position: relative;
      margin: 45px 0 20px 0;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    /* Candles */
    .candles {
      display: flex;
      gap: 22px;
      position: absolute;
      top: -38px;
      z-index: 20;
    }

    .candle {
      width: 8px;
      height: 38px;
      background: linear-gradient(to bottom, #38bdf8, #0284c7);
      border-radius: 4px;
      position: relative;
      cursor: pointer;
    }

    .flame {
      width: 12px;
      height: 18px;
      background: #f59e0b;
      border-radius: 50% 50% 20% 20%;
      position: absolute;
      top: -18px;
      left: -2px;
      animation: flicker 0.6s infinite alternate;
      box-shadow: 0 0 10px #f59e0b;
    }

    @keyframes flicker {
      0% { transform: scale(1); opacity: 0.9; }
      100% { transform: scale(1.2); opacity: 1; }
    }

    .flame.off {
      display: none;
    }

    /* 3-Tier Layered Cake Design */
    .cake-tier {
      border-radius: 12px 12px 0 0;
      box-shadow: inset 0 -4px 0 rgba(0,0,0,0.05);
    }

    .tier-top {
      width: 110px;
      height: 35px;
      background: #fbcfe8;
      border-bottom: 4px solid #f472b6;
    }

    .tier-middle {
      width: 150px;
      height: 40px;
      background: #f472b6;
      border-bottom: 4px solid #db2777;
    }

    .tier-bottom {
      width: 210px;
      height: 45px;
      background: #fbcfe8;
      border-bottom: 6px solid #f472b6;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
    }

    .cake-plate {
      width: 230px;
      height: 10px;
      background: #e2e8f0;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }

    .cake-text {
      font-size: 13px;
      font-weight: bold;
      color: #831843;
      margin-right: 5px;
    }

    .instruction {
      font-size: 13px;
      color: #64748b;
      margin-top: 15px;
    }

    /* Wish Box Popup Modal */
    .modal-overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.4);
      backdrop-filter: blur(5px);
      z-index: 100;
      justify-content: center;
      align-items: center;
    }

    .modal-box {
      background: #ffffff;
      padding: 25px;
      border-radius: 20px;
      text-align: center;
      max-width: 340px;
      width: 88%;
      max-height: 80vh;
      overflow-y: auto;
      box-shadow: 0 10px 25px rgba(0,0,0,0.2);
      animation: popIn 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }

    @keyframes popIn {
      0% { transform: scale(0.3); opacity: 0; }
      100% { transform: scale(1); opacity: 1; }
    }

    .modal-box h2 {
      color: #7c3aed;
      margin-bottom: 12px;
      font-size: 20px;
    }

    .modal-box p {
      color: #475569;
      font-size: 14px;
      line-height: 1.6;
      margin-bottom: 20px;
      white-space: pre-line;
      text-align: left;
    }
  </style>
</head>
<body>

  <div class="card">
    <!-- Screen 1: Date Section -->
    <div id="dateScreen" class="date-section">
      <h1>Enter Birthday Date 🎂</h1>
      <input type="date" id="birthDate">
      <button class="btn" onclick="submitDate()">Submit</button>
    </div>

    <!-- Screen 2: Cake Section -->
    <div id="cakeScreen" class="cake-section">
      <h1>Blow the Candles! 🎂</h1>
      
      <div class="cake-container">
        <!-- 3 Candles -->
        <div class="candles">
          <div class="candle" onclick="extinguish(1)"><div class="flame" id="flame1"></div></div>
          <div class="candle" onclick="extinguish(2)"><div class="flame" id="flame2"></div></div>
          <div class="candle" onclick="extinguish(3)"><div class="flame" id="flame3"></div></div>
        </div>

        <!-- 3-Tier Layered Cake -->
        <div class="cake-tier tier-top"></div>
        <div class="cake-tier tier-middle"></div>
        <div class="cake-tier tier-bottom">
          <span class="cake-text">Happy Birthday Juthii</span> 🤍 ✨
        </div>
        <div class="cake-plate"></div>
      </div>

      <p class="instruction">Tap on all 3 candles to blow them out!</p>
    </div>
  </div>

  <!-- Wish Box Popup Modal -->
  <div class="modal-overlay" id="wishModal">
    <div class="modal-box">
      <div style="font-size: 38px; margin-bottom: 8px;">🎉🎂🤍</div>
      <h2>Happy Birthday Juthii!</h2>
      
      <p id="wishText">Happy Birthday, Juthi! 🌸🤍

Today is a very special day because it is the day someone truly special came into this world. I hope your life is always filled with happiness, peace, success and countless beautiful moments. 🪻✨

I want you to know that no matter how difficult life becomes, I will always be there for you. Just like I want you to stay beside me, I want to stay beside you through every beautiful and difficult moment of life. 🤍

Let's keep supporting each other, understanding each other, and making beautiful memories together. I may not know what the future will look like, but I sincerely hope we can continue walking beside each other for a long, long time. 🌷🤍

May every dream of yours come true, and may your beautiful smile never fade.

Happy Birthday, Juthi. Stay happy, stay blessed, and always stay beside me. 🌸🤍</p>
      
      <button class="btn" onclick="closeWish()">Close 🤍</button>
    </div>
  </div>

  <script>
    let blownCandles = 0;
    let audioCtx = null;

    function submitDate() {
      const dateVal = document.getElementById('birthDate').value;
      if (!dateVal) {
        alert('Please select a date first!');
        return;
      }
      document.getElementById('dateScreen').style.display = 'none';
      document.getElementById('cakeScreen').style.display = 'flex';
    }

    function extinguish(id) {
      const flame = document.getElementById('flame' + id);
      if (!flame.classList.contains('off')) {
        flame.classList.add('off');
        blownCandles++;
      }

      // 3টি মোমবাতি নেভানোর পর
      if (blownCandles === 3) {
        setTimeout(() => {
          // ১. জিকিমিকি/ফায়ারওয়ার্কস এফেক্ট (Sparkles & Confetti)
          triggerSparkles();

          // ২. বার্থডে টিউন প্লে করা (Built-in Web Audio Synthesizer)
          playBirthdayTune();

          // ৩. উইশ বক্স পপ-আপ করা
          document.getElementById('wishModal').style.display = 'flex';
        }, 300);
      }
    }

    function triggerSparkles() {
      var count = 200;
      var defaults = {
        origin: { y: 0.7 }
      };

      function fire(particleRatio, opts) {
        confetti(Object.assign({}, defaults, opts, {
          particleCount: Math.floor(count * particleRatio)
        }));
      }

      fire(0.25, { spread: 26, startVelocity: 55, colors: ['#a1c4fd', '#c2e9fb'] });
      fire(0.2, { spread: 60, colors: ['#8b5cf6', '#7c3aed'] });
      fire(0.35, { spread: 100, decay: 0.91, scalar: 0.8 });
      fire(0.1, { spread: 120, startVelocity: 25, decay: 0.92, colors: ['#ffffff', '#f472b6'] });
      fire(0.1, { spread: 120, startVelocity: 45 });
    }

    function playBirthdayTune() {
      try {
        audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        
        // Happy Birthday Melody Notes and Duration
        const notes = [
          {f: 264, d: 0.3}, {f: 264, d: 0.3}, {f: 297, d: 0.6}, {f: 264, d: 0.6}, {f: 352, d: 0.6}, {f: 330, d: 1.0},
          {f: 264, d: 0.3}, {f: 264, d: 0.3}, {f: 297, d: 0.6}, {f: 264, d: 0.6}, {f: 396, d: 0.6}, {f: 352, d: 1.0},
          {f: 264, d: 0.3}, {f: 264, d: 0.3}, {f: 528, d: 0.6}, {f: 440, d: 0.6}, {f: 352, d: 0.6}, {f: 330, d: 0.6}, {f: 297, d: 0.8},
          {f: 466, d: 0.3}, {f: 466, d: 0.3}, {f: 440, d: 0.6}, {f: 352, d: 0.6}, {f: 396, d: 0.6}, {f: 352, d: 1.2}
        ];

        let currTime = audioCtx.currentTime;

        notes.forEach(note => {
          let osc = audioCtx.createOscillator();
          let gain = audioCtx.createGain();
          
          osc.type = 'triangle';
          osc.frequency.setValueAtTime(note.f, currTime);
          
          gain.gain.setValueAtTime(0.3, currTime);
          gain.gain.exponentialRampToValueAtTime(0.001, currTime + note.d);

          osc.connect(gain);
          gain.connect(audioCtx.destination);

          osc.start(currTime);
          osc.stop(currTime + note.d);

          currTime += note.d + 0.05;
        });
      } catch(e) {
        console.log("Audio play error", e);
      }
    }

    function closeWish() {
      document.getElementById('wishModal').style.display = 'none';
    }
  </script>
</body>
</html>
