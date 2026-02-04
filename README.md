<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>Soa 💖 Ma Valentine</title>

<style>
body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(135deg, #ff758c, #ff7eb3);
    overflow: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: Arial, sans-serif;
}

.box {
    background: white;
    padding: 40px;
    border-radius: 25px;
    text-align: center;
    box-shadow: 0 15px 40px rgba(0,0,0,0.3);
    z-index: 2;
}

h1 {
    color: #ff4d6d;
}

.cat {
    width: 200px;
    margin: 15px 0;
    border-radius: 15px;
}

/* Boutons */
.buttons {
    margin-top: 20px;
    position: relative;
    height: 120px;
}

button {
    padding: 15px 30px;
    font-size: 18px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
}

#yes {
    background: #ff4d6d;
    color: white;
}

#no {
    background: #ddd;
    position: absolute;
}

/* Cœurs qui tombent */
.heart {
    position: absolute;
    color: rgba(255,255,255,0.8);
    font-size: 20px;
    animation: fall linear forwards;
    pointer-events: none;
}

@keyframes fall {
    0% { transform: translateY(-10vh) scale(1); opacity: 1; }
    100% { transform: translateY(110vh) scale(0.5); opacity: 0; }
}

/* Explosion de cœurs */
.explosion {
    position: absolute;
    font-size: 30px;
    animation: boom 1s ease-out forwards;
    pointer-events: none;
}

@keyframes boom {
    0% { transform: scale(0); opacity: 1; }
    100% { transform: scale(1.5) translate(var(--x), var(--y)); opacity: 0; }
}
</style>
</head>

<body>

<div class="box">
    <h1>Soa, veux-tu être ma Valentine ? 💖</h1>

    <!-- Chat avec bague au départ -->
    <img class="cat" id="cat" src="https://media.giphy.com/media/v6aOjy0Qo1fIA/giphy.gif">

    <div class="buttons">
        <button id="yes" onclick="yesClick()">Oui 💘</button>
        <button id="no" onmouseover="moveNo()">Non 💔</button>
    </div>

    <p id="message"></p>
</div>

<script>
function moveNo() {
    let noBtn = document.getElementById("no");
    let container = document.querySelector(".buttons");

    let maxX = container.clientWidth - noBtn.offsetWidth;
    let maxY = container.clientHeight - noBtn.offsetHeight;

    noBtn.style.left = Math.random() * maxX + "px";
    noBtn.style.top = Math.random() * maxY + "px";
}

function yesClick() {
    document.getElementById("message").innerHTML =
        "💖 OUIII Soa !!! Tu viens de me rendre la personne la plus heureuse du monde 😍";

    // Changer le chat
    document.getElementById("cat").src =
        "https://media.giphy.com/media/MDJ9IbxxvDUQM/giphy.gif";

    // Lancer la musique via YouTube (autoplay après clic)
    let musicFrame = document.createElement("iframe");
    musicFrame.width = "0";
    musicFrame.height = "0";
    musicFrame.src = "https://www.youtube.com/embed/wLv_vODhxcQ?autoplay=1&loop=1&playlist=wLv_vODhxcQ";
    musicFrame.frameBorder = "0";
    musicFrame.allow = "autoplay; encrypted-media";
    document.body.appendChild(musicFrame);

    // Explosion de cœurs
    for (let i = 0; i < 40; i++) {
        let heart = document.createElement("div");
        heart.classList.add("explosion");
        heart.innerHTML = "❤";
        heart.style.left = "50%";
        heart.style.top = "50%";
        heart.style.setProperty("--x", (Math.random() * 500 - 250) + "px");
        heart.style.setProperty("--y", (Math.random() * 500 - 250) + "px");
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 1000);
    }
}

/* Pluie de cœurs en fond */
setInterval(() => {
    let heart = document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML = "❤";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = (10 + Math.random() * 30) + "px";
    heart.style.animationDuration = (3 + Math.random() * 5) + "s";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 8000);
}, 300);
</script>

</body>
</html>
