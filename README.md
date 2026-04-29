<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>💖 رسالة خاصة</title>

<style>
body {
    margin: 0;
    font-family: Arial;
    background: linear-gradient(135deg, #ff4e8a, #ff9a8b);
    overflow: hidden;
    text-align: center;
    color: white;
}

/* البداية */
#startScreen {
    position: fixed;
    width: 100%;
    height: 100%;
    background: black;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 28px;
    z-index: 10;
}

/* المحتوى */
#main {
    display: none;
    padding-top: 70px;
}

h1 {
    font-size: 40px;
}

p {
    font-size: 20px;
}

/* الأزرار */
button {
    padding: 15px 30px;
    font-size: 18px;
    border: none;
    border-radius: 12px;
    cursor: pointer;
}

#yes {
    background: white;
    color: #ff4e8a;
}

#no {
    background: #222;
    color: white;
    position: absolute;
}

/* النهاية */
#final {
    display: none;
    font-size: 30px;
    margin-top: 30px;
    animation: pop 1s ease;
}

@keyframes pop {
    from {transform: scale(0); opacity:0;}
    to {transform: scale(1); opacity:1;}
}

/* قلوب */
.heart {
    position: absolute;
    color: red;
    animation: float 6s linear infinite;
}

@keyframes float {
    0% {transform: translateY(100vh); opacity:1;}
    100% {transform: translateY(-10vh); opacity:0;}
}

/* كونفيتي */
.confetti {
    position: absolute;
    width: 10px;
    height: 10px;
    background: yellow;
    animation: fall 3s linear forwards;
}

@keyframes fall {
    to {
        transform: translateY(100vh) rotate(720deg);
        opacity: 0;
    }
}
</style>

</head>

<body>

<div id="startScreen">💖 Loading Surprise...</div>

<div id="main">

<h1 id="title"></h1>

<p>
أنا عارف إني غلطت…  
بس إنتي أهم حد في حياتي ❤️
</p>

<button onclick="startGame()">ابدأ 💌</button>

<div id="question" style="display:none; margin-top:30px;">
    <h2>تسامحيني؟ 🥺</h2>

    <button id="yes" onclick="yes()">أيوه ❤️</button>
    <button id="no" onmouseover="runNo()">لأ 😏</button>
</div>

<div id="final">
❤️ كنت عارف إنك هتسامحيني ❤️<br><br>
حقك عليا بجد ومش هزعلك تاني 💖
</div>

</div>

<script>

// بداية
setTimeout(() => {
    document.getElementById("startScreen").style.display = "none";
    document.getElementById("main").style.display = "block";
    typeWriter("معلش يا حبيبتي 💔");
}, 2000);

// كتابة اسماء بشكل أنيميشن
function typeWriter(text) {
    let i = 0;
    let speed = 100;
    function typing() {
        if (i < text.length) {
            document.getElementById("title").innerHTML += text.charAt(i);
            i++;
            setTimeout(typing, speed);
        }
    }
    typing();
}

// بداية اللعبة
function startGame() {
    document.getElementById("question").style.display = "block";
    hearts();
}

// زر "لا" يهرب بذكاء
function runNo() {
    const btn = document.getElementById("no");
    btn.style.top = Math.random() * 80 + "vh";
    btn.style.left = Math.random() * 80 + "vw";
}

// موافقة
function yes() {
    document.getElementById("final").style.display = "block";
    confetti();
}

// قلوب
function hearts() {
    setInterval(() => {
        let h = document.createElement("div");
        h.className = "heart";
        h.innerHTML = "❤️";
        h.style.left = Math.random() * 100 + "vw";
        h.style.fontSize = (Math.random()*20+10) + "px";
        document.body.appendChild(h);
        setTimeout(()=>h.remove(),6000);
    },200);
}

// كونفيتي
function confetti() {
    for (let i = 0; i < 80; i++) {
        let c = document.createElement("div");
        c.className = "confetti";
        c.style.left = Math.random() * 100 + "vw";
        c.style.background = ["#fff","#ff0","#f0f","#0ff"][Math.floor(Math.random()*4)];
        document.body.appendChild(c);
        setTimeout(()=>c.remove(),3000);
    }
}

</script>

</body>
</html>
