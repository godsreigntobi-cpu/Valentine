# Valentine<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>For Serena ❤️</title>

<style>
body{
    margin:0;
    height:100vh;
    overflow:hidden;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#ff9a9e,#fad0c4);
    font-family:Arial;
    text-align:center;
}

.container{
    background:white;
    padding:40px;
    border-radius:20px;
    box-shadow:0 10px 30px rgba(0,0,0,0.2);
    z-index:2;
}

h1{color:#ff4d6d;}

button{
    padding:15px 30px;
    font-size:18px;
    border:none;
    border-radius:12px;
    cursor:pointer;
    margin:10px;
}

#yes{
    background:#ff4d6d;
    color:white;
}

#no{
    background:#999;
    color:white;
    position:relative;
}

/* Floating hearts */
.heart{
    position:absolute;
    color:red;
    font-size:20px;
    animation: float 6s linear infinite;
}

@keyframes float{
    0%{transform:translateY(100vh);}
    100%{transform:translateY(-10vh);}
}
</style>
</head>

<body>

<audio autoplay loop>
<source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3" type="audio/mp3">
</audio>

<div class="container" id="mainBox">
    <h1 id="typing"></h1>
    <div id="buttons" style="display:none;">
        <button id="yes" onclick="sayYes()">Yes 💖</button>
        <button id="no">No 😢</button>
    </div>
</div>

<script>

// ===== FLOATING HEARTS =====
function createHeart(){
    let heart=document.createElement("div");
    heart.className="heart";
    heart.innerHTML="❤️";
    heart.style.left=Math.random()*100+"vw";
    heart.style.fontSize=(Math.random()*20+10)+"px";
    document.body.appendChild(heart);

    setTimeout(()=>heart.remove(),6000);
}
setInterval(createHeart,300);


// ===== TYPING INTRO =====
let message="Serena... I have something important to ask you ❤️";
let i=0;

function typeText(){
    if(i<message.length){
        document.getElementById("typing").innerHTML+=message.charAt(i);
        i++;
        setTimeout(typeText,60);
    }else{
        countdown();
    }
}
typeText();


// ===== COUNTDOWN =====
function countdown(){
    let count=3;
    let box=document.getElementById("typing");

    let timer=setInterval(()=>{
        box.innerHTML="Get ready... "+count+" ❤️";
        count--;

        if(count<0){
            clearInterval(timer);
            showQuestion();
        }
    },1000);
}


// ===== SHOW QUESTION =====
function showQuestion(){
    document.getElementById("typing").innerHTML="Serena, will you be my Valentine? ❤️";
    document.getElementById("buttons").style.display="block";
}


// ===== RUNNING NO BUTTON =====
let noBtn=document.getElementById("no");

function moveNo(){
    let x=Math.random()*(window.innerWidth-100);
    let y=Math.random()*(window.innerHeight-50);

    noBtn.style.position="absolute";
    noBtn.style.left=x+"px";
    noBtn.style.top=y+"px";
}

noBtn.addEventListener("mouseover",moveNo);
noBtn.addEventListener("click",moveNo);


// ===== CONFETTI + YES SCREEN =====
function sayYes(){

    // Confetti
    for(let i=0;i<120;i++){
        let conf=document.createElement("div");
        conf.innerHTML="🎉";
        conf.style.position="absolute";
        conf.style.left=Math.random()*100+"vw";
        conf.style.top="-10px";
        conf.style.fontSize="25px";
        conf.style.animation="fall 3s linear";
        document.body.appendChild(conf);

        setTimeout(()=>conf.remove(),3000);
    }

    document.body.innerHTML=`
    <style>
    @keyframes fall{
        to{transform:translateY(100vh);}
    }
    </style>

    <div style="display:flex;justify-content:center;align-items:center;height:100vh;background:linear-gradient(135deg,#ff9a9e,#fad0c4);text-align:center;">
        <div>
            <h1 style="color:white;font-size:55px;">YAYYYY SERENA ❤️</h1>
            <p style="color:white;font-size:28px;">
            You just made Toby the happiest person alive 😍💖
            </p>
        </div>
    </div>
    `;
}

</script>
</body>
