<!-- GLOBAL STYLES: keep page white -->
<style>
  body {
    background-color: #ffffff !important;
    margin: 0;
    padding: 0;
  }

  /* Soft cursor-follow swirl in the deep background */
  #cursor-swirl {
    position: fixed;
    inset: 0;
    z-index: -3;
    pointer-events: none;

    background: radial-gradient(
      circle at center,
      #ffd6ff 0%,
      #c3e7ff 12%,
      #fff1b8 25%,
      transparent 60%
    );

    opacity: 0.25;   /* soft so page still reads as white */
    transition: background-position 0.12s ease-out;
  }

  /* Medium RGB glow dots (trail) — ABOVE everything */
  .glow-dot {
    position: fixed;
    width: 36px;           /* back to medium size */
    height: 36px;
    border-radius: 50%;
    pointer-events: none;
    z-index: 999;          /* sits over banner + buttons */

    opacity: 0.8;
    transform: translate(-50%, -50%);
    animation: fadeOut 1s linear forwards;
    filter: blur(4px);
  }

  @keyframes fadeOut {
    0% {
      opacity: 0.8;
      transform: translate(-50%, -50%) scale(1);
    }
    100% {
      opacity: 0;
      transform: translate(-50%, -50%) scale(0.3);
    }
  }

  /* Link card styles */
  .pop-card {
    padding: 16px 12px;
    background: #e5e0ff;
    border-radius: 8px;
    border: 1px solid #c7b4ff;
    text-decoration: none;
    display: block;
    color: #000;
    transition: all 0.3s ease;
  }

  .pop-card:hover {
    background: linear-gradient(
      135deg,
      #ffd6ff,
      #c3c8ff,
      #f7e0ff,
      #ffe1fa
    );
    transform: scale(1.07);
    box-shadow: 0 0 20px rgba(176, 120, 255, 0.55);
    border-color: #b48aff;
  }
</style>

<div id="cursor-swirl"></div>

<script>
  const swirl = document.getElementById("cursor-swirl");

  // Move swirl + trail with cursor
  document.addEventListener("mousemove", (e) => {
    const x = (e.clientX / window.innerWidth) * 100;
    const y = (e.clientY / window.innerHeight) * 100;
    swirl.style.backgroundPosition = `${x}% ${y}%`;

    createGlow(e.clientX, e.clientY);
  });

  // Extra color bursts on click
  document.addEventListener("click", (e) => {
    createBurst(e.clientX, e.clientY);
  });

  let hue = 0;

  // Single glow dot
  function createGlow(x, y, sizeMultiplier = 1) {
    const dot = document.createElement("div");
    dot.className = "glow-dot";

    dot.style.left = x + "px";
    dot.style.top = y + "px";

    // optional size tweak for bursts
    if (sizeMultiplier !== 1) {
      const base = 36;
      const size = base * sizeMultiplier;
      dot.style.width = size + "px";
      dot.style.height = size + "px";
    }

    dot.style.background = `radial-gradient(circle, hsl(${hue}, 100%, 75%), transparent 70%)`;

    hue = (hue + 15) % 360;

    document.body.appendChild(dot);
    setTimeout(() => dot.remove(), 1000);
  }

  // Click burst: several dots around click point
  function createBurst(x, y) {
    const particles = 8; // number of dots in burst
    const minDist = 20;
    const maxDist = 70;

    for (let i = 0; i < particles; i++) {
      const angle = Math.random() * Math.PI * 2;
      const dist = minDist + Math.random() * (maxDist - minDist);
      const offsetX = Math.cos(angle) * dist;
      const offsetY = Math.sin(angle) * dist;

      // slightly larger dots for the burst
      createGlow(x + offsetX, y + offsetY, 1.3);
    }
  }
</script>


<!-- MAIN CONTENT WRAPPER -->
<div style="background-color: #ffffff; min-height: 100vh; padding: 20px 0; position: relative; z-index: 1;">

  <div style="max-width: 1100px; margin: 0 auto; text-align: center;">

    <!-- BANNER -->
    <img src="images/Banner2.jpg"
         alt="POPaganda Archive banner"
         style="width: 100%; height: auto; border-radius: 8px; margin-bottom: 32px;" />

    <!-- GRID OF LINKS -->
    <div style="
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
        gap: 16px;
        text-align: center;
        margin-top: 20px;
      ">

      <a href="exhibitions/solo-exhibitions.html" class="pop-card">
        <strong>Solo exhibitions by decade</strong>
      </a>

      <a href="exhibitions/group-exhibitions.html" class="pop-card">
        <strong>Group exhibitions by decade</strong>
      </a>

      <a href="murals-and-street-works.html" class="pop-card">
        <strong>Murals and street works</strong>
      </a>

      <a href="pop-ups-shops-brand-activations.html" class="pop-card">
        <strong>Pop-ups, shops and brand activations</strong>
      </a>

      <a href="public-talks-lectures-book-signings.html" class="pop-card">
        <strong>Public talks, lectures and book signings</strong>
      </a>

      <a href="benefit-auctions-charity-projects.html" class="pop-card">
        <strong>Benefit auctions and charity projects</strong>
      </a>

      <a href="film-screenings-festivals-film-events.html" class="pop-card">
        <strong>Film screenings, festivals and film-related events</strong>
      </a>

      <a href="digital-projects-nft-crypto-art.html" class="pop-card">
        <strong>Digital projects, NFT drops and crypto-art events</strong>
      </a>

      <a href="special-events-parties-tours.html" class="pop-card">
        <strong>Special events, parties, and tours</strong>
      </a>

    </div>

  </div>
</div>
