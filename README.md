# -kiss-embed-<!DOCTYPE html>
<html>
<head>
<style>
  body {
    background-color: #0f0f1a;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    overflow: hidden;
    cursor: pointer;
  }
  .kiss-btn {
    font-size: 80px;
    user-select: none;
    transition: transform 0.2s;
  }
  .kiss-btn:hover {
    transform: scale(1.2);
  }
  .particle {
    position: absolute;
    font-size: 24px;
    pointer-events: none;
    animation: floatUp 2s ease-out forwards;
  }
  @keyframes floatUp {
    0% { opacity: 1; transform: translate(0, 0) scale(1); }
    100% { opacity: 0; transform: translate(var(--x), var(--y)) scale(2); }
  }
</style>
</head>
<body>
<div class="kiss-btn" onclick="createHearts(event)">💋</div>
<script>
function createHearts(e) {
  const items = ['💋', '💖', '❤️', '✨', '😘', '💕'];
  for (let i = 0; i < 15; i++) {
    const particle = document.createElement('div');
    particle.className = 'particle';
    particle.innerText = items[Math.floor(Math.random() * items.length)];
    particle.style.left = e.clientX + 'px';
    particle.style.top = e.clientY + 'px';
    const x = (Math.random() - 0.5) * 300 + 'px';
    const y = (Math.random() - 0.8) * 300 + 'px';
    particle.style.setProperty('--x', x);
    particle.style.setProperty('--y', y);
    document.body.appendChild(particle);
    setTimeout(() => { particle.remove(); }, 2000);
  }
}
</script>
</body>
</html>
