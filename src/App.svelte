<script>
  import Navbar from "./components/Navbar.svelte";
  import Hero from "./components/Hero.svelte";
  import Footer from "./components/Footer.svelte";
  import Intro from "./components/Intro.svelte";
  import Projects from "./components/Projects.svelte";
  import Contact from "./components/Contact.svelte";

  let projectsSize = [0];
  let dark = false;
</script>

{#if !dark}
  <style>
    :global(body) {
      font-family: "Poppins", sans-serif;
      /* background: #f8f9fc; */
      background: #f8f9fc;
    }

    .main {
      background: white;
    }
  </style>
{:else}
  <style>
    body {
      background: black;
    }
  </style>
{/if}

<header>
  <Navbar />
</header>
<div class="container-fluid main">
  <Hero />
  <Projects />
  <!-- <Intro /> -->
  <Contact />
</div>

<footer>
  <Footer />
</footer>
