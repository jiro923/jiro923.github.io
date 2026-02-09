<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>For You 🤍</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }

    body {
      background: #fff;
      color: #333;
      text-align: center;
      overflow-x: hidden;
    }

    section {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 2rem;
    }

    /* Color palette */
    .red { color: #e63946; }
    .yellow { color: #f4c430; }

    /* First section */
    .hero {
      background: linear-gradient(180deg, #ffffff, #fff5f5);
    }

    .hero img {
      width: 220px;
      margin-bottom: 1.5rem;
    }

    .hero h1 {
      font-size: 2.2rem;
      margin-bottom: 1rem;
    }

    .hero p {
      font-size: 1.1rem;
      max-width: 500px;
    }

    .scroll {
      margin-top: 2rem;
      font-size: 0.9rem;
      opacity: 0.7;
    }

    /* Message section */
    .message {
      background: #fff;
    }

    .message h2 {
      font-size: 2rem;
      margin-bottom: 1rem;
    }

    .message p {
      max-width: 600px;
      font-size: 1.1rem;
      line-height: 1.7;
    }

    /* Question section */
    .question {
      background: linear-gradient(180deg, #fff, #fff9e6);
    }

    .question h2 {
      font-size: 2.3rem;
      margin-bottom: 2rem;
    }

    .buttons {
      display: flex;
      gap: 1.5rem;
    }

    button {
      padding: 0.9rem 2rem;
      font-size: 1.1rem;
      border-radius: 30px;
      border: none;
      cursor: pointer;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    button:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.15);
    }

    .yes {
      background: #e63946;
      color: white;
    }

    .no {
      background: #f4c430;
      color: #333;
    }

    /* Little hearts animation */
    .heart {
      position: fixed;
      bottom: -20px;
      font-size: 20px;
      animation: floatUp 6s linear infinite;
      opacity: 0.8;
    }

    @keyframes floatUp {
      0% { transform: translateY(0); opacity: 0; }
      10% { opacity: 1; }
      100% { transform: translateY(-110vh); opacity: 0; }
    }
  
        /* Gift cover (oval envelope style) */
    .gift-cover {
      width: 380px;
      height: 260px;
      background: #e63946;
      border-radius: 160px;
      position: relative;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 16px 40px rgba(0,0,0,0.25);
      transition: transform 0.5s ease, opacity 0.5s ease;
    }

    .gift-cover:hover {
      transform: scale(1.03);
    }

    .ribbon-vertical {
      position: absolute;
      width: 28px;
      height: 100%;
      background: #f4c430;
      left: 50%;
      transform: translateX(-50%);
    }

    .ribbon-bow {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 2rem;
    }

    .cover-text {
      position: absolute;
      bottom: 18px;
      font-size: 0.9rem;
      color: #fff;
      opacity: 0.85;
    }

    .gift-cover.open {
      opacity: 0;
      transform: scale(0.8);
      pointer-events: none;
    }

    .hidden-question { display: none; }

    .question-inside {
      opacity: 0;
      transition: opacity 0.5s ease;
      z-index: 2;
      color: white;
    }

    .question-inside h2 {
      font-size: 1.6rem;
      margin-bottom: 1.5rem;
    }

    .gift-cover.open .question-inside {
      opacity: 1;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(25px); }
      to { opacity: 1; transform: translateY(0); }
    }
      to { opacity: 1; transform: translateY(0); }
    }

  </style>
</head>
<body>

  <!-- Section 1: Thank you page -->
  <section class="hero">
    <!-- Replace the src with a Snoopy image you like -->
    <img src="https://i.imgur.com/9QOZQYB.png" alt="Snoopy" />

    <h1 class="red">Hi, baby 🤍</h1>
    <p>
      Thank you for today. I really appreciate it more than you know.
      This is just a small thing, but I wanted to make something special for you.
    </p>

    <div class="scroll">scroll down ⬇</div>
  </section>

  <!-- Section 2: Hidden message -->
  <section class="message">
    <h2 class="yellow">A little confession…</h2>
    <p>
      Spending time with you feels easy, warm, and safe.
      You make ordinary days feel softer and brighter.
      Somewhere along the way, I realized I don’t just like you —
      I want to choose you, intentionally, every day.
    </p>
  </section>

  <!-- Section 3: Mystery cover -->
  <section class="question">
    <div class="gift-cover" onclick="openBox()" id="giftCover">
      <div class="ribbon-vertical"></div>
      <div class="ribbon-bow">🎀</div>
      <div class="cover-text">tap to open</div>

      <div class="question-inside">
        <h2>Will you be my girlfriend? 🥺❤️</h2>
        <div class="buttons">
          <button class="yes" onclick="yesClicked()">Yes</button>
          <button class="no" onclick="noClicked()">No</button>
        </div>
      </div>
    </div>

    <div class="hidden-question" id="hiddenQuestion">
      <h2 class="red">Will you be my girlfriend? 🥺❤️</h2>
      <div class="buttons">
        <button class="yes" onclick="yesClicked()">Yes</button>
        <button class="no" onclick="noClicked()">No</button>
      </div>
    </div>
  </section>

  <script>
    function yesClicked() {
      window.location.href = "https://open.spotify.com/playlist/6FF9QQMTbt2tVxKWy1cj4Q?si=8258c92a38dd49f7";
    }

            function openBox() {
      const cover = document.getElementById('giftCover');
      cover.classList.add('open');
    }
, 400);
    }

    function noClicked() {
      alert("are you sure? 😭 try again");
    }

    // floating hearts
    setInterval(() => {
      const heart = document.createElement('div');
      heart.classList.add('heart');
      heart.innerText = '❤️';
      heart.style.left = Math.random() * 100 + 'vw';
      heart.style.animationDuration = (4 + Math.random() * 3) + 's';
      document.body.appendChild(heart);

      setTimeout(() => {
        heart.remove();
      }, 7000);
    }, 600);
  </script>

</body>
</html>
