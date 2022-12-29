<style>
.navbar {
  position: fixed; /* Fixes the navbar to the top of the page */
  top: 0; /* Positions the navbar at the top of the page */
  left: 0; /* Positions the navbar at the left side of the page */
  right: 0; /* Takes up the full width of the page */
  z-index: 1; /* Ensures that the navbar is displayed above other elements on the page */
  background-color: transparent;
}
a.top-left {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 2;
  width: 10%;
  height: 10%;
}
</style>



<div class="hero min-h-screen" style="background-image: url('../spacejam.jpg');">
  <div class="hero-overlay bg-opacity-0"></div>
  <div class="hero-content text-center text-neutral-content">
    <div class="navbar bg-base-100">
      <div class="flex-1">
        <a class="btn btn-ghost normal-case text-xl top-left">
          <img src="../multiversusocetransparent.png" alt="Multiversus OCE logo">
        </a>
      </div>
      <div class="flex-none">
        <ul class="menu menu-horizontal px-1">
          <li><a href="https://twitter.com/multiversus_oce" target="_blank" class="text-blue-300 font-bold">Twitter</a></li>
          <li><a href="https://www.twitch.tv/multiversus_oce" target="_blank" class="text-purple-500 font-bold">Twitch</a></li>
          <li><a>Coming Soon...</a></li>
        </ul>
      </div>
    </div>
    <div class="max-w-2xl">
      <h1 class="mb-5 text-6xl font-bold">Join MultiVersus OCE</h1>
      <h2 class="mb-5 text-2xl font-bold">We host weekly tournaments. Join our friendly, active community today!</h2>
      <p class="mb-5"></p>
      <a href="https://discord.gg/mvsoce" target="_blank" class="btn btn-primary">MVSOCE Discord</a>
    </div>
  </div>
</div>