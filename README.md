# Valentine-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Valentine 💖</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins&family=Dancing+Script:wght@700&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box;margin:0;padding:0}

body{
height:100vh;
font-family:Poppins,sans-serif;
background:linear-gradient(135deg,#ffd1dc,#ff5f8a);
overflow:hidden;
display:flex;
justify-content:center;
align-items:center;
text-align:center;
}

.container{
z-index:2;
padding:20px;
}

.bear{
font-size:60px;
animation:bounce 1.2s infinite;
}

@keyframes bounce{
0%,100%{transform:translateY(0)}
50%{transform:translateY(-15px)}
}

h1{
font-family:"Dancing Script",cursive;
font-size:42px;
color:#b4003c;
margin:15px 0;
}

.subtitle{
font-style:italic;
color:#7a0028;
margin-bottom:15px;
}

.buttons{
display:flex;
justify-content:center;
gap:40px;
margin-top:25px;
}

#yesBtn{
padding:15px 35px;
border:none;
border-radius:40px;
background:linear-gradient(45deg,#ff0033,#ff5f5f);
color:white;
font-size:20px;
cursor:pointer;
box-shadow:0 0 10px #ff0033;
transition:.3s;
}

#yesBtn:hover{
box-shadow:0 0 25px #ff0033;
transform:scale(1.05);
}

#noBtn{
padding:10px 25px;
border-radius:30px;
background:white;
border:2px solid red;
color:red;
cursor:pointer;
position:fixed;
}

.heart{
position:fixed;
bottom:-50px;
animation:float linear infinite;
opacity:0;
}

@keyframes float{
0%{transform:translateY(0);opacity:0}
10%{opacity:1}
90%{opacity:1}
100%{transform:translateY(-110vh);opacity:0}
}

#celebrate{
display:none;
position:fixed;
inset:0;
background:linear-gradient(135deg,#ff8fb1,#ff3366);
justify-content:center;
align-items:center;
flex-direction:column;
z-index:10;
color:white;
}

#yay{
font-size:70px;
animation:pulse 1s infinite;
}

@keyframes pulse{
0%,100%{transform:scale(1)}
50%{transform:scale(1.2)}
}

.spin{
font-size:60px;
animation:spin 2s linear infinite;
}

@keyframes spin{
to{transform:rotate(360deg)}
}

.confetti{
position:fixed;
width:8px;
height:8px;
top:50%;
left:50%;
}

.message{
margin-top:20px;
font-size:22px;
}
</style>
</head>

<body>

<div class="container" id="main">

<div class="bear">🐻</div>

<h1>Will You Be My Valentine, <span id="name">Your Name</span>?</h1>

<div class="subtitle" id="subtitle">
I've been gathering courage to ask you this...
</div>

<div>Every love story is beautiful, but ours is my favourite</div>

<div class="buttons">
<button id="yesBtn">Yes</button>
<button id="noBtn">No</button>
</div>

</div>

<div id="celebrate">
<div id="yay">Yayyyy!!</div>
<div class="spin">💃</div>
<div class="message" id="yesMessage">I knew you'd say yes...</div>
</div>

<script>
// ===== CUSTOMIZE HERE =====
document.getElementById(" Parshant").innerText = "Rana Ji ";
document.getElementById("subtitle").innerText = "From the moment I met you, my heart knew...";
document.getElementById("yesMessage").innerText = "I knew you'd say yes, my love 💖";
// =========================

const hearts=[];
for(let i=0;i<15;i++)createHeart();

function createHeart(){
const h=document.createElement("div");
h.className="heart";
h.innerText="💖";
resetHeart(h);
document.body.appendChild(h);
hearts.push(h);
}

function resetHeart(h){
const size=20+Math.random()*30;
h.style.fontSize=size+"px";
h.style.left=Math.random()*100+"vw";
h.style.animationDuration=5+Math.random()*6+"s";
}

const noBtn=document.getElementById("noBtn");
const yesBtn=document.getElementById("yesBtn");

const msgs=["Nope, not an option!","Try again!","You sure about that?","Not happening!","Think again!"];
let msgIndex=0;

function moveNo(){
const yesRect=yesBtn.getBoundingClientRect();
let x,y;

do{
x=Math.random()*(window.innerWidth-100);
y=Math.random()*(window.innerHeight-50);
}while(
x>yesRect.left-80 &&
x<yesRect.right+80 &&
y>yesRect.top-80 &&
y<yesRect.bottom+80
);

noBtn.style.left=x+"px";
noBtn.style.top=y+"px";
noBtn.innerText=msgs[msgIndex++%msgs.length];
}

noBtn.addEventListener("mouseover",moveNo);
noBtn.addEventListener("click",moveNo);
noBtn.addEventListener("touchstart",moveNo);

yesBtn.onclick=()=>{
document.getElementById("main").style.display="none";
hearts.forEach(h=>h.remove());
document.getElementById("celebrate").style.display="flex";
confetti();
};

function confetti(){
for(let i=0;i<120;i++){
const c=document.createElement("div");
c.className="confetti";
c.style.background=`hsl(${Math.random()*360},100%,50%)`;
document.body.appendChild(c);

const angle=Math.random()*2*Math.PI;
const dist=200+Math.random()*300;

c.animate([
{transform:"translate(-50%,-50%)"},
{transform:`translate(${Math.cos(angle)*dist}px,${Math.sin(angle)*dist}px)`}
],{duration:2000,easing:"ease-out"});
}
}
</script>

</body>
</html>. 
