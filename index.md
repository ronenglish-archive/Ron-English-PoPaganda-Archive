<!-- GLOBAL STYLES: keep page white -->
<style>
  body {
    background-color: #ffffff !important;
    margin: 0;
    padding: 0;
  }

  /* Cursor effects sit behind content */
  #cursor-dot,
  .trail-dot {
    pointer-events: none;
    z-index: 0;
  }

  /* Main neon dot following cursor */
  #cursor-dot {
    position: fixed;
    width: 42px;
    height: 42px;
    border-radius: 50%;
    opacity: 0.9;
    transform: translate(-50%, -50%);
    filter: blur(8px);
    background: radial-gradient(circle, hsl(0, 100%, 75%), transparent 70%);
  }

  /* Trail dots */
  .trail-dot {
    position: fixed;
    width: 26px;
    height: 26px;
    border-radius: 50%;
    opacity: 0.6;
    transform: translate(-50%, -50%);
    filter: blur(6px);
    animation: fadeTrail 0.6s ease-out forwards;
  }

  @keyframes fadeTrail {
    0% { opacity: 0.7; transform: translate(-50%, -50%) scale(1); }
    100% { opacity: 0; transform: translate(-50%, -50%) scale(0.4); }
  }

  /* Page layout */
  .page-wrap {
    background-color: #ffffff;
    min-height: 100vh;
    padding: 20px 0 60px;
    position: relative;
    z-index: 1; /* content above cursor effects */
  }

  .container {
    max-width: 1100px;
    margin: 0 auto;
    padding: 0 18px;
  }

  /* Banner */
  .banner {
    width: 100%;
    height: auto;
    border-radius: 12px;
    display: block;
    margin: 0 auto 22px;
    border: 1px solid rgba(0,0,0,0.08);
  }

  /* 4-card grid */
  .card-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 18px;
    margin-top: 10px;
  }

  @media (max-width: 860px) {
    .card-grid { grid-template-columns: 1fr; }
  }

  /* Card */
  .section-card {
    background: #ffffff;
    border: 1px solid #e6e6e6;
    border-radius: 16px;
    overflow: hidden;
    text-align: left;
    box-shadow: 0 10px 30px rgba(0,0,0,0.06);
    transition: transform 0.14s ease, box-shadow 0.14s ease, border-color 0.14s ease;
  }

  .section-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 16px 42px rgba(0,0,0,0.10);
    border-color: #d8d8d8;
  }

  /* Square image */
  .card-media {
    width: 100%;
    aspect-ratio: 1 / 1;
    background: #f2f2f2;
    border-bottom: 1px solid #e6e6e6;
  }

  .card-media img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }

  .card-body {
    padding: 16px 16px 18px;
  }

  .card-title {
    margin: 0 0 6px;
    font-size: 20px;
    line-height: 1.15;
    color: #111;
  }

  .card-desc {
    margin: 0 0 14px;
    font-size: 15px;
    line-height: 1.35;
    color: #444;
    max-width: 65ch;
  }

  /* Action links (more noticeable) */
  .action-row {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .action-link {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 10px 14px;
    border-radius: 999px;
    border: 1px solid #c7b4ff;
    background: #e5e0ff;
    color: #000;
    text-decoration: none;
    font-weight: 750;
    letter-spacing: 0.01em;
    transition: transform 0.14s ease, box-shadow 0.14s ease, background 0.14s ease;
  }

  .action-link:hover {
    background: linear-gradient(135deg, #ffd6ff, #c3c8ff, #f7e0ff, #ffe1fa);
    transform: scale(1.03);
    box-shadow: 0 0 18px rgba(176, 120, 255, 0.45);
  }

  .action-dot {
    width: 10px;
    height: 10px;
    border-radius: 999px;
    background: #000;
    display: inline-block;
  }

  /* Sub-actions */
  .sub-row {
    margin-top: 10px;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .sub-link {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 8px 12px;
    border-radius: 999px;
    border: 1px solid rgba(0,0,0,0.14);
    background: #fff;
    color: #111;
    text-decoration: none;
    font-weight: 650;
  }

  .sub-link:hover {
    border-color: rgba(0,0,0,0.22);
    box-shadow: 0 10px 20px rgba(0,0,0,0.06);
  }

  .sub-dot {
    width: 8px;
    height: 8px;
    border-radius: 999px;
    background: #111;
    display: inline-block;
  }
</style>

<!-- Main cursor dot -->
<div id="cursor-dot"></div>

<script>
  const cursorDot = document.getElementById("cursor-dot");
  let colorAngle = 0;

  document.addEventListener("mousemove", (e) => {
    const x = e.clientX;
    const y = e.clientY;

    cursorDot.style.left = x + "px";
    cursorDot.style.top = y + "px";

    colorAngle = (colorAngle + 4) % 360;
    const gradient = `radial-gradient(circle, hsl(${colorAngle}, 100%, 75%), transparent 70%)`;
    cursorDot.style.background = gradient;

    createTrailDot(x, y, colorAngle);
  });

  function createTrailDot(x, y, angleValue) {
    const dot = document.createElement("div");
    dot.className = "trail-dot";
    dot.style.left = x + "px";
    dot.style.top = y + "px";
    dot.style.background = `radial-gradient(circle, hsl(${angleValue}, 100%, 75%), transparent 70%)`;
    document.body.appendChild(dot);
    setTimeout(() => dot.remove(), 600);
  }
</script>

<div class="page-wrap">
  <div class="container">

    <!-- BANNER -->
    <img
      src="images/Banner2.jpg"
      alt="POPaganda Archive banner"
      class="banner"
    />

    <!-- 4 SECTION CARDS -->
    <div class="card-grid" aria-label="PoPaganda archive sections">

      <!-- Exhibitions -->
      <section class="section-card">
        <div class="card-media">
          <img src="images/entry-exhibitions.jpg" alt="Exhibitions section image" />
        </div>
        <div class="card-body">
          <h2 class="card-title">Exhibitions</h2>
          <p class="card-desc">Solo and group exhibitions organized by decade.</p>

          <div class="action-row">
            <a class="action-link" href="exhibitions/solo-exhibitions.html">
              <span class="action-dot"></span>
              Enter exhibitions
            </a>
          </div>

          <div class="sub-row">
            <a class="sub-link" href="exhibitions/solo-exhibitions.html">
              <span class="sub-dot"></span> Solo
            </a>
            <a class="sub-link" href="exhibitions/group-exhibitions.html">
              <span class="sub-dot"></span> Group
            </a>
          </div>
        </div>
      </section>

      <!-- Murals -->
      <section class="section-card">
        <div class="card-media">
          <img src="images/entry-murals.jpg" alt="Murals and street works section image" />
        </div>
        <div class="card-body">
          <h2 class="card-title">Murals and Street Works</h2>
          <p class="card-desc">Public murals, street pieces, and related documentation.</p>

          <div class="action-row">
            <a class="action-link" href="murals-and-street-works.html">
              <span class="action-dot"></span>
              Enter murals
            </a>
          </div>
        </div>
      </section>

      <!-- Events -->
      <section class="section-card">
        <div class="card-media">
          <img src="images/entry-events.jpg" alt="Events and appearances section image" />
        </div>
        <div class="card-body">
          <h2 class="card-title">Public Appearances and Events</h2>
          <p class="card-desc">Talks, lectures, signings, benefits, and special events.</p>

          <div class="action-row">
            <a class="action-link" href="special-events-parties-tours.html">
              <span class="action-dot"></span>
              Enter events
            </a>
          </div>

          <div class="sub-row">
            <a class="sub-link" href="public-talks-lectures-book-signings.html">
              <span class="sub-dot"></span> Talks
            </a>
            <a class="sub-link" href="benefit-auctions-charity-projects.html">
              <span class="sub-dot"></span> Benefits
            </a>
            <a class="sub-link" href="special-events-parties-tours.html">
              <span class="sub-dot"></span> Special
            </a>
          </div>
        </div>
      </section>

      <!-- Projects -->
      <section class="section-card">
        <div class="card-media">
          <img src="images/entry-projects.jpg" alt="Projects and media section image" />
        </div>
        <div class="card-body">
          <h2 class="card-title">Projects and Media</h2>
          <p class="card-desc">Pop-ups, brand activations, film events, and digital projects.</p>

          <div class="action-row">
            <a class="action-link" href="digital-projects-nft-crypto-art.html">
              <span class="action-dot"></span>
              Enter projects
            </a>
          </div>

          <div class="sub-row">
            <a class="sub-link" href="pop-ups-shops-brand-activations.html">
              <span class="sub-dot"></span> Pop-ups
            </a>
            <a class="sub-link" href="film-screenings-festivals-film-events.html">
              <span class="sub-dot"></span> Film
            </a>
            <a class="sub-link" href="digital-projects-nft-crypto-art.html">
              <span class="sub-dot"></span> Digital
            </a>
          </div>
        </div>
      </section>

    </div>
  </div>
</div>
