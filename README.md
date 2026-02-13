
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Skylor 💗</title>

<style>
* { margin:0; padding:0; box-sizing:border-box; }

body {
    height:100vh;
    font-family:-apple-system, BlinkMacSystemFont, sans-serif;
    background: linear-gradient(145deg,#f8c8dc,#a3b18a);
    display:flex;
    justify-content:center;
    align-items:center;
    overflow:hidden;
}

/* Romantic glow overlay */
body::after {
    content:"";
    position:fixed;
    width:100%;
    height:100%;
    background:radial-gradient(circle at center,rgba(255,255,255,0.1),rgba(0,0,0,0.35));
    pointer-events:none;
}

/* App Card */
.app {
    width:95%;
    max-width:420px;
    padding:35px;
    border-radius:30px;
    background:rgba(255,255,255,0.15);
    backdrop-filter:blur(25px);
    box-shadow:0 30px 60px rgba(0,0,0,0.3);
    text-align:center;
    color:white;
    position:relative;
}

h1 {
    font-size:1.8rem;
    margin-bottom:20px;
    cursor:pointer;
}

#message {
    font-size:1.1rem;
    min-height:90px;
    margin-bottom:25px;
    line-height:1.6;
}

/* Buttons */
.buttons { position:relative; height:80px; }

button {
    padding:12px 24px;
    border:none;
    border-radius:30px;
    font-size:1rem;
    cursor:pointer;
    transition:0.3s;
}

#yesBtn {
    background:#ff6fa5;
    color:white;
    margin-right:10px;
}

#noBtn {
    background:#7c9a7a;
    color:white;
}

/* Music button */
#musicBtn {
    position:absolute;
    top:15px;
    right:15px;
    background:rgba(255,255,255,0.2);
    font-size:0.8rem;
}

/* Roses */
.rose {
    position:absolute;
    top:-10vh;
    font-size:22px;
    animation:fall linear infinite;
    opacity:0.8;
}

@keyframes fall {
    to {
        transform:translateY(110vh) rotate(360deg);
    }
}

/* Confetti */
.confetti {
    position:absolute;
    width:8px;
    height:8px;
    background:white;
    animation:confettiFall 2s linear forwards;
}

@keyframes confettiFall {
    to {
        transform:translateY(300px) rotate(720deg);
        opacity:0;
    }
}

@media(min-width:700px){
    .app { max-width:500px; padding:45px; }
}
</style>
</head>

<body>

<div class="app">
    <button id="musicBtn">🎵 Play Music</button>
    <h1 id="title">Skylor 🌹</h1>
    <div id="message"></div>

    <div class="buttons">
        <button id="yesBtn">Yes 💕</button>
        <button id="noBtn">No 😏</button>
    </div>
</div>

<audio id="bgMusic" loop>
    <source src="brent.mp3" type="audio/mpeg">
</audio>


<script>

/* Typing Effect */
const text = "I would Lowkeniunely be honored to be your Valentine. Highkey tho in real way. 🥹💗 Will you be mine?";
let i = 0;
function typeWriter(){
    if(i < text.length){
        document.getElementById("message").innerHTML += text.charAt(i);
        i++;
        setTimeout(typeWriter, 35);
    }
}
typeWriter();

/* Music Toggle */
const music = document.getElementById("bgMusic");
const musicBtn = document.getElementById("musicBtn");

musicBtn.addEventListener("click",()=>{
    if(music.paused){
        music.play();
        musicBtn.innerText="🎵 Pause Music";
    } else {
        music.pause();
        musicBtn.innerText="🎵 Play Music";
    }
});

/* No button shrink */
const noBtn = document.getElementById("noBtn");
let scale = 1;
noBtn.addEventListener("click",()=>{
    scale -= 0.2;
    noBtn.style.transform=`scale(${scale})`;
    if(scale <= 0){
        noBtn.style.display="none";
    }
});

yesBtn.addEventListener("click",()=>{
    for(let j=0;j<80;j++){
        const confetti=document.createElement("div");
        confetti.classList.add("confetti");
        confetti.style.left=Math.random()*100+"%";
        confetti.style.background=Math.random()>0.5?"#ff6fa5":"#a3b18a";
        document.body.appendChild(confetti);
        setTimeout(()=>confetti.remove(),2000);
    }

    document.querySelector(".app").innerHTML=`
        <h1>You said YES 😭💖</h1>
        <p style="margin-top:20px;font-size:1.2rem;">
       Happy Valentines pretty lady! Thanks for sticking with me!
        </p>
    `;
});


/* Elegant Roses */
function createRose(){
    const rose=document.createElement("div");
    rose.classList.add("rose");
    rose.innerHTML="🌹";
    rose.style.left=Math.random()*100+"vw";
    rose.style.animationDuration=(10+Math.random()*6)+"s";
    document.body.appendChild(rose);
    setTimeout(()=>rose.remove(),16000);
}
setInterval(createRose,1200);

/* Hidden Easter Egg */
let tapCount=0;
document.getElementById("title").addEventListener("click",()=>{
    tapCount++;
    if(tapCount===5){
        alert("Inside joke unlocked 😌 You already knew the answer.");
    }
});
</script>

</body>
</html>
