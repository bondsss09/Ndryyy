# Ndryyy
!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Apakah Kamu Mau Jadi Ceweku?</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@600&display=swap');
  body {
    margin: 0;
    padding: 0;
    height: 100vh;
    background: linear-gradient(135deg, #fceabb, #f8b500);
    font-family: 'Poppins', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    overflow: hidden;
  }
  h1 {
    font-size: 2.8rem;
    margin-bottom: 2rem;
    color: #5b2c6f;
    text-shadow: 0 2px 6px rgba(0,0,0,0.2);
  }
  .buttons {
    display: flex;
    gap: 3rem;
  }
  button {
    padding: 1rem 2rem;
    font-size: 1.4rem;
    border-radius: 50px;
    border: none;
    cursor: pointer;
    user-select: none;
    font-weight: 600;
    min-width: 160px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.15);
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }
  button:active {
    transform: scale(0.95);
  }
  #ya {
    background-color: #e91e63;
    color: white;
  }
  #ya:hover {
    box-shadow: 0 10px 20px rgba(233, 30, 99, 0.7);
  }
  #tidak {
    background-color: #555;
    color: white;
    position: relative;
  }
  /* Animation for 'Tidak' button moving randomly inside container */
  @keyframes moveAround {
    0%   { transform: translate(0px, 0px); }
    20%  { transform: translate(50px, -20px); }
    40%  { transform: translate(-40px, 20px); }
    60%  { transform: translate(30px, 40px); }
    80%  { transform: translate(-30px, -40px); }
    100% { transform: translate(0px, 0px); }
  }
  #tidak.moving {
    animation: moveAround 4s ease-in-out infinite;
  }
  /* Heart container */
  #hearts-container {
    position: fixed;
    top: 0; left: 0; width: 100%; height: 100%;
    pointer-events: none;
    overflow: visible;
  }
  .heart {
    position: absolute;
    width: 24px;
    height: 24px;
    pointer-events: none;
    background-color: #e91e63;
    clip-path: polygon(
      50% 15%,
      61% 10%,
      75% 10%,
      85% 28%,
      85% 43%,
      75% 60%,
      55% 80%,
      50% 90%,
      45% 80%,
      25% 60%,
      15% 43%,
      15% 28%,
      25% 10%,
      39% 10%
    );
    animation: floatUp 3s ease forwards;
    filter: drop-shadow(0 1px 1px rgba(0,0,0,0.2));
  }
  @keyframes floatUp {
    0% {
      opacity: 1;
      transform: translateY(0) scale(1);
    }
    100% {
      opacity: 0;
      transform: translateY(-120px) scale(1.5);
    }
  }
</style>
</head>
<body>
  <h1>Ndryyy ko mau kah jadi ceweku?</h1>
  <div class="buttons">
    <button id="tidak" class="moving">Tidak</button>
    <button id="ya">Ya saya mau</button>
  </div>
  <div id="hearts-container"></div>
<script>
  const tidakBtn = document.getElementById('tidak');
  const yaBtn = document.getElementById('ya');
  const heartsContainer = document.getElementById('hearts-container');

  // Initially moving class animates 'Tidak'
  let tidakMoving = true;

  // Click event for 'Tidak' button
  tidakBtn.addEventListener('click', () => {
    if (tidakMoving) {
      // Change text and stop moving
      tidakBtn.textContent = 'Ya saya mau sekali';
      tidakBtn.classList.remove('moving');
      tidakMoving = false;
      // Change color to pink to match 'Ya' button
      tidakBtn.style.backgroundColor = '#e91e63';
      tidakBtn.style.cursor = 'default';
    }
  });

  // Click event for 'Ya saya mau' button
  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart');
    // Random start position near bottom center-ish
    heart.style.left = (50 + (Math.random() * 30 - 15)) + '%';
    heart.style.top = '90%';
    // Random size for variety
    const size = 16 + Math.random() * 16;
    heart.style.width = size + 'px';
    heart.style.height = size + 'px';
    // Random animation duration
    heart.style.animationDuration = (2 + Math.random() * 2) + 's';
    heartsContainer.appendChild(heart);
    // Remove heart after animation
    setTimeout(() => {
      heart.remove();
    }, 3000);
  }

  yaBtn.addEventListener('click', () => {
    // Create many hearts quickly
    for (let i = 0; i < 50; i++) {
      setTimeout(createHeart, i * 60);
    }
  });
</script>
</body>
</html>

