<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Explain It Simply</title>
<meta name="viewport" content="width=device-width, initial-scale=1">

<style>
:root {
  --bg:#f4f6f8; --card:#fff; --text:#222; --accent:#4a6cff;
}
body.dark {
  --bg:#121212; --card:#1e1e1e; --text:#f0f0f0; --accent:#8aa4ff;
}
body {
  margin:0; font-family:Arial; background:var(--bg); color:var(--text);
}
header {
  background:var(--accent); color:white; padding:20px; text-align:center;
}
header button {
  padding:8px 12px; border:none; border-radius:6px; cursor:pointer;
}
main {
  max-width:900px; margin:20px auto; padding:15px;
}
input, textarea {
  width:100%; padding:10px; margin-bottom:15px; border-radius:6px; border:1px solid #ccc;
}
.card {
  background:var(--card); padding:20px; border-radius:10px; margin-bottom:20px;
  box-shadow:0 2px 6px rgba(0,0,0,.1);
  transition: transform 0.2s;
}
.card:hover { transform: scale(1.01); }
.tag { font-size:12px; color:var(--accent); margin-bottom:5px; display:block; }
footer { text-align:center; opacity:.7; padding:15px; }
.like { cursor:pointer; color:var(--accent); font-weight:bold; margin-top:10px; display:inline-block; }
</style>
</head>

<body>

<header>
  <h1>Explain It Simply</h1>
  <p>Confusing things. Explained in under 60 seconds.</p>
  <button onclick="toggleDark()">🌙 Dark Mode</button>
</header>

<main>

<input id="search" placeholder="Search something..." onkeyup="searchCards()">

<!-- CARD 1 -->
<div class="card">
  <div class="tag">Technology</div>
  <h2>What is AI?</h2>
  <p>AI is when computers learn from data to make decisions.</p>
  <p><b>Example:</b> YouTube recommending videos.</p>
  <div class="like" onclick="like(0)">👍 Likes: <span id="l0">0</span></div>
</div>

<!-- CARD 2 -->
<div class="card">
  <div class="tag">Life Skills</div>
  <h2>Why do we procrastinate?</h2>
  <p>Our brain prefers easy fun over hard work.</p>
  <p><b>Example:</b> Gaming instead of homework.</p>
  <div class="like" onclick="like(1)">👍 Likes: <span id="l1">0</span></div>
</div>

<!-- CARD 3 -->
<div class="card">
  <div class="tag">School</div>
  <h2>What is gravity?</h2>
  <p>Gravity is the force that pulls objects toward each other.</p>
  <p><b>Example:</b> Dropping a phone makes it fall down.</p>
  <div class="like" onclick="like(2)">👍 Likes: <span id="l2">0</span></div>
</div>

<!-- ABOUT -->
<div class="card">
  <h2>About This Website</h2>
  <p>This website explains hard topics using simple words so anyone can understand in under one minute.</p>
</div>

<!-- SUGGESTION -->
<div class="card">
  <h2>Suggest a Topic</h2>
  <textarea placeholder="What should we explain next?"></textarea>
  <button>Send (demo)</button>
</div>

</main>

<footer>
© 2026 Explain It Simply
</footer>

<script>
function toggleDark(){
  document.body.classList.toggle("dark");
}

function searchCards(){
  let v = search.value.toLowerCase();
  document.querySelectorAll(".card").forEach(c=>{
    c.style.display = c.innerText.toLowerCase().includes(v)?"block":"none";
  });
}

function like(n){
  let count = localStorage.getItem("like"+n) || 0;
  count++;
  localStorage.setItem("like"+n,count);
  document.getElementById("l"+n).innerText = count;
}

// Load saved likes
for(let i=0;i<3;i++){
  document.getElementById("l"+i).innerText = localStorage.getItem("like"+i) || 0;
}
</script>

</body>
</html>
