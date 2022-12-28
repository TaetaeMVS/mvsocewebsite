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
          <li><a>Item 1</a></li>
          <li tabindex="0">
            <a>
              Parent
              <svg class="fill-current" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24"><path d="M7.41,8.58L12,13.17L16.59,8.58L18,10L12,16L6,10L7.41,8.58Z"/></svg>
            </a>
            <ul class="p-2 bg-base-100">
              <li><a>Submenu 1</a></li>
              <li><a>Submenu 2</a></li>
            </ul>
          </li>
          <li><a>Item 3</a></li>
        </ul>
      </div>
    </div>
    <div class="max-w-md">
      <h1 class="mb-5 text-5xl font-bold">Join Multiversus OCE</h1>
      <p class="mb-5"></p>
      <button class="btn btn-primary">Get Started</button>
    </div>
  </div>
</div>