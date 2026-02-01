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
--muted:rgba(255,255,255,0.7);
}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html,body{height:100%}
body{
margin:0;
font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial;
color:var(--text);
background:
radial-gradient(1200px 800px at 20% 15%, #ff4d87 0%, transparent 55%),
radial-gradient(1200px 800px at 80% 85%, #ffb703 0%, transparent 55%),
linear-gradient(180deg,var(--bg2),var(--bg1));
overflow:hidden;
}

/* floating hearts */
.hearts{position:fixed;inset:0;pointer-events:none}
.heart{
position:absolute;
bottom:-40px;
animation:floatUp linear infinite;
opacity:.75;
font-size:18px;
}
@keyframes floatUp{
0%{transform:translateY(0);opacity:0}
10%{opacity:.75}
100%{transform:translateY(-120vh);opacity:0}
}

.wrap{
min-height:100%;
display:flex;
align-items:center;
justify-content:center;
padding:18px;
}
.card{
width:min(820px,100%);
background:var(--card);
border-radius:26px;
border:1px solid var(--stroke);
backdrop-filter:blur(10px);
overflow:hidden;
}

/* top bar */
.topbar{
display:flex;
align-items:center;
justify-content:space-between;
padding:14px;
border-bottom:1px solid rgba(255,255,255,.1);
}
.pill{
font-size:12px;
padding:6px 10px;
border-radius:999px;
border:1px solid var(--stroke);
}
.progress{
flex:1;
height:6px;
margin:0 10px;
background:rgba(255,255,255,.1);
border-radius:999px;
overflow:hidden;
}
.progress div{
height:100%;
width:40%;
background:linear-gradient(90deg,#ff4d87,#ffb703);
}

.content{
padding:16px;
display:grid;
gap:12px;
text-align:center;
}
h1{
margin:0;
font-size:clamp(26px,4vw,42px);
}
.sub{
color:var(--muted);
font-size:16px;
}

.frame{
border-radius:22px;
overflow:hidden;
border:1px solid var(--stroke);
}
.photo{
width:100%;
height:55vh;
max-height:520px;
object-fit:cover;
}

.actions{
position:relative;
height:95px;
display:flex;
align-items:center;
justify-content:center;
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
background:rgba(255,255,255,.2);
color:white;
}

.hidden{display:none}
.footer{
font-size:14px;
color:var(--muted);
}
</style>
</head>

<body>

<div class="hearts" id="hearts"></div>

<div class="wrap">
<div class="card">

<!-- ASK SCREEN -->
<section id="ask">
<div class="topbar">
<div class="pill">💌 For Piyush</div>
<div class="progress"><div></div></div>
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

<p class="footer">Hint: No is scared</p>
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
<p class="sub">
Congratulations Piyush 💕<br>
You are officially my Valentine.
</p>

<div class="frame">
<img src="yes.jpg" class="photo" alt="Piyush">
</div>

<p class="sub">Love, Reshma 💖</p>
</div>
</section>

</div>
</div>

<script>
const noBtn=document.getElementById("noBtn");
const yesBtn=document.getElementById("yesBtn");
const arena=document.getElementById("arena");
const ask=document.getElementById("ask");
const yes=document.getElementById("yes");

const phrases=[
"No 🙅‍♂️",
"Piyush pls 😭",
"Wrong answer 😌",
"Try again 🙂",
"Nice try 😏",
"Just press Yes 💖"
];
let count=0;

function moveNo(){
const maxX=arena.offsetWidth-noBtn.offsetWidth-10;
const maxY=arena.offsetHeight-noBtn.offsetHeight-10;
noBtn.style.left=Math.random()*maxX+"px";
noBtn.style.top=Math.random()*maxY+"px";
noBtn.textContent=phrases[Math.min(count++,phrases.length-1)];
}

["mouseenter","mouseover","touchstart"].forEach(e=>{
noBtn.addEventListener(e,ev=>{
ev.preventDefault();
moveNo();
});
});

noBtn.onclick=()=>showYes();
yesBtn.onclick=()=>showYes();

function showYes(){
ask.classList.add("hidden");
yes.classList.remove("hidden");
confetti();
}

function confetti(){
const emojis=["💖","💘","💝","✨","🥰"];
for(let i=0;i<26;i++){
const s=document.createElement("span");
s.textContent=emojis[Math.floor(Math.random()*emojis.length)];
s.style.position="fixed";
s.style.left=Math.random()*100+"vw";
s.style.top="-20px";
s.style.fontSize=16+Math.random()*24+"px";
s.style.animation="fall 1.6s ease forwards";
document.body.appendChild(s);
setTimeout(()=>s.remove(),1600);
}
}

setInterval(()=>{
const h=document.createElement("div");
h.className="heart";
h.textContent=["💗","💖","💘","✨"][Math.floor(Math.random()*4)];
h.style.left=Math.random()*100+"vw";
h.style.animationDuration=6+Math.random()*6+"s";
document.getElementById("hearts").appendChild(h);
setTimeout(()=>h.remove(),12000);
},420);
</script>

</body>
</html>
