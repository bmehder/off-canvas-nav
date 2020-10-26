<script>
  import Home from "./Home.svelte";
  import About from "./About.svelte";

  // Router
  let currentPage = "home";
  $: console.log(currentPage);

  const switchPage = page => {
    currentPage = page;
  };

  // Hamburger
  let isNavOpen;
  const toggleHamburgerClick = e => {
    isNavOpen = !isNavOpen;
  };
</script>

<style>
  /* Closed State Styles */
  #hamburger {
    width: 100%;
    background: darkorange;
    margin-bottom: 1em;
    padding: 10px 20px;
    display: inline-block;
    cursor: pointer;
  }

  .crown,
  .burger,
  .heel {
    width: 35px;
    height: 5px;
    background-color: #333;
    margin: 6px 0;
    transition: 0.4s;
  }

  #sidenav {
    height: 100%;
    width: 0; /* 0 width - change this with JavaScript */
    position: fixed;
    z-index: 1;
    top: 45px;
    left: 0;
    background-color: darkorange;
    overflow-x: hidden;
    padding-top: 60px;
    transition: 0.4s;
  }

  a {
    padding: 8px 8px 8px 32px;
    text-decoration: none;
    font-size: 25px;
    color: white;
    display: block;
    transition: 0.3s;
  }
  a:hover {
    color: #333;
  }

  /* Opened State Styles */
  .isNavOpen .crown {
    transform: rotate(-45deg) translate(-9px, 6px);
  }
  .isNavOpen .burger {
    opacity: 0;
  }
  .isNavOpen .heel {
    transform: rotate(45deg) translate(-8px, -8px);
  }

  main {
    padding: 0 8em;
    transition: margin-left 0.5s;
  }
  .isNavOpen main {
    margin-left: 20%;
  }
  .isNavOpen #sidenav {
    width: 20% !important;
  }

  @media screen and (max-width: 450px) {
    #sidenav {
      padding-top: 15px;
    }
    a {
      font-size: 18px;
    }
    .isNavOpen {
      margin-left: 100%;
    }
  }
</style>

<div class:isNavOpen>
  <div id="hamburger" on:click={toggleHamburgerClick}>
    <div class="crown" />
    <div class="burger" />
    <div class="heel" />
  </div>

  <div id="sidenav">
    <a
      href="#home"
      on:click|preventDefault={() => {
        switchPage('home');
      }}>
      Home
    </a>
    <a
      href="#about"
      on:click|preventDefault={() => {
        switchPage('about');
      }}>
      About
    </a>
    <a href="#services">Services</a>
    <a href="#clients">Clients</a>
    <a href="#contact">Contact</a>
  </div>

  <section>
    <main>
      <!-- Home Section -->
      {#if currentPage === 'home'}
        <Home />
      {/if}

      <!-- About Section -->
      {#if currentPage === 'about'}
        <About />
      {/if}

    </main>
  </section>
</div>
