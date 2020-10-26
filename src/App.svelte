<script>
  let isNavOpen;

  const toggleHamburgerClick = e => {
    isNavOpen = !isNavOpen;
  };
</script>

<style>
  /* Closed State Styles */
  section {
    margin: 0;
  }
  #hamburger {
    width: 100%;
    background: darkorange;
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

  main {
    transition: margin-left 0.5s;
    padding: 2em 4em;
  }
  p {
    min-width: 300px;
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

<section class:isNavOpen>
  <div id="hamburger" on:click={toggleHamburgerClick}>
    <div class="crown" />
    <div class="burger" />
    <div class="heel" />
  </div>

  <div id="sidenav">
    <a href=".">Home</a>
    <a href="#b">About</a>
    <a href="#c">Services</a>
    <a href="#d">Clients</a>
    <a href="#e">Contact</a>
  </div>

  <main>
    <h2>Off-Canvas Nav</h2>
    <p>
      Lorem ipsum, dolor sit amet consectetur adipisicing elit. Illum quod
      obcaecati voluptatibus exercitationem non odio? Ducimus maxime repellat
      incidunt ad maiores quis ab porro doloribus cum nobis quidem architecto
      delectus, ipsam consequatur.
    </p>
  </main>
</section>
