<script>
	import Navbar from './components/Navbar.svelte'
	import Hero from './components/Hero.svelte'
	import Footer from './components/Footer.svelte'
	import Projects from './components/Projects.svelte'
	import Contact from './components/Contact.svelte'

	let projectsSize = [0]
</script>

<header>
	<Navbar />
</header>
<div class="container-fluid main">
	<Hero />
	<Projects />
	<Contact />
</div>

<footer>
	<Footer />
</footer>

<style>
	:global(body){
		font-family: 'Poppins', sans-serif;
		background: #F8F9FC;
	}

	.main{
		background: white;
	}
</style>