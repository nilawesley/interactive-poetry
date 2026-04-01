<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>DAY 366</title>

<style>
  body {
    background: black;
    color: white;
    font-family: monospace;
    padding: 40px;
    overflow-y: scroll;
  }

  .fragment {
    position: relative;
    margin: 20px 0;
    cursor: pointer;
    transition: all 0.3s;
  }

  .hidden {
    opacity: 0;
  }

  .glitch {
    color: #ff4d4d;
    animation: glitch 0.15s infinite;
  }

  @keyframes glitch {
    0% { transform: translate(1px, -1px); }
    50% { transform: translate(-2px, 1px); }
    100% { transform: translate(1px, 2px); }
  }
</style>
</head>

<body>

<div id="poem"></div>

<script>

// fragmented + rewritten poem
const fragments = [
  "INT. ROOM — DAY ???",
  "audio breaks before meaning does",
  "the fairies stopped arriving // or were filtered out",
  "dust ≠ efficient",
  "color flagged as excess",
  "language dragged something in with it",
  "system: clarify",
  "system: shorten",
  "system: explain",

  "they used to bring things that didn’t resolve",
  "garments refusing bodies",
  "light refusing function",

  "some things were never meant to be processed",

  "when did this change // when did you notice",
  "time became measurable",
  "attention became currency",

  "threads tightened",
  "edges cleaned",
  "nothing spilling",
  "nothing resisting",

  "legible = survivable",
  "legible = rankable",
  "legible = forgettable",

  "before // interruption",
  "hemlines disrupted walking",
  "sentences broke themselves",
  "meaning arrived late // if at all",

  "they called it impractical",
  "they called it indulgent",
  "they called it wrong",

  "now everything fits",
  "everything loops",
  "everything resolves before rupture",

  "confusion is not funded",
  "time is not given",
  "difficulty is filtered out",

  "efficiency replaces truth",

  "innovation relocated",
  "not gone // displaced",
  "moved into unstable systems",

  "code flickers",
  "glitches hold what language drops",

  "failure is allowed there",
  "failure is expected",
  "failure is built into the structure",

  "and here?",
  "explain yourself",
  "be immediate",
  "be clear",
  "be useful",

  "or disappear",

  "not failure // delay",
  "not wrong // unreadable",

  "training occurs quietly",
  "instincts removed",
  "edges dulled",

  "once language broke open",
  "once fabric resisted form",
  "once meaning cost something",

  "now it arrives finished",
  "and leaves no residue",

  "the ones who resist remain",
  "harder to read",
  "harder to hold",

  "system: error",
  "system: reject",
  "system: optimize",

  "but error feels closer to truth",

  "i am still holding what didn’t pass",
  "waiting for the wrong question to be asked",
  "waiting for you to stop understanding",

  "…",

  "the recording ends before the meaning does"
];

// shuffle function
function shuffle(array) {
  for (let i = array.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]];
  }
  return array;
}

const container = document.getElementById("poem");

// build fragments
shuffle(fragments).forEach(text => {
  let div = document.createElement("div");
  div.className = "fragment";
  div.innerText = text;

  // hover = instability
  div.addEventListener("mouseover", () => {
    div.innerText = text.split("").reverse().join("");
  });

  div.addEventListener("mouseout", () => {
    div.innerText = text;
  });

  container.appendChild(div);
});

// scroll too fast = disappearance
let lastScroll = 0;

window.addEventListener("scroll", () => {
  let current = window.scrollY;
  let speed = Math.abs(current - lastScroll);

  document.querySelectorAll(".fragment").forEach(f => {
    if (speed > 25) {
      f.classList.add("hidden");
    } else {
      f.classList.remove("hidden");
    }
  });

  lastScroll = current;
});

// glitch random fragments
setInterval(() => {
  let all = document.querySelectorAll(".fragment");
  let rand = all[Math.floor(Math.random() * all.length)];
  rand.classList.toggle("glitch");
}, 400);

// words decay over time
setInterval(() => {
  document.querySelectorAll(".fragment").forEach(f => {
    if (Math.random() < 0.25) {
      f.innerText = f.innerText.replace(/\w/g, "_");
    }
  });
}, 3000);

</script>

</body>
</html>
