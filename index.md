<!-- Swirly animated background -->
<style>
  .swirl-bg {
    position: fixed;
    inset: 0;
    z-index: -1;
    background:
      radial-gradient(circle at 0% 0%, #ffd6ff 0, transparent 55%),
      radial-gradient(circle at 100% 0%, #c3e7ff 0, transparent 55%),
      radial-gradient(circle at 0% 100%, #fff1b8 0, transparent 55%),
      radial-gradient(circle at 100% 100%, #d5b8ff 0, transparent 55%);
    background-size: 200% 200%;
    animation: swirl-bg-move 30s ease-in-out infinite;
    opacity: 0.35; /* strength of the color burst */
    pointer-events: none;
  }

  @keyframes swirl-bg-move {
    0% {
      background-position: 0% 0%;
    }
    50% {
      background-position: 100% 100%;
    }
    100% {
      background-position: 0% 0%;
    }
  }

  .pop-card {
    padding: 16px 12px;
    background: #e5e0ff; /* soft purple base */
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

<div class="swirl-bg"></div>

<!-- Main page content on top of the swirl -->
<div style="background-color: #ffffff; min-height: 100vh; padding: 20px 0;">

  <!-- Centered content wrapper -->
  <div style="max-width: 1100px; margin: 0 auto; text-align: center; display: block;">

    <!-- Banner -->
    <img src="images/Banner2.jpg"
         alt="POPaganda Archive banner"
         style="width: 100%; height: auto; border-radius: 8px; margin-bottom: 32px;" />

    <!-- Responsive Grid -->
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

    </div> <!-- end grid -->

  </div> <!-- end centered content wrapper -->
</div> <!-- end white background wrapper -->
