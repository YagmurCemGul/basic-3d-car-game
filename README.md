<h1 align="center">🚗 Basic 3D Car Game — HTML/CSS (Vanilla)</h1>

<p align="center">
  CSS perspektif hileleriyle 3D-vari görünüm, basit kontroller, coin toplama ve skor takibi — tamamen HTML/CSS/JS ile.
</p>

<p align="center">
  <img alt="HTML5" src="https://img.shields.io/badge/HTML5-✔-e34f26?logo=html5&logoColor=white">
  <img alt="CSS3" src="https://img.shields.io/badge/CSS3-✔-1572B6?logo=css3&logoColor=white">
  <img alt="Vanilla JS" src="https://img.shields.io/badge/JavaScript-Vanilla-f7df1e?logo=javascript&logoColor=222">
  <a href="./LICENSE"><img alt="License" src="https://img.shields.io/badge/License-MIT-yellow"></a>
</p>

<p align="center">
  <a href="#-demo--play">Play</a> •
  <a href="#-description">About</a> •
  <a href="#-features">Features</a> •
  <a href="#-controls">Controls</a> •
  <a href="#-tech-stack">Tech</a> •
  <a href="#-project-structure">Structure</a> •
  <a href="#-getting-started">Setup</a> •
  <a href="#-performance-tips">Performance</a> •
  <a href="#-accessibility">A11y</a> •
  <a href="#-testing--lighthouse">Testing</a> •
  <a href="#-deploy">Deploy</a> •
  <a href="#-roadmap">Roadmap</a> •
  <a href="#-contributing">Contributing</a> •
  <a href="#-license">License</a>
</p>

---

## 🎮 Demo & Play

* **Live Demo:** *add your GitHub Pages / Netlify / Vercel link here*
* **Short video:** *add a YouTube link*

> Tip: Put a screenshot under `docs/screenshot.png` and embed:
> `![Gameplay](docs/screenshot.png)`

---

## 📜 Description

A simple web-based game using only **HTML/CSS/JS**. Drive a car through a faux-3D track, **collect coins**, **avoid obstacles**, and push your **high score**.

---

## ✨ Features

* **3D-like environment:** CSS `perspective` + layered transforms
* **Simple controls:** keyboard **arrow keys**; optional on-screen **touch** buttons
* **Coin collection & scoring:** score HUD; incremental difficulty
* **Obstacle avoidance:** random spawn, collision ends the run
* **Pure frontend:** no frameworks, no WebGL — great for learning

---

## ⌨️ Controls

| Keyboard     | Action            |
| ------------ | ----------------- |
| ← / →        | Steer left/right  |
| ↑            | Speed up          |
| ↓            | Slow down / brake |
| P (optional) | Pause             |

*On mobile*: on-screen left/right buttons or swipe gestures (see `js/input.js`).

---

## 🧰 Tech Stack

* **HTML5** for structure
* **CSS3** for 3D-like perspective (`transform`, `perspective`, `translate3d`)
* **Vanilla JS** for game loop (`requestAnimationFrame`), collisions, UI

---

## 📁 Project Structure

```
.
├─ index.html
├─ css/
│  └─ styles.css              # layout, perspective, HUD
├─ js/
│  ├─ game.js                 # main loop, update/draw, collisions
│  ├─ input.js                # keyboard + touch controls
│  └─ utils.js                # helpers (rand, clamp, AABB)
├─ assets/
│  ├─ images/                 # car, coin, obstacle, track
│  └─ audio/                  # pickup / crash sfx (optional)
├─ docs/
│  └─ screenshot.png          # README media
└─ LICENSE
```

---

## 🚀 Getting Started

### Play locally

Just open **`index.html`** in a modern browser — or use a tiny static server (recommended for mobile inputs & caching):

```bash
# Option A: Python
python3 -m http.server 5173

# Option B: Node (serve)
npx serve -p 5173

# then open
http://localhost:5173
```

### How to Play

* Steer to collect **coins** and avoid **obstacles**
* **Score** goes up with each coin
* **Crash** ends the game — try to beat your high score!

---

## ⚙️ Performance Tips

* Use **`requestAnimationFrame`** for the game loop
* Move elements with **`transform: translate3d(...)`** (GPU friendly), not `top/left`
* Assign **`will-change: transform`** to moving sprites sparingly
* Minimize layout trashing; batch DOM writes/reads
* Keep textures small; prefer inline SVGs for UI icons
* On mobile, add `touch-action: none;` and **passive** listeners for smoother input

---

## ♿ Accessibility

* High contrast HUD colors; readable fonts
* Keyboard playable by default
* Announce score updates with an **ARIA live region** (e.g., `<div aria-live="polite">Score: …</div>`)
* Pause overlay captures focus; `Esc` to close (if you implement pause)

