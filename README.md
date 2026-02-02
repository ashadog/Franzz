<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Will You Be My Valentine?</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      text-align: center;
    }

    .card {
      background: #fff;
      padding: 24px;
      border-radius: 20px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.2);
      max-width: 340px;
      width: 90%;
    }

    h1 {
      font-size: 1.4rem;
      margin-bottom: 16px;
      color: #e63946;
    }

    img {
      width: 100%;
      border-radius: 16px;
      margin-bottom: 16px;
    }

    .buttons {
      display: flex;
      gap: 12px;
      justify-content: center;
    }

    button {
      padding: 10px 18px;
      border: none;
      border-radius: 999px;
      font-size: 1rem;
      cursor: pointer;
      transition: transform 0.15s ease, box-shadow 0.15s ease;
    }

    button:hover {
      transform: scale(1.05);
      box-shadow: 0 6px 14px rgba(0,0,0,0.15);
    }

    .yes {
      background: #38b000;
      color: white;
    }

    .no {
      background: #adb5bd;
      color: white;
    }

    .hidden {
      display: none;
    }

    .caption {
      margin-top: 10px;
      font-size: 0.95rem;
      color: #555;
    }
  </style>
</head>
<body>

  <div class="card">
    <h1 id="question">Will you be my Valentine? 💛</h1>

    <!-- Replace these GIF links with your own Minion GIFs -->
    <img
      id="minionImg"
      src="https://media.tenor.com/8GjbkVyjbakAAAAd/minions-heart.gif"
      alt="Minion begging with flowers"
    />

    <div class="buttons" id="btnGroup">
      <button class="yes" onclick="sayYes()">Yes 💐</button>
      <button class="no" onclick="sayNo()">No 🙃</button>
    </div>

    <div class="caption" id="caption">Click one… I’m nervous 😳</div>
  </div>

  <script>
    function sayYes() {
      document.getElementById('question').innerText = 'YAAAY!! Happy Valentine’s 💖';
      document.getElementById('minionImg').src = 'https://www.gifcen.com/wp-content/uploads/2021/05/minions-gif-8.gif';
      document.getElementById('caption').innerText = 'You just made my day 🥳💛';
      document.getElementById('btnGroup').classList.add('hidden');
    }

    function sayNo() {
      const noBtn = document.querySelector('.no');
      const card = document.querySelector('.card');

      const captions = [
        "don’t click the no button 😭",
        "be honest pls",
        "try pressing no",
        "i dare you to press no",
        "this took courage to post",
        "just answer the question 🥹"
      ];

      if (typeof sayNo.count === 'undefined') {
        sayNo.count = 0;
      }

      document.getElementById('caption').innerText = captions[sayNo.count];
      sayNo.count = (sayNo.count + 1) % captions.length;

      const cardRect = card.getBoundingClientRect();
      const btnRect = noBtn.getBoundingClientRect();

      const maxX = cardRect.width - btnRect.width - 20;
      const maxY = cardRect.height - btnRect.height - 20;

      const randomX = Math.random() * maxX;
      const randomY = Math.random() * maxY;

      noBtn.style.position = 'absolute';
      noBtn.style.left = randomX + 'px';
      noBtn.style.top = randomY + 'px';
    }
  </script>

</body>
</html>
