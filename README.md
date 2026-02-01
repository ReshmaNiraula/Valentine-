<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<title>💘 Piyush Valentine</title>

<style>
:root{
  --bg1:#0b0b12;
  --bg2:#190b2f;
  --card:rgba(20,20,35,0.78);
  --stroke:rgba(255,255,255,0.14);
  --text:#f7f7ff;
  --muted:rgba(255,255,255,0.72);
}

*{
  box-sizing:border-box;
  -webkit-tap-highlight-color:transparent;
}

html, body{
  margin:0;
  padding:0;
  height:auto;
  overflow-y:auto;              /* allow scroll */
  -webkit-overflow-scrolling:touch;
}

body{
  min-height:100vh;
  font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial;
  color:var(--text);
  background:
    radial-gradient(1200px 800px at 20% 15%, #ff4d87 0%, transparent 55%),
    radial-gradient(1200px 800px at 80% 85%, #ffb703 0%, transparent 55%),
    linear-gradient(180deg,var(--bg2),var(--bg1));
}

/* floating hearts background */
.hearts{
  position:fixed;
  inset:0;
  pointer-events:none;
  z-index:0;
}
.heart{
  position:absolute;
  bottom:-40px;
  opacity:.75;
  font-size:18px;
  animation:floatUp linear infinite;
}
@keyframes floatUp{
  0%{transform:translateY(0);opacity:0}
  10%{opacity:.75}
  100%{transform:translateY(-120vh);opacity:0}
}

/* Normal website layout (scroll-friendly) */
.page{
  position:relative;
  z-index:1;
  padding:18px 14px 60px;
  max-width:920px;
  margin:0 auto;
}

.card{
  background:var(--card);
  border-radius:26px;
  border:1px solid var(--stroke);
  backdrop-filter:blur(10px);
  overflow:hidden;
  margin-top: 12px;
}

/* top bar */
.topbar{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:10px;
  padding:14px;
  border-bottom:1px solid rgba(255,255,255,.10);
}
.pill{
  font-size:12px;
  padding:6px 10px;
  border-radius:999px;
  border:1px solid var(--stroke);
  white-space:nowrap;
}
.progress{
  flex:1;
  height:6px;
  background:rgba(255,255,255,.10);
  border-radius:999px;
  overflow:hidden;
}
.progress div{
  height:100%;
  width:40%;
  background:linear-gradient(90deg,#ff4d87,#ffb703);
}

/* content */
.content{
  padding:18px;
  display:grid;
  gap:14px;
  text-align:center;
}
h1{
  margin:0;
  font-size:clamp(26px,4vw,42px);
  line-height:1.06;
}
.sub{
  margin:0;
  color:var(--muted);
  font-size:16px;
  line-height:1.4;
}

/* image */
.frame{
  border-radius:22px;
  overflow:hidden;
  border:1px solid var(--stroke);
  background:rgba(0,0,0,0.18);
}
.photo{
  width:100%;
  height:auto;
  display:block;
  object-fit:cover;
}

/* actions */
.actions{
  position:relative;
  height:110px;                 /* more room for runaway button */
  display:flex;
  align-items:center;
  justify-content:center;
  margin-top:4px;
  touch-action: pan-y;          /* allow vertical scrolling */
}

button{
  border:none;
  border-radius:18px;
  padding:14px 22px;
  font-size:18px;
  font-weight:800;
  cursor:pointer;
}
.yes{
  background:linear-gradient(135deg,#ff4d87,#ffb703);
  color:#1b1020;
}
.no{
  position:absolute;
  right:10px;
  top:10px;
  background:rgba(255,255,255,.20);
  color:white;
}

.footer{
  margin:0;
  font-size:14px;
  color:rgba(255,255,255,0.65);
}

.hidden{ display:none; }

/* Confetti (emoji fall) */
@keyframes fall{
  to{ transform:translateY(120vh) rotate(360deg); opacity:0; }
}

</style>
</head>

<body>
<div class="hearts" id="hearts"></div>

<div class="page">
  <div class="card">

    <!-- ASK SCREEN -->
    <section id="ask">
      <div class="topbar">
        <div class="pill">💌 For Piyush</div>
        <div class="progress"><div id="prog"></div></div>
        <div class="pill">💘 Valentine</div>
      </div>

      <div class="content">
        <h1>Piyush, will you be my Valentine? 💘</h1>
        <p class="sub">Choose wisely 😌</p>

        <div class="frame">
          <img src="ask.PNG" class="photo" alt="Us together">
        </div>

        <div class="actions" id="arena">
          <button class="yes" id="yesBtn">Yes 💖</button>
          <button class="no" id="noBtn">No 🙅‍♂️</button>
        </div>

        <p class="footer">Hint: saying no has consequences</p>
      </div>
    </section>

    <!-- YES SCREEN -->
    <section id="yes" class="hidden">
      <div class="topbar">
        <div class="pill">✅ Accepted</div>
        <div class="progress"><div style="width:100%"></div></div>
        <div class="pill">🥰 Locked in</div>
      </div>

      <div class="content">
        <h1>YAYYYYY 🥰</h1>
        <p class="sub">Congratulations Piyush 💕<br>You are officially my Valentine.</p>

        <div class="frame">
          <img src="yes.jpg" class="photo" alt="Piyush">
        </div>

        <p class="sub">Love, Reshma 💖</p>
        <p class="footer">Now come here, Valentine 😌💞</p>
      </div>
    </section>

  </div>
</div>

<script>
const noBtn = document.getElementById("noBtn");
const yesBtn = document.getElementById("yesBtn");
const arena = document.getElementById("arena");
const ask = document.getElementById("ask");
const yes = document.getElementById("yes");
const prog = document.getElementById("prog");

const phrases = [
  "No 🙅‍♂️",
  "Pitchu aile ma 🥺",
  "Piyush pls 😭",
  "Wrong answer 😌",
  "Try again 🙂",
  "Nice try 😏",
  "Just press Yes 💖"
];
let count = 0;

function moveNo(){
  const maxX = arena.offsetWidth - noBtn.offsetWidth - 10;
  const maxY = arena.offsetHeight - noBtn.offsetHeight - 10;
  const x = Math.max(10, Math.random() * Math.max(10, maxX));
  const y = Math.max(10, Math.random() * Math.max(10, maxY));
  noBtn.style.left = x + "px";
  noBtn.style.top = y + "px";
  noBtn.style.right = "auto";
  noBtn.textContent = phrases[Math.min(count++, phrases.length - 1)];
}

/* Desktop hover */
["mouseenter","mouseover"].forEach(evt => {
  noBtn.addEventListener(evt, () => moveNo(), {passive:true});
});

/* Mobile touch: only prevent default on the NO button itself (does not block page scroll) */
noBtn.addEventListener("touchstart", (e) => {
  e.preventDefault();
  moveNo();
}, {passive:false});

/* If he somehow clicks No, still show Yes */
noBtn.addEventListener("click", (e) => {
  e.preventDefault();
  showYes();
});

yesBtn.addEventListener("click", showYes);

function showYes(){
  prog.style.width = "100%";
  ask.classList.add("hidden");
  yes.classList.remove("hidden");
  confetti();
  window.scrollTo({top:0,behavior:"smooth"});
}

function confetti(){
  const emojis = ["💖","💘","💝","✨","🥰","💞"];
  for(let i=0;i<24;i++){
    const s=document.createElement("span");
    s.textContent = emojis[Math.floor(Math.random()*emojis.length)];
    s.style.position="fixed";
    s.style.left = Math.random()*100 + "vw";
    s.style.top = "-20px";
    s.style.fontSize = (16 + Math.random()*24) + "px";
    s.style.animation = "fall 1.6s ease forwards";
    s.style.pointerEvents = "none";
    document.body.appendChild(s);
    setTimeout(()=>s.remove(),1600);
  }
}

/* Floating hearts */
setInterval(()=>{
  const h=document.createElement("div");
  h.className="heart";
  h.textContent=["💗","💖","💘","✨"][Math.floor(Math.random()*4)];
  h.style.left=Math.random()*100 + "vw";
  h.style.animationDuration=(6+Math.random()*6) + "s";
  document.getElementById("hearts").appendChild(h);
  setTimeout(()=>h.remove(),12000);
}, 420);
</script>

</body>
</html>
