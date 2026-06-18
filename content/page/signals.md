---
title: "Signals & Traces"
slug: "study"
menu:
  main:
    weight: 20
---

<div id="signal-receiver" style="
  min-height: 90px;
  padding: 1rem;
  border: 1px solid rgba(255,255,255,.15);
  border-radius: 10px;
  font-family: monospace;
  letter-spacing: .03em;
  opacity: .9;
">
  tuning...
</div>

<script>
const signals = [
  "follow your curiosity",
  "learning best is learning slowly",
  "the real treasure often lives here",
  "this is not my life i'm just trying it on",
  "a black cat named Pumpkin",
  "the devil likes peanut butter",
  "ask about the changeling",
  "will-o-the-wisp adventures often end up right where you started"
];

const receiver = document.getElementById("signal-receiver");
const noise = "░▒▓█#@$%&*+?";

function scrambleText(length) {
  return Array.from({ length }, () =>
    noise[Math.floor(Math.random() * noise.length)]
  ).join("");
}

function tuneSignal(message) {
  let step = 0;
  const maxSteps = 18;

  const interval = setInterval(() => {
    let output = "";

    for (let i = 0; i < message.length; i++) {
      const revealChance = step / maxSteps;
      output += Math.random() < revealChance
        ? message[i]
        : noise[Math.floor(Math.random() * noise.length)];
    }

    receiver.textContent = output;
    step++;

    if (step > maxSteps) {
      clearInterval(interval);
      receiver.textContent = message;
    }
  }, 80);
}

function receiveSignal() {
  const signal = signals[Math.floor(Math.random() * signals.length)];

  receiver.textContent = scrambleText(signal.length);

  setTimeout(() => tuneSignal(signal), 600);
}

receiveSignal();
setInterval(receiveSignal, 10000);
</script>

<h2>Now Reading</h2>

<div class="artifact-stack" onclick="rotateStack(this)">
  <img src="/Shelf/Now Reading/wicked+divine.jpg">
  <img src="/Shelf/Now Reading/Unknown.jpg">
  <img src="/Shelf/Now Reading/TWTD13_900px.jpg">

</div>


<h2>Now Playing</h2>

<div class="artifact-stack album-stack" onclick="rotateStack(this)">
  <img src="/Shelf/Now Playing/3 ft.jpeg">
  <img src="/Shelf/Now Playing/hate.jpeg">
  <img src="/Shelf/Now Playing/mothership.jpg">
</div>


<h2>Now Watching</h2>

<div class="artifact-stack movie-stack" onclick="rotateStack(this)">
  <img src="/Shelf/Now Watching/house party.jpg">
  <img src="/Shelf/Now Watching/baby oopsie.jpg">
  <img src="/Shelf/Now Watching/punky brewster.jpg">
  <img src="/Shelf/Now Watching/he man.jpeg">
</div>

<style>
.artifact-stack {
  position: relative;
  height: 360px;
  width: 230px;
  margin: 1rem 0 2rem 1rem;
  cursor: pointer;
}

.artifact-stack img {
  position: absolute;
  height: 260px;
  width: auto;
  border-radius: 8px;
  box-shadow: 0 8px 24px rgba(0,0,0,.35);
  transition: transform .25s ease, z-index .25s ease;
}

.album-stack {
  height: 260px;
  width: 220px;
}

.album-stack img {
  height: 180px;
}

.movie-stack {
  height: 300px;
  width: 200px;
}

.movie-stack img {
  height: 220px;
}

.artifact-stack img:nth-child(1) {
  transform: rotate(-2deg) translate(0, 0);
  z-index: 4;
}

.artifact-stack img:nth-child(2) {
  transform: rotate(3deg) translate(18px, 12px);
  z-index: 3;
}

.artifact-stack img:nth-child(3) {
  transform: rotate(-5deg) translate(36px, 24px);
  z-index: 2;
}

.artifact-stack img:nth-child(4) {
  transform: rotate(5deg) translate(54px, 36px);
  z-index: 1;
}
</style>

<script>
function rotateStack(stack) {
  const first = stack.querySelector("img");
  stack.appendChild(first);
}
</script>