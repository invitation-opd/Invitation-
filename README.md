
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Birthday Invitation</title>
<style>
  @font-face {
    font-family: 'RobotoBold';
    src: local('Roboto'), local('Roboto-Bold'), url('https://fonts.googleapis.com/css2?family=Roboto:wght@700&display=swap') format('woff2');
    font-weight: bold;
  }
  body {
    margin: 0;
    font-family: 'RobotoBold', sans-serif;
    background: #000;
    color: #FFD700;
    text-align: center;
    overflow-x: hidden;
    position: relative;
  }
  #particles {
    position: fixed;
    width: 100%;
    height: 100%;
    z-index: -1;
    top: 0;
    left: 0;
  }
  .container {
    position: relative;
    max-width: 750px;
    margin: 50px auto;
    background: rgba(0,0,0,0.85);
    border: 2px solid #FFD700;
    border-radius: 25px;
    padding: 50px 40px;
    box-shadow: 0 0 40px rgba(255,215,0,0.6);
    opacity: 0;
    animation: fadeInSlide 2s forwards;
  }
  @keyframes fadeInSlide {
    0% {opacity: 0; transform: translateY(50px);}
    100% {opacity: 1; transform: translateY(0);}
  }
  h1 { font-size: 4em; margin-bottom: 10px; text-shadow: 0 0 15px #FFD700; }
  h2 { font-size: 1.7em; margin-bottom: 30px; }
  p { font-size: 1.2em; margin: 10px 0; }
  a.button {
    display: inline-block; padding: 15px 30px; margin: 25px 0;
    font-weight: bold; color: #000; background: #FFD700;
    border-radius: 30px; text-decoration: none;
    box-shadow: 0 0 20px rgba(255,215,0,0.6);
    transition: all 0.3s ease; animation: bounceIn 2s forwards;
  }
  a.button:hover { transform: scale(1.08); box-shadow: 0 0 30px rgba(255,215,0,0.9); }
  @keyframes bounceIn {
    0% {transform: translateY(-100px); opacity: 0;}
    60% {transform: translateY(20px); opacity: 1;}
    80% {transform: translateY(-10px);}
    100% {transform: translateY(0);}
  }
  #countdown {
    font-size: 2.5em; margin: 25px 0; font-weight: bold;
    letter-spacing: 1px; text-shadow: 0 0 15px #FFD700;
    animation: glow 1.5s infinite alternate;
  }
  @keyframes glow {
    from {text-shadow: 0 0 10px #FFD700, 0 0 20px #FFD700;}
    to {text-shadow: 0 0 20px #FFD700, 0 0 40px #FFD700;}
  }
</style>
</head>
<body>

<canvas id="particles"></canvas>

<div class="container">
  <h1>🎉 LITA’S BIRTHDAY</h1>
  <h2>✨ A Night to Remember — Let’s Celebrate Together</h2>
  <p>📅 Tuesday, October 28, 2025</p>
  <p>🕖 7:00 PM</p>
  <p>📍 Black Owl, Surabaya</p>
  <p>👗 Dresscode: Black</p>
  <a href="https://wa.me/6282287000029" target="_blank" class="button">💬 RSVP via WhatsApp</a>
  <div id="countdown"></div>
</div>

<!-- Musik meriah autoplay (base64 embedded) -->
<audio id="bg-music" autoplay loop>
  <source src="data:audio/mpeg;base64,//BASE64_AUDIO_MERIAH_HERE" type="audio/mpeg">
</audio>

<script>
  // Countdown Timer
  const eventDate = new Date("October 28, 2025 19:00:00").getTime();
  const countdown = document.getElementById("countdown");
  function updateCountdown() {
    const now = new Date().getTime();
    const distance = eventDate - now;
    if(distance < 0) { countdown.innerHTML = "🎉 The party is on! 🎉"; clearInterval(timerInterval); return; }
    const days = Math.floor(distance / (1000 * 60 * 60 * 24));
    const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
    const seconds = Math.floor((distance % (1000 * 60)) / 1000);
    countdown.innerHTML = `${days}d ${hours}h ${minutes}m ${seconds}s`;
  }
  const timerInterval = setInterval(updateCountdown, 1000);
  updateCountdown();

  // Particle Background
  const canvas = document.getElementById('particles');
  const ctx = canvas.getContext('2d');
  let w, h;
  function resize() { w = canvas.width = window.innerWidth; h = canvas.height = window.innerHeight; }
  window.addEventListener('resize', resize); resize();

  const particlesArray = [];
  const particleCount = 100;
  function Particle(){ this.x = Math.random()*w; this.y = Math.random()*h; this.size = Math.random()*3+1; this.speedX = Math.random()*1-0.5; this.speedY = Math.random()*1-0.5; }
  Particle.prototype.update = function(){ this.x+=this.speedX; this.y+=this.speedY; if(this.x<0||this.x>w)this.speedX*=-1; if(this.y<0||this.y>h)this.speedY*=-1; }
  Particle.prototype.draw = function(){ ctx.fillStyle="#FFD700"; ctx.beginPath(); ctx.arc(this.x,this.y,this.size,0,Math.PI*2); ctx.fill(); }
  function initParticles(){ particlesArray.length=0; for(let i=0;i<particleCount;i++){ particlesArray.push(new Particle()); } }
  function animateParticles(){ ctx.clearRect(0,0,w,h); particlesArray.forEach(p=>{p.update();p.draw();}); requestAnimationFrame(animateParticles); }
  initParticles(); animateParticles();
</script>
</body>
</html>
