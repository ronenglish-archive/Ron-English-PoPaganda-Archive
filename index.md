<!-- GLOBAL STYLES: keep page white -->
<style>
  body {
    background-color: #ffffff !important;
    margin: 0;
    padding: 0;
  }

  /* Comet streak particles */
  .comet {
    position: fixed;
    pointer-events: none;
    z-index: 999;              /* above everything */
    border-radius: 999px;
    opacity: 0.9;
    transform: translate(-50%, -50%);
    animation: cometFade 0.6s ease-out forwards;
    filter: blur(2px);         /* softer neon edge */
  }

  @keyframes cometFade {
    0% {
      opacity: 0.9;
      transform: translate(-50%, -50%) scale(1);
    }
    100% {
      opacity: 0;
      transform: translate(-50%, -50%) scale(0.5);
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

<script>
  let lastX = null;
  let lastY = null;
  let hue = 0;

  document.addEventListener("mousemove", (e) => {
    const x = e.clientX;
    const y = e.clientY;

    if (lastX === null || lastY === null) {
      lastX = x;
      lastY = y;
      return;
    }

    const dx = x - lastX;
    const dy = y - lastY;
    const dist = Math.sqrt(dx * dx + dy * dy);

    // Skip if barely moving (prevents too many tiny streaks)
    if (dist < 2) {
      lastX = x;
      lastY = y;
      return;
    }

    const angle = Math.atan2(dy, dx) * (180 / Math.PI);

    createComet(x, y, dist, angle);

    lastX = x;
    lastY = y;
  });

  function createComet(x, y, dist, angle) {
    const comet = document.createElement("div");
    comet.className = "comet";

    // Length scales with speed, clamped to reasonable range
    const baseLength = 40;
    const maxExtra = 100;
    const length = baseLength + Math.min(dist * 1.5, maxExtra);
    const thickness = 6;

    comet.style.width = length + "px";
    comet.style.height = thickness + "px";

    comet.style.left = x + "px";
    comet.style.top = y + "px";

    // Color cycles through RGB spectrum
    const currentHue = hue;
    hue = (hue + 12) % 360;

    comet.style.background = `linear-gradient(90deg,
      hsla(${currentHue}, 100%, 70%, 0) 0%,
      hsla(${currentHue}, 100%, 70%, 0.1) 20%,
      hsla(${currentHue}, 100%, 70%, 0.8) 60%,
      hsla(${currentHue}, 100%, 80%, 1) 100%
    )`;

    comet.style.transform = `translate(-50%, -50%) rotate(${angle}deg)`;

    document.body.appendChild(comet);

    setTimeout(() => {
      comet.remove();
    }, 600);
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