---

## ✅ Testing & Lighthouse

* **Manual tests:** collisions, coin pickup, boundary conditions
* **Lighthouse:** check **Performance**, **Best Practices**, **SEO**, **Accessibility**
* Optional browser tests with **Playwright** (e2e click/keys) if you want CI

---

## ☁️ Deploy

* **GitHub Pages:** push to `main`, enable Pages (or use `gh-pages` branch)
* **Netlify:** drag & drop repo or connect directly
* **Vercel:** “New Project” → select repo → deploy (static)

---

## 🗺️ Roadmap

* [ ] Touch UI (floating buttons) & gyroscope steering (optional)
* [ ] Power-ups (magnet, shield, slow-mo)
* [ ] High-score persistence (LocalStorage)
* [ ] PWA (manifest + service worker) for offline play
* [ ] Procedural track segments & difficulty ramp
* [ ] Simple SFX mixer (volume slider)

---

## 🤝 Contributing

PRs welcome!

1. Fork → feature branch
2. Keep PRs small; attach a short GIF/screen
3. Use clear commit messages (e.g., `feat: magnet power-up`)

**Good first issues:** touch buttons, score persist, pause menu, PWA.

---

## 📄 License

This project is licensed under the **MIT License** — see [`LICENSE`](./LICENSE).

---

## 🧩 Appendix: Minimal Skeleton

**`index.html`**

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Basic 3D Car Game</title>
  <link rel="stylesheet" href="css/styles.css" />
</head>
<body>
  <main class="game">
    <div id="hud"><span id="score">0</span></div>
    <div id="track">
      <div id="car" class="sprite"></div>
      <div id="coins"></div>
      <div id="obstacles"></div>
    </div>
    <div id="touch-ui" aria-hidden="true">
      <button id="btn-left">◀</button>
      <button id="btn-right">▶</button>
    </div>
  </main>
  <script src="js/utils.js"></script>
  <script src="js/input.js"></script>
  <script src="js/game.js"></script>
</body>
</html>
```

**`css/styles.css` (excerpt)**

```css
:root { --w: 800px; --h: 600px; }
body { margin:0; background:#111; color:#fff; font:16px/1.4 system-ui; display:grid; place-items:center; }
.game { width:var(--w); height:var(--h); position:relative; }
#track {
  width:100%; height:100%; position:relative; overflow:hidden;
  perspective: 900px; background: linear-gradient(#333, #111);
}
.sprite { will-change: transform; position:absolute; }
#car { width:60px; height:100px; bottom:30px; left:calc(50% - 30px); background:#0ff; border-radius:10px; transform:translate3d(0,0,0); }
#hud { position:absolute; top:12px; left:12px; font-weight:bold; }
#touch-ui { position:absolute; bottom:10px; left:0; right:0; display:flex; justify-content:space-between; padding:0 12px; }
#touch-ui button { font-size:20px; padding:12px 18px; background:#222; color:#fff; border:1px solid #444; border-radius:10px; }
```

**`js/game.js` (excerpt)**

```js
const car = document.getElementById('car');
const coinsBox = document.getElementById('coins');
const obstaclesBox = document.getElementById('obstacles');
const scoreEl = document.getElementById('score');

let running = true, score = 0, x = 0, speed = 6;
const state = { left:false, right:false, up:false, down:false };

function spawn(el, cls, x, y, w, h) {
  const n = document.createElement('div');
  n.className = `sprite ${cls}`;
  n.style.cssText = `left:${x}px; top:${y}px; width:${w}px; height:${h}px; background:#fc0;`;
  el.appendChild(n);
  return n;
}

function aabb(a, b) {
  const ar = a.getBoundingClientRect(); const br = b.getBoundingClientRect();
  return !(ar.right < br.left || ar.left > br.right || ar.bottom < br.top || ar.top > br.bottom);
}

function update() {
  // input
  if (state.left) x -= 8;
  if (state.right) x += 8;
  x = Math.max(-300, Math.min(300, x));
  car.style.transform = `translate3d(${x}px,0,0)`;
  // TODO: move coins/obstacles toward the car, recycle off-screen, check collisions
}

function loop() {
  if (!running) return;
  update();
  requestAnimationFrame(loop);
}
requestAnimationFrame(loop);

// wire inputs
window.addEventListener('keydown', e => { if (e.key === 'ArrowLeft') state.left = true; if (e.key === 'ArrowRight') state.right = true; }, {passive:true});
window.addEventListener('keyup',   e => { if (e.key === 'ArrowLeft') state.left = false; if (e.key === 'ArrowRight') state.right = false; }, {passive:true});
```
