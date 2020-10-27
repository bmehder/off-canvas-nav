<script>
  import Home from "./Home.svelte";
  import About from "./About.svelte";
  import Services from "./Services.svelte";
  import Clients from "./Clients.svelte";
  import Contact from "./Contact.svelte";
  import Footer from "./Footer.svelte";

  // Router
  const pages = ["home", "about", "services", "clients", "contact"];
  let currentPage = pages[0];
  const switchPage = i => {
    currentPage = pages[i];
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
    position: sticky;
    top: 0;
    width: 100%;
    height: 10vh;
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
    /* z-index: 1; */
    top: 10%;
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
    text-transform: capitalize;
    transition: 0.3s;
  }
  a:hover,
  .active {
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
    padding: 0 8em 10%;
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
      margin-left: 20%;
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
    {#each pages as page, i}
      <a
        href={page}
        on:click|preventDefault={() => {
          switchPage(i);
        }}
        class:active={currentPage === page}>
        {page}
      </a>
    {/each}
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

      <!-- Services Section -->
      {#if currentPage === 'services'}
        <Services />
      {/if}

      <!-- Clients Section -->
      {#if currentPage === 'clients'}
        <Clients />
      {/if}

      <!-- Contact Section -->
      {#if currentPage === 'contact'}
        <Contact />
      {/if}
    </main>
  </section>
  <!-- Footer -->
  <Footer />
</div>
