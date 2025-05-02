<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Game Review's</title>
  <style>
    body {
      background-color: #121212;
      color: #ffffff;
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }

    header {
      background-color: #1f1f1f;
      padding: 20px;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 2.5em;
      color: #00ffcc;
    }

    .container {
      padding: 20px;
      max-width: 800px;
      margin: auto;
    }

    .search-bar {
      margin-bottom: 20px;
      text-align: center;
    }

    .search-bar input {
      padding: 10px;
      width: 70%;
      border-radius: 5px;
      border: none;
      font-size: 1em;
    }

    .game-review {
      background-color: #1e1e1e;
      padding: 20px;
      margin-bottom: 20px;
      border-radius: 8px;
      border-left: 5px solid #00ffcc;
    }

    .game-review h2 {
      margin-top: 0;
      color: #00ffff;
    }

    .rating, .user-rating {
      font-size: 1.2em;
      color: #ffaa00;
    }

    .stars {
      cursor: pointer;
    }

    .stars span {
      font-size: 1.5em;
      color: gray;
    }

    .stars span.selected {
      color: gold;
    }

    .comment-section {
      margin-top: 15px;
    }

    .comment-section textarea {
      width: 100%;
      height: 60px;
      border-radius: 5px;
      border: none;
      padding: 10px;
      margin-bottom: 5px;
      resize: none;
    }

    .comment-section button {
      padding: 8px 12px;
      background-color: #00ffcc;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-weight: bold;
    }

    .comments {
      margin-top: 10px;
      font-size: 0.95em;
    }

    .comments p {
      background-color: #2b2b2b;
      padding: 8px;
      border-radius: 5px;
      margin-bottom: 5px;
    }
  </style>
</head>
<body>
  <header>
    <h1>Game Review's</h1>
  </header>
  <div class="container">
    <div class="search-bar">
      <input type="text" id="searchInput" placeholder="Search for a game..." onkeyup="filterGames()">
    </div>

    <!-- Fortnite -->
    <div class="game-review" data-title="fortnite">
      <h2>Fortnite</h2>
      <p class="rating">Official Rating: 8/10</p>
      <p>Fortnite offers fast-paced, creative battle royale gameplay with frequent updates and a vibrant player community.</p>

      <div class="user-rating stars" data-game="fortnite">
        <strong>Rate this game:</strong>
        <span data-star="1">&#9733;</span>
        <span data-star="2">&#9733;</span>
        <span data-star="3">&#9733;</span>
        <span data-star="4">&#9733;</span>
        <span data-star="5">&#9733;</span>
      </div>

      <div class="comment-section">
        <textarea placeholder="Leave a comment..."></textarea>
        <button onclick="submitComment(this)">Post</button>
        <div class="comments"></div>
      </div>
    </div>

    <!-- Minecraft -->
    <div class="game-review" data-title="minecraft">
      <h2>Minecraft</h2>
      <p class="rating">Official Rating: 7/10</p>
      <p>Minecraft is a sandbox classic, great for creativity and exploration, but its pace and style may not appeal to everyone.</p>

      <div class="user-rating stars" data-game="minecraft">
        <strong>Rate this game:</strong>
        <span data-star="1">&#9733;</span>
        <span data-star="2">&#9733;</span>
        <span data-star="3">&#9733;</span>
        <span data-star="4">&#9733;</span>
        <span data-star="5">&#9733;</span>
      </div>

      <div class="comment-section">
        <textarea placeholder="Leave a comment..."></textarea>
        <button onclick="submitComment(this)">Post</button>
        <div class="comments"></div>
      </div>
    </div>
  </div>

  <script>
    // Star rating
    document.querySelectorAll('.stars').forEach(starBlock => {
      starBlock.addEventListener('click', function (e) {
        if (e.target.tagName === 'SPAN') {
          const allStars = Array.from(this.children).slice(1);
          const rating = parseInt(e.target.dataset.star);
          allStars.forEach((star, index) => {
            star.classList.toggle('selected', index < rating);
          });
        }
      });
    });

    // Comments
    function submitComment(button) {
      const section = button.parentElement;
      const textarea = section.querySelector('textarea');
      const commentText = textarea.value.trim();
      if (commentText === '') return;
      const commentsDiv = section.querySelector('.comments');
      const p = document.createElement('p');
      p.textContent = commentText;
      commentsDiv.appendChild(p);
      textarea.value = '';
    }

    // Search Filter
    function filterGames() {
      const input = document.getElementById("searchInput").value.toLowerCase();
      const games = document.querySelectorAll(".game-review");
      games.forEach(game => {
        const title = game.getAttribute("data-title");
        game.style.display = title.includes(input) ? "block" : "none";
      });
    }
  </script>
</body>
</html>
