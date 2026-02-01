<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Pankhuri, Will You Be My Valentine?</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
:root {
  --pink:#FFB3D9;
  --soft-pink:#FFE5F1;
  --coral:#FF8FAB;
  --beige:#FFF5E4;
  --soft-red:#FF6B9D;
  --cream:#FFFEF9;
  --text:#5A4A4A;
}

* { box-sizing:border-box; }

body {
  margin:0;
  font-family:'Segoe UI',sans-serif;
  background:linear-gradient(135deg,var(--soft-pink),var(--beige));
  color:var(--text);
  overflow-x:hidden;
}

/* Floating hearts */
.heart {
  position:fixed;
  bottom:-20px;
  font-size:18px;
  animation:floatUp 6s linear infinite;
  opacity:.7;
}

@keyframes floatUp {
  to { transform:translateY(-110vh) scale(1.5); opacity:0; }
}

section {
  padding:30px 16px;
  max-width:900px;
  margin:auto;
}

h1,h2 {
  text-align:center;
  animation:softPop .8s ease;
}

@keyframes softPop {
  from {transform:scale(.9);opacity:0}
  to {transform:scale(1);opacity:1}
}

.card {
  background:var(--cream);
  border-radius:22px;
  padding:22px;
  margin-bottom:26px;
  box-shadow:0 12px 28px rgba(0,0,0,.08);
  animation:fadeUp .8s ease;
}

@keyframes fadeUp {
  from {transform:translateY(20px);opacity:0}
  to {transform:translateY(0);opacity:1}
}

.letter { line-height:1.75; }

/* Valentine buttons */
.valentine-box {
  text-align:center;
  position:relative;
}

.yes-btn {
  background:var(--soft-red);
  color:#fff;
  border:none;
  padding:16px 34px;
  border-radius:32px;
  font-size:1.1rem;
  animation:pulse 1.8s infinite;
  cursor:pointer;
}

@keyframes pulse {
  0%{box-shadow:0 0 0 0 rgba(255,107,157,.6)}
  70%{box-shadow:0 0 0 18px rgba(255,107,157,0)}
  100%{box-shadow:0 0 0 0 rgba(255,107,157,0)}
}

.no-btn {
  background:#ddd;
  border:none;
  padding:14px 28px;
  border-radius:28px;
  position:absolute;
  cursor:pointer;
}

/* Confetti */
.confetti {
  position:fixed;
  width:10px;
  height:10px;
  top:-10px;
  animation:fall 3s linear forwards;
}

@keyframes fall {
  to { transform:translateY(110vh) rotate(360deg); }
}

/* Heart text spell */
.heart-text {
  position:fixed;
  top:40%;
  left:50%;
  transform:translate(-50%,-50%);
  display:flex;
  gap:6px;
  z-index:999;
}

.heart-letter {
  font-size:30px;
  color:#FF6B9D;
  opacity:0;
  animation:popIn .6s ease forwards, glow 1.5s infinite alternate;
}

@keyframes popIn {
  from {transform:translateY(20px) scale(.5);opacity:0}
  to {transform:translateY(0) scale(1);opacity:1}
}

@keyframes glow {
  from {text-shadow:0 0 6px #FFB3D9}
  to {text-shadow:0 0 16px #FF6B9D}
}

footer {
  text-align:center;
  padding:26px;
  font-size:.9rem;
}

/* Music button */
.music-hint {
  position:fixed;
  bottom:18px;
  right:18px;
  background:var(--soft-red);
  color:#fff;
  padding:10px 14px;
  border-radius:22px;
  font-size:.85rem;
  cursor:pointer;
}
</style>
</head>

<body>

<!-- Floating hearts -->
<script>
setInterval(()=>{
  const h=document.createElement("div");
  h.className="heart";
  h.innerText=["💖","💗","💕","💞","✨"][Math.floor(Math.random()*5)];
  h.style.left=Math.random()*100+"vw";
  h.style.animationDuration=4+Math.random()*3+"s";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),7000);
},500);
</script>

<section>
<h1>💖 Pankhuri, Will You Be My Valentine? 💖</h1>
</section>

<section class="card letter">
<h2>💌 A Letter for You</h2>
<p>
Dear Pankhuri,<br><br>
From the moment you walked into my life, things just felt lighter.
Your smile has this quiet magic that turns ordinary days into something special.
Being with you feels like home — safe, warm, and full of little moments I never want to forget.
<br><br>
Thank you for choosing me, for understanding me, and for loving me the way you do.
And no matter how much time passes or how much we grow,
just know that for me, you'll always be <b>my chota</b> 🤍.
<br><br>
Love,<br><b>Aditya ❤️</b>
</p>
</section>

<section class="card valentine-box">
<h2>💘 Will You Be My Valentine?</h2>
<button class="yes-btn" onclick="celebrate()">YES 💖</button>
<button class="no-btn" id="noBtn">No 🙈</button>
</section>

<footer>
Made with all my love by Aditya  
for Pankhuri ❤️
</footer>

<!-- MUSIC -->
<audio id="song" loop>
  <source src="https://dl.dropboxusercontent.com/scl/fi/1g0x5l0j4v8t6j9m2t6fs/starboy-hook.mp3?rlkey=example" type="audio/mpeg">
</audio>

<div class="music-hint" onclick="playMusic()">🎵 tap for music</div>

<script>
const song=document.getElementById("song");

// Try autoplay
window.onload=()=>song.play().catch(()=>{});

// No button runs away
const noBtn=document.getElementById("noBtn");
noBtn.addEventListener("mouseenter",move);
noBtn.addEventListener("touchstart",move);

function move(){
  noBtn.style.left=Math.random()*70+"%";
  noBtn.style.top=Math.random()*70+"%";
}

// Spell name with hearts
function spellName(name){
  const box=document.createElement("div");
  box.className="heart-text";

  name.split("").forEach((l,i)=>{
    const s=document.createElement("span");
    s.className="heart-letter";
    s.innerHTML="💖"+l;
    s.style.animationDelay=i*0.15+"s";
    box.appendChild(s);
  });

  document.body.appendChild(box);
  setTimeout(()=>box.remove(),6000);
}

// Confetti + music + name
function celebrate(){
  playMusic();

  for(let i=0;i<90;i++){
    const c=document.createElement("div");
    c.className="confetti";
    c.style.left=Math.random()*100+"vw";
    c.style.background=["#FF6B9D","#FFB3D9","#FF8FAB","#FFE5F1"][Math.floor(Math.random()*4)];
    document.body.appendChild(c);
    setTimeout(()=>c.remove(),3000);
  }

  spellName("PANKHURI");

  setTimeout(()=>{
    alert("I knew it 💖 You're my Valentine!");
  },1200);
}

function playMusic(){
  song.play().catch(()=>{});
}
</script>

</body>
</html>

