# ngocthuyah
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<title>Thiệp 20/11 - PECREW</title>
<style>
body {
    margin: 0;
    padding: 0;
    background: linear-gradient(to bottom, #fff8f0, #ffe6e0);
    font-family: 'Arial', sans-serif;
    overflow: hidden;
    text-align: center;
}

h1 {
    margin-top: 20px;
    color: #e67e22;
}

#envelope {
    width: 400px;
    height: 200px;
    margin: 50px auto;
    background-color: #fde3e0;
    border: 2px solid #f99;
    border-radius: 10px;
    position: relative;
    cursor: pointer;
    transition: all 1s ease;
}

#flap {
    width: 400px;
    height: 100px;
    background-color: #f99;
    position: absolute;
    top: 0;
    left: 0;
    clip-path: polygon(0 0, 50% 100%, 100% 0);
    transition: transform 1s;
    z-index: 2;
}

#letter {
    opacity: 0;
    margin-top: 120px;
    transition: opacity 2s;
    position: relative;
    z-index: 1;
    background: rgba(255, 255, 255, 0.85);
    padding: 20px;
    border-radius: 10px;
}

#message p {
    margin: 10px 0;
    font-size: 16px;
    color: #c0392b;
}

.flower {
    font-size: 30px;
    color: #ff69b4;
}

#footer {
    position: absolute;
    bottom: 10px;
    width: 100%;
    font-size: 14px;
    color: #d35400;
}

/* Hiệu ứng hoa rơi */
.petal {
    position: absolute;
    font-size: 28px;
    color: #ff6eb4;
    animation: fall linear infinite;
}

@keyframes fall {
    0% {transform: translateY(-50px) rotate(0deg); opacity:1;}
    100% {transform: translateY(850px) rotate(360deg); opacity:0;}
}
</style>
</head>
<body>

<h1>Thiệp Tri Ân 20/11</h1>

<div id="envelope" onclick="openEnvelope()">
    <div id="flap"></div>
    <div id="letter">
        <p class="flower">🌸🌿🌼</p>
        <div id="message"></div>
        <p class="flower">🌼🌿🌸</p>
    </div>
</div>

<div id="footer">Câu lạc bộ PECREW</div>

<script>
const message = [
    "Kính gửi tất cả giảng viên trường Cao đẳng FPT Polytechnic,",
    "Đặc biệt các thầy cô bộ môn Kinh tế,",
    "Chúc thầy cô luôn là người dẫn dắt, truyền cảm hứng tri thức và niềm đam mê học tập cho sinh viên.",
    "Cảm ơn thầy cô đã cống hiến, dìu dắt và gieo mầm kiến thức quý giá.",
    "Câu lạc bộ PECREW xin gửi lời tri ân sâu sắc nhân ngày Nhà giáo Việt Nam 20/11!"
];

function typeWriter(text, i, callback) {
    if (i < text.length) {
        document.getElementById("message").innerHTML += text.charAt(i);
        setTimeout(function() {
            typeWriter(text, i + 1, callback)
        }, 40);
    } else {
        document.getElementById("message").innerHTML += "<br><br>";
        if (callback) callback();
    }
}

function displayMessage(lines, index = 0) {
    if (index < lines.length) {
        typeWriter(lines[index], 0, function() {
            displayMessage(lines, index + 1);
        });
    }
}

function openEnvelope() {
    document.getElementById("flap").style.transform = "rotateX(180deg)";
    setTimeout(function() {
        document.getElementById("letter").style.opacity = 1;
        displayMessage(message);
    }, 1000);
}

// Tạo hiệu ứng hoa rơi
function createPetal() {
    const petal = document.createElement("div");
    petal.className = "petal";
    petal.style.left = Math.random() * window.innerWidth + "px";
    petal.style.animationDuration = 3 + Math.random() * 3 + "s";
    petal.innerText = "🌸";
    document.body.appendChild(petal);
    setTimeout(() => petal.remove(), 6000);
}
setInterval(createPetal, 300);
</script>

</body>
</html>
