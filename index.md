<!-- GLOBAL STYLES: keep page white -->
<style>
  body {
    background-color: #ffffff !important;
    margin: 0;
    padding: 0;
  }

  /* Main neon dot following cursor */
  #cursor-dot {
    position: fixed;
    width: 42px;          /* bigger main dot */
    height: 42px;
    border-radius: 50%;
    pointer-events: none;
    z-index: 999;
    opacity: 0.9;
    transform: translate(-50%, -50%);
    filter: blur(8px);
    background: radial-gradient(circle, hsl(0, 100%, 75%), transparent 70%);
  }

  /* Trail dots */
  .trail-dot {
    position: fixed;
    width: 26px;          /* smaller than main dot */
    height: 26px;
    border-radius: 50%;
    pointer-events: none;
    z-index: 999;
    opacity: 0.6;
    transform: translate(-50%, -50%);
    filter: blur(6px);
    animation: fadeTrail 0.6s ease-out forwards;
  }

  @keyframes fadeTrail {
    0% { opacity: 0.7; transform: translate(-50%, -50%) scale(1); }
    100% { opacity: 0; transform: translate(-50%, -50%) scale(0.4); }
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
    transition: all 0.25s ease;
  }

  /* Bright color flash on hover */
  .pop-card:hover {
    background: linear-gradient(
      135deg,
      #ffd6ff,
      #c3c8ff,
      #f7e0ff,
      #ffe1fa
    );
    transform: scale(1.07);
    box-shadow: 0 0 20px rgba(176, 120, 255, 0.6);
    border-color: #b48aff;
  }
</style>

<!-- Main cursor dot -->
<div id="cursor-dot"></div>

<script>
  const cursorDot = document.getElementById("cursor-dot");
  let hue = 0;

  document.addEventListener("mousemove", (e) => {
    const x = e.clientX;
    const y = e.clientY;

    // Move main dot
    cursorDot.style.left = x + "px";
    cursorDot.style.top = y + "px";

    // Update color
    hue = (hue + 4) % 360;
    const color = `radial-gradient(circle, hsl(${hue}, 100%, 75%), transparent 70%)`;
    cursorDot.style.background = color;

    // Create trailing dot
    createTrailDot(x, y, hue);
  });

  function createTrailDot(x, y, hueValue) {
    const dot = document.createElement("div");
    dot.className = "trail-dot";

    dot.style.left = x + "px";
    dot.style.top = y + "px";

    dot.style.background = `radial-gradient(circle, hsl(${hueValue}, 100%, 75%), transparent 70%)`;

    document.body.appendChild(dot);

    setTimeout(() => dot.remove(), 600);
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
