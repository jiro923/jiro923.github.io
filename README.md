<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For Cesca - A Snoopy Valentine</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Comic Sans MS', 'Chalkboard SE', cursive;
        }
        
        body {
            background: linear-gradient(135deg, #fff8e1 0%, #ffebee 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            color: #333;
        }
        
        .container {
            width: 100%;
            max-width: 900px;
            padding: 20px;
            text-align: center;
            position: relative;
            z-index: 1;
        }
        
        .header {
            margin-bottom: 40px;
        }
        
        h1 {
            color: #d32f2f;
            font-size: 2.8rem;
            text-shadow: 3px 3px 0 #ffeb3b;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #d32f2f; /* Changed to plain red */
            font-size: 1.5rem;
            font-weight: bold;
            background-color: #ffeb3b;
            padding: 8px 20px;
            border-radius: 30px;
            display: inline-block;
            border: 3px solid #d32f2f;
        }
        
        .valentine-card {
            background-color: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(211, 47, 47, 0.2);
            border: 8px solid #ffeb3b;
            position: relative;
            overflow: hidden;
            margin-bottom: 40px;
        }
        
        .card-content {
            padding: 20px;
        }
        
       .snoopy-container {
    height: 250px;
    position: relative;
    margin: 30px 0;
    overflow: hidden;
    border-radius: 15px;
    background-color: #d32f2f;
    border: 5px dashed #ffeb3b;
    background-size: cover;
    background-position: center;
    background-blend-mode: multiply;
}
        .snoopy-img {
            position: absolute;
            bottom: 20px;
            left: -200px;
            width: 180px;
            height: auto;
            animation: walk 10s linear forwards;
            animation-delay: 1s;
            filter: drop-shadow(5px 5px 5px rgba(0,0,0,0.3));
        }
        
        .speech-bubble {
            position: absolute;
            top: 50px;
            left: 200px;
            background-color: white;
            padding: 15px 20px;
            border-radius: 20px;
            box-shadow: 3px 3px 0 #ffcdd2;
            border: 3px solid #d32f2f;
            max-width: 300px;
            text-align: left;
            opacity: 0;
            animation: fadeIn 0.5s forwards;
            animation-delay: 8s;
            z-index: 10;
        }
        
        .speech-bubble:after {
            content: '';
            position: absolute;
            left: -20px;
            top: 30px;
            border: 10px solid transparent;
            border-right-color: #d32f2f;
        }
        
        .speech-bubble p {
            color: #5d4037;
            font-size: 1.1rem;
            line-height: 1.4;
        }
        
        .message-box {
            margin: 30px 0;
            padding: 20px;
            background-color: #ffebee;
            border-radius: 15px;
            border-left: 8px solid #d32f2f;
        }
        
        .message-box h2 {
            color: #d32f2f;
            margin-bottom: 15px;
        }
        
        .message-box p {
            font-size: 1.2rem;
            color: #5d4037;
            line-height: 1.6;
        }
        
        .cesca-name {
            color: #d32f2f;
            font-weight: bold;
            font-size: 1.3rem;
            background-color: #ffeb3b;
            padding: 2px 8px;
            border-radius: 10px;
        }
        
        .button-container {
            margin: 40px 0;
        }
        
        .reveal-btn {
            background: linear-gradient(to right, #d32f2f, #f57c00);
            color: white;
            border: none;
            padding: 18px 40px;
            font-size: 1.4rem;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            box-shadow: 0 6px 0 #b71c1c;
            font-weight: bold;
            letter-spacing: 1px;
        }
        
        .reveal-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 0 #b71c1c;
        }
        
        .reveal-btn:active {
            transform: translateY(0);
            box-shadow: 0 3px 0 #b71c1c;
        }
        
        .proposal-container {
            display: none;
            margin-top: 40px;
            padding: 30px;
            background-color: #fffde7;
            border-radius: 20px;
            border: 5px solid #ffeb3b;
            position: relative;
            overflow: hidden;
        }
        
        .proposal-text {
            font-size: 2.5rem;
            color: #d32f2f;
            font-weight: bold;
            margin-bottom: 40px;
            text-shadow: 2px 2px 0 #ffecb3;
            animation: pulse 1.5s infinite alternate;
        }
        
        .response-buttons {
            display: flex;
            justify-content: center;
            gap: 40px;
            margin-top: 30px;
        }
        
        .response-btn {
            padding: 18px 50px;
            font-size: 1.8rem;
            border: none;
            border-radius: 15px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
            box-shadow: 0 6px 0 rgba(0,0,0,0.2);
        }
        
        .yes-btn {
            background-color: #4caf50;
            color: white;
        }
        
        .no-btn {
            background-color: #f44336;
            color: white;
        }
        
        .response-btn:hover {
            transform: scale(1.1);
        }
        
        .playlist-container {
            display: none;
            margin-top: 40px;
            padding: 30px;
            background-color: #e8f5e9;
            border-radius: 20px;
            border: 5px solid #4caf50;
        }
        
        .playlist-title {
            color: #2e7d32;
            font-size: 2rem;
            margin-bottom: 20px;
        }
        
        .playlist-description {
            color: #5d4037;
            font-size: 1.2rem;
            margin-bottom: 30px;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }
        
        .qr-code {
            width: 200px;
            height: 200px;
            margin: 20px auto;
            padding: 15px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            background: white url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjAwIiBoZWlnaHQ9IjIwMCIgdmlld0JveD0iMCAwIDI0IDI0IiBmaWxsPSJub25lIiBzdHJva2U9IiMxREI5NTQiIHN0cm9rZS13aWR0aD0iMiIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIj48cGF0aCBkPSJNMTIgMTMuNWMxLjEgMCAyLS45IDItMnMtLjktMi0yLTItMiAuOS0yIDIgLjkgMiAyIDJ6Ii8+PHBhdGggZD0iTTIwIDkuM1Y3YTIgMiAwIDAgMC0yLTJoLTEuOU0xNSAydDItMmgyYTIgMiAwIDAgMSAyIDJ2MS45TTkgMjJINC4xYTIuMSAyLjEgMCAxIDEgMC00LjJINS45TTIyIDEydjIuOWEyLjEgMi4xIDAgMSAxLTQuMiAwVjE5TTIgMTJINC4xYTIuMSAyLjEgMCAxIDAgMCA0LjJIMk0xOSAyMmEyIDIgMCAwIDAgMi0ydi0xLjkiLz48L3N2Zz4=') center/60% no-repeat;
        }
        
        .spotify-link {
            display: inline-block;
            margin-top: 20px;
            padding: 12px 25px;
            background-color: #1db954;
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: all 0.3s;
        }
        
        .spotify-link:hover {
            background-color: #1ed760;
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(29, 185, 84, 0.4);
        }
        
        .heart {
            position: absolute;
            color: #ff5252;
            font-size: 20px;
            opacity: 0;
            z-index: 0;
        }
        
        .firework {
            position: absolute;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            z-index: 0;
            pointer-events: none;
        }
        
        .footer {
            margin-top: 40px;
            color: #d32f2f; /* Changed to red */
            font-size: 1.1rem;
            padding: 20px;
            border-top: 3px dotted #ffeb3b;
            background-color: #fff8e1;
            border-radius: 15px;
        }
        
        @keyframes walk {
            0% { 
                left: -200px;
                transform: scaleX(1);
            }
            30% { 
                left: 30%;
                transform: scaleX(1);
            }
            50% {
                transform: scaleX(1);
            }
            51% {
                transform: scaleX(-1);
            }
            70% { 
                left: 60%;
                transform: scaleX(-1);
            }
            100% { 
                left: calc(100% - 180px);
                transform: scaleX(1);
            }
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes pulse {
            from { transform: scale(1); }
            to { transform: scale(1.05); }
        }
        
        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-1000px) rotate(720deg); opacity: 0; }
        }
        
        @keyframes explode {
            0% { transform: scale(1); opacity: 1; }
            100% { transform: scale(20); opacity: 0; }
        }
        
        .footprint {
            position: absolute;
            bottom: 20px;
            width: 30px;
            height: 15px;
            background-color: rgba(255, 255, 255, 0.7);
            border-radius: 50%;
            opacity: 0;
        }
        
        @media (max-width: 768px) {
            h1 { font-size: 2.2rem; }
            .proposal-text { font-size: 1.8rem; }
            .response-buttons { flex-direction: column; gap: 20px; }
            .response-btn { padding: 15px 30px; }
            .snoopy-container { height: 200px; }
            .snoopy-img { width: 150px; }
            .speech-bubble {
                max-width: 250px;
                left: 150px;
                top: 30px;
            }
        }
        
        @media (max-width: 480px) {
            .snoopy-img { width: 120px; }
            .speech-bubble {
                max-width: 200px;
                left: 100px;
                top: 20px;
                padding: 10px 15px;
            }
            .speech-bubble p { font-size: 1rem; }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1><i class="fas fa-heart"></i> A Snoopy Valentine <i class="fas fa-heart"></i></h1>
            <div class="subtitle">For someone very special...</div>
        </div>
        
        <div class="valentine-card">
            <div class="snoopy-container">
                <!-- Working Snoopy Image -->
                <img src="https://www.pngmart.com/files/22/Snoopy-PNG-Isolated-HD.png" alt="Snoopy" class="snoopy-img" id="snoopyImage">
                <div class="speech-bubble">
                    <p>Hello <span class="cesca-name">Cesca</span>, I really had a great time with you today. Thank you for this wonderful Valentine's Day!</p>
                </div>
            </div>
            
            <div class="card-content">
                <div class="message-box">
                    <h2><i class="fas fa-gift"></i> A Special Message</h2>
                    <p>This Valentine's Day, I wanted to do something special to show you how much you mean to me. You make every day brighter and every moment more meaningful.</p>
                </div>
                
                <div class="button-container">
                    <button class="reveal-btn" id="revealBtn">
                        <i class="fas fa-fireworks"></i> Click for a Surprise! <i class="fas fa-fireworks"></i>
                    </button>
                </div>
                
                <div class="proposal-container" id="proposalContainer">
                    <div class="proposal-text">Will you be my girlfriend?</div>
                    <div class="response-buttons">
                        <button class="response-btn yes-btn" id="yesBtn">YES! <i class="fas fa-heart"></i></button>
                        <button class="response-btn no-btn" id="noBtn">No</button>
                    </div>
                </div>
                
                <div class="playlist-container" id="playlistContainer">
                    <h2 class="playlist-title"><i class="fab fa-spotify"></i> For You: Our Playlist</h2>
                    <p class="playlist-description">I've put together a collection of songs that remind me of you and our special moments together. Scan the QR code or click the link below to listen!</p>
                    
                    <div class="qr-code"></div>
                    
                    <a href="https://open.spotify.com/playlist/6FF9QQMTbt2tVxKWy1cj4Q?si=a58c552501ef46f0" target="_blank" class="spotify-link">
                        <i class="fab fa-spotify"></i> Open Our Playlist in Spotify
                    </a>
                </div>
            </div>
        </div>
        
        <div class="footer">
            Made with <i class="fas fa-heart" style="color: #d32f2f;"></i> 2/14/26
        </div>
    </div>

    <script>
        const revealBtn = document.getElementById('revealBtn');
        const proposalContainer = document.getElementById('proposalContainer');
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const playlistContainer = document.getElementById('playlistContainer');
        const snoopyImage = document.getElementById('snoopyImage');
        
        function createHearts() {
            const container = document.querySelector('.container');
            for (let i = 0; i < 25; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.innerHTML = '<i class="fas fa-heart"></i>';
                heart.style.left = Math.random() * 100 + 'vw';
                heart.style.top = Math.random() * 100 + 'vh';
                heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
                heart.style.opacity = Math.random() * 0.5 + 0.1;
                heart.style.animation = `float ${Math.random() * 10 + 10}s linear infinite`;
                heart.style.animationDelay = Math.random() * 5 + 's';
                container.appendChild(heart);
            }
        }
        
        function createFootprints() {
            const container = document.querySelector('.snoopy-container');
            const positions = [10, 25, 40, 55, 70, 85];
            
            positions.forEach(pos => {
                const footprint = document.createElement('div');
                footprint.className = 'footprint';
                footprint.style.left = `${pos}%`;
                
                if (pos % 20 === 0) {
                    footprint.style.transform = 'scaleX(-1)';
                }
                
                container.appendChild(footprint);
                
                setTimeout(() => {
                    footprint.style.opacity = '0.7';
                    setTimeout(() => {
                        footprint.style.opacity = '0';
                    }, 3000);
                }, (pos / 10) * 1000);
            });
        }
        
        function createFireworks() {
            const container = document.querySelector('.container');
            const colors = ['#ff5252', '#ffeb3b', '#4caf50', '#2196f3', '#9c27b0'];
            
            for (let i = 0; i < 50; i++) {
                const firework = document.createElement('div');
                firework.className = 'firework';
                firework.style.left = Math.random() * 100 + 'vw';
                firework.style.top = Math.random() * 100 + 'vh';
                firework.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                firework.style.boxShadow = `0 0 10px ${firework.style.backgroundColor}`;
                container.appendChild(firework);
                
                setTimeout(() => {
                    firework.style.animation = `explode ${Math.random() * 0.5 + 0.5}s forwards`;
                }, Math.random() * 1000);
                
                setTimeout(() => firework.remove(), 1500);
            }
        }
        
        function createConfetti() {
            const container = document.querySelector('.container');
            const confettiColors = ['#d32f2f', '#ffeb3b', '#4caf50', '#2196f3', '#ffffff'];
            
            for (let i = 0; i < 150; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'heart';
                confetti.innerHTML = '<i class="fas fa-heart"></i>';
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.top = '-20px';
                confetti.style.color = confettiColors[Math.floor(Math.random() * confettiColors.length)];
                confetti.style.fontSize = (Math.random() * 15 + 10) + 'px';
                confetti.style.opacity = Math.random() * 0.7 + 0.3;
                container.appendChild(confetti);
                
                const animationDuration = Math.random() * 3 + 2;
                confetti.style.animation = `float ${animationDuration}s linear forwards`;
                setTimeout(() => confetti.remove(), animationDuration * 1000);
            }
        }
        
        function startSnoopyAnimation() {
            snoopyImage.style.left = '-200px';
            snoopyImage.style.animation = 'walk 10s linear forwards';
            snoopyImage.style.animationDelay = '1s';
            
            setTimeout(createFootprints, 1500);
            
            setTimeout(() => {
                snoopyImage.style.animation = 'none';
                snoopyImage.style.animation = 'pulse 1s infinite alternate';
            }, 11000);
        }
        
        revealBtn.addEventListener('click', function() {
            revealBtn.style.display = 'none';
            proposalContainer.style.display = 'block';
            proposalContainer.style.animation = 'fadeIn 1s forwards';
            
            createFireworks();
            setTimeout(createConfetti, 500);
            setTimeout(createFireworks, 1000);
            
            snoopyImage.style.animation = 'pulse 0.5s infinite alternate';
        });
        
        yesBtn.addEventListener('click', function() {
            createFireworks();
            createConfetti();
            
            proposalContainer.style.display = 'none';
            playlistContainer.style.display = 'block';
            playlistContainer.style.animation = 'fadeIn 1s forwards';
            
            setTimeout(createFireworks, 300);
            setTimeout(createConfetti, 600);
            setTimeout(createFireworks, 900);
        });
        
        noBtn.addEventListener('click', function() {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            
            noBtn.style.position = 'absolute';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
            
            yesBtn.style.transform = 'scale(1.2)';
            yesBtn.style.transition = 'transform 0.3s';
            
            alert("Just kidding! You have to click YES! 😉");
        });
        
        window.addEventListener('DOMContentLoaded', function() {
            createHearts();
            startSnoopyAnimation();
            window.scrollTo(0, 0);
            
            snoopyImage.addEventListener('click', function() {
                createConfetti();
                snoopyImage.style.transform = 'scale(1.2)';
                setTimeout(() => snoopyImage.style.transform = 'scale(1)', 300);
            });
        });
    </script>
</body>
</html>
