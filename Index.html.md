<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8">  
  <title>Valentine 💖</title>  
  <style>  
    body {  
      margin: 0;  
      height: 100vh;  
      display: flex;  
      flex-direction: column;  
      align-items: center;  
      justify-content: center;  
      background: #ffe6ea;  
      font-family: Arial, sans-serif;  
      overflow: hidden;  
      text-align: center;  
    }  
  
    h1 {  
      margin-bottom: 30px;  
    }  
  
    button {  
      font-size: 20px;  
      padding: 12px 25px;  
      margin: 10px;  
      border: none;  
      border-radius: 10px;  
      cursor: pointer;  
    }  
  
    #yes {  
      background-color: #ff4d6d;  
      color: white;  
      z-index: 2;  
    }  
  
    #no {  
      position: absolute;  
      background-color: #ccc;  
      z-index: 2;  
    }  
  
    #message {  
      display: none;  
      font-size: 32px;  
      font-weight: bold;  
      color: #ff2f68;  
      z-index: 2;  
    }  
  
    canvas {  
      position: fixed;  
      top: 0;  
      left: 0;  
      z-index: 1;  
    }  
  </style>  
</head>  
<body>  
  
  <h1 id="question">Will you be my Valentine? 💘</h1>  
  
  <button id="yes">YES 💕</button>  
  <button id="no">NO 🙄</button>  
  
  <div id="message">🎆 Woohoo! You’re HUSSAIN’s Valentine 💖 🎆</div>  
  
  <canvas id="fireworks"></canvas>  
  
  <script>  
    // NO button runs away  
    const noBtn = document.getElementById("no");  
    noBtn.addEventListener("mouseover", moveNo);  
    noBtn.addEventListener("touchstart", moveNo);  
  
    function moveNo() {  
      const x = Math.random() * (window.innerWidth - 100);  
      const y = Math.random() * (window.innerHeight - 50);  
      noBtn.style.left = x + "px";  
      noBtn.style.top = y + "px";  
    }  
  
    // YES button logic  
    const yesBtn = document.getElementById("yes");  
    const question = document.getElementById("question");  
    const message = document.getElementById("message");  
  
    yesBtn.onclick = () => {  
      question.style.display = "none";  
      yesBtn.style.display = "none";  
      noBtn.style.display = "none";  
      message.style.display = "block";  
      startFireworks();  
    };  
  
    // Fireworks animation  
    const canvas = document.getElementById("fireworks");  
    const ctx = canvas.getContext("2d");  
    canvas.width = window.innerWidth;  
    canvas.height = window.innerHeight;  
  
    let particles = [];  
  
    function startFireworks() {  
      setInterval(() => {  
        const x = Math.random() * canvas.width;  
        const y = Math.random() * canvas.height / 2;  
        for (let i = 0; i < 50; i++) {  
          particles.push({  
            x,  
            y,  
            vx: (Math.random() - 0.5) * 6,  
            vy: (Math.random() - 0.5) * 6,  
            life: 60  
          });  
        }  
      }, 400);  
    }  
  
    function animate() {  
      ctx.clearRect(0, 0, canvas.width, canvas.height);  
      particles.forEach((p, i) => {  
        p.x += p.vx;  
        p.y += p.vy;  
        p.life--;  
        ctx.fillStyle = `hsl(${Math.random()*360},100%,60%)`;  
        ctx.fillRect(p.x, p.y, 3, 3);  
        if (p.life <= 0) particles.splice(i, 1);  
      });  
      requestAnimationFrame(animate);  
    }  
  
    animate();  
  </script>  
  
</body>  
</html>  
