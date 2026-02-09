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
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 800px;
            text-align: center;
        }
        
        .header {
            margin-bottom: 30px;
        }
        
        h1 {
            color: #d32f2f;
            font-size: 2.5rem;
            text-shadow: 3px 3px 0 #ffeb3b;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #d32f2f;
            font-size: 1.3rem;
            font-weight: bold;
            background-color: #ffeb3b;
            padding: 8px 20px;
            border-radius: 30px;
            display: inline-block;
            border: 3px solid #d32f2f;
        }
        
        /* BOX 1: Snoopy Box */
        .snoopy-box {
            background-color: #d32f2f;
            border-radius: 15px;
            border: 5px dashed #ffeb3b;
            height: 250px;
            position: relative;
            margin-bottom: 30px;
            overflow: hidden;
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
        
        .cesca-name {
            color: #d32f2f;
            font-weight: bold;
            font-size: 1.3rem;
            background-color: #ffeb3b;
            padding: 2px 8px;
            border-radius: 10px;
        }
        
        /* BOX 2: Message Box */
        .message-box {
            background-color: #ffebee;
            border-radius: 15px;
            border-left: 8px solid #d32f2f;
            padding: 25px;
            margin-bottom: 30px;
            text-align: left;
        }
        
        .message-box h2 {
            color: #d32f2f;
            margin-bottom: 15px;
            font-size: 1.8rem;
        }
        
        .message-box p {
            font-size: 1.2rem;
            color: #5d4037;
            line-height: 1.6;
        }
        
        /* BOX 3: Gift Box */
        .gift-box {
            background-color: #d32f2f;
            border-radius: 15px;
            height: 200px;
            position: relative;
            margin-bottom: 30px;
            cursor: pointer;
            overflow: hidden;
        }
        
        .gift-lid {
            width: 100%;
            height: 60px;
            background-color: #b71c1c;
            position: absolute;
            top: 0;
            left: 0;
            transition: all 0.8s ease;
            border-radius: 15px 15px 0 0;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 1.3rem;
            font-weight: bold;
        }
        
        .gift-lid i {
            margin-right: 10px;
        }
        
        .gift-body {
            width: 100%;
            height: 140px;
            background-color: #d32f2f;
            position: absolute;
            bottom: 0;
            left: 0;
            border-radius: 0 0 15px 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .gift-question {
            font-size: 2.2rem;
            color: white;
            font-weight: bold;
            text-align: center;
            opacity: 0;
            transition: opacity 0.5s ease;
        }
        
        .gift-box.opened .gift-lid {
            height: 0;
            opacity: 0;
        }
        
        .gift-box.opened .gift-question {
            opacity: 1;
        }
        
        /* Response buttons */
        .response-container {
            display: none;
            margin-top: 30px;
        }
        
        .response-buttons {
            display: flex;
            justify-content: center;
            gap: 40px;
            margin-top: 20px;
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
        
        /* Playlist */
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
        }
        
        .footer {
            margin-top: 40px;
            color: #d32f2f;
            font-size: 1.1rem;
            padding: 20px;
            border-top: 3px dotted #ffeb3b;
        }
        
        @keyframes walk {
            0% { left: -200px; }
            30% { left: 30%; }
            70% { left: 60%; }
            100% { left: calc(100% - 180px); }
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .snoopy-box, .gift-box { height: 200px; }
            .snoopy-img { width: 150px; }
            .speech-bubble {
                max-width: 250px;
                left: 150px;
                top: 30px;
            }
            .gift-question { font-size: 1.8rem; }
            .response-buttons { flex-direction: column; gap: 20px; }
            .response-btn { padding: 15px 30px; font-size: 1.5rem; }
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
            .gift-question { font-size: 1.5rem; }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1><i class="fas fa-heart"></i> A Snoopy Valentine</h1>
            <div class="subtitle">For someone very special...</div>
        </div>
        
        <!-- BOX 1: Snoopy Box -->
        <div class="snoopy-box">
            <img src="https://www.pngmart.com/files/22/Snoopy-PNG-Isolated-HD.png" alt="Snoopy" class="snoopy-img" id="snoopyImage">
            <div class="speech-bubble">
                <p>Hello <span class="cesca-name">Cesca</span>, I really had a great time with you today. Thank you for this!</p>
            </div>
        </div>
        
        <!-- BOX 2: Message Box -->
        <div class="message-box">
            <h2>A Special Message</h2>
            <p>This Valentine's Day, I wanted to do something special to show you how much you mean to me. You make every day brighter.</p>
        </div>
        
        <!-- BOX 3: Gift Box -->
        <div class="gift-box" id="giftBox">
            <div class="gift-lid">
                <i class="fas fa-gift"></i> Click to Open
            </div>
            <div class="gift-body">
                <div class="gift-question">Can I be your girlfriend?</div>
            </div>
        </div>
        
        <!-- Response buttons (appear after gift is opened) -->
        <div class="response-container" id="responseContainer">
            <div class="response-buttons">
                <button class="response-btn yes-btn" id="yesBtn">YES! <i class="fas fa-heart"></i></button>
                <button class="response-btn no-btn" id="noBtn">No</button>
            </div>
        </div>
        
        <!-- Playlist (appear after YES) -->
        <div class="playlist-container" id="playlistContainer">
            <h2 class="playlist-title"><i class="fab fa-spotify"></i> For You: Our Playlist</h2>
            <p class="playlist-description">Songs that remind me of you. Click below to listen!</p>
            
            <a href="https://open.spotify.com/playlist/6FF9QQMTbt2tVxKWy1cj4Q?si=a58c552501ef46f0" target="_blank" class="spotify-link">
                <i class="fab fa-spotify"></i> Open Our Spotify Playlist
            </a>
        </div>
        
        <div class="footer">
            Made with <i class="fas fa-heart" style="color: #d32f2f;"></i> for Cesca
        </div>
    </div>

    <script>
        const giftBox = document.getElementById('giftBox');
        const responseContainer = document.getElementById('responseContainer');
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const playlistContainer = document.getElementById('playlistContainer');
        const snoopyImage = document.getElementById('snoopyImage');
        let giftOpened = false;
        
        function startSnoopyAnimation() {
            snoopyImage.style.left = '-200px';
            snoopyImage.style.animation = 'walk 10s linear forwards';
            snoopyImage.style.animationDelay = '1s';
        }
        
        giftBox.addEventListener('click', function() {
            if (!giftOpened) {
                giftOpened = true;
                giftBox.classList.add('opened');
                
                setTimeout(() => {
                    responseContainer.style.display = 'block';
                    responseContainer.style.animation = 'fadeIn 1s forwards';
                }, 800);
            }
        });
        
        yesBtn.addEventListener('click', function() {
            responseContainer.style.display = 'none';
            playlistContainer.style.display = 'block';
            playlistContainer.style.animation = 'fadeIn 1s forwards';
        });
        
        noBtn.addEventListener('click', function() {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            
            noBtn.style.position = 'absolute';
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
            
            yesBtn.style.transform = 'scale(1.2)';
            yesBtn.style.transition = 'transform 0.3s';
            
            alert("Just kidding! Click YES! 😉");
        });
        
        window.addEventListener('DOMContentLoaded', function() {
            startSnoopyAnimation();
        });
    </script>
</body>
</html>
