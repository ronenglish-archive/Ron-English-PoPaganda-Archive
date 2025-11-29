<!-- CURSOR-FOLLOW COLOR SWIRL BACKGROUND -->
<style>
  #cursor-swirl {
    position: fixed;
    inset: 0;
    z-index: -2;
    pointer-events: none;

    background: radial-gradient(
      circle at center,
      #ffd6ff 0%,
      #c3e7ff 25%,
      #fff1b8 45%,
      transparent 70%
    );

    opacity: 0.40;
    transition: background-position 0.12s ease-out;
  }

  /* Glow particles for RGB trail */
  .glow-dot {
    position: fixed;

    /* ⬆⬆⬆ Increased size from 18px → 36px ⬆⬆⬆ */
    width: 36px;
    height: 36px;

    border-radius: 50%;
    pointer-events: none;

    /* Appears ABOVE the white panel */
    z-index: 999;

    opacity: 0.8;
    transform: translate(-50%, -50%);
    animation: fadeOut 1s linear forwards;
    filter: blur(4px); /* softer glow */
  }

  @keyframes fadeOut {
    0% {
      opacity: 0.8;
      transform: translate(-50%, -50%) scale(1);
    }
    100% {
      opacity: 0;
      transform: translate(-50%, -50%) scale(0.2);
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


<!-- JAVASCRIPT FOR CURSOR SWIRL + RGB TRAIL -->
<script>
  const swirl = document.getElementById("cursor-swirl");

  document.addEventListener("mousemove", (e) => {
    const x = (e.clientX / window.innerWidth) * 100;
    const y = (e.clientY / window.innerHeight) * 100;
    swirl.style.backgroundPosition = `${x}% ${y}%`;

    createGlow(e.clientX, e.clientY);
  });

  // Glow trail hue cycling
  let hue = 0;

  function createGlow(x, y) {
    const dot = document.createElement("div");
    dot.className = "glow-dot";

    dot.style.left = x + "px";
    dot.style.top = y + "px";

    /* RGB color cycle */
    dot.style.background = `radial-gradient(circle, hsl(${hue}, 100%, 75%), transparent 70%)`;

    hue = (hue + 15) % 360;

    document.body.appendChild(dot);

    setTimeout(() => dot.remove(), 1000);
  }
</script>


<!-- MAIN CONTENT WRAPPER -->
<div style="background-color: #ffffff; min-height: 100vh; padding: 20px 0; position: relative; z-index: 1;">

  <div style="max-width: 1100px; margin: 0 auto; text-align: center; display: block;">

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
