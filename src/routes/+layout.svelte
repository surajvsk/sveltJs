<script>
	import Header from '../Components/Navbar.svelte';
</script>

<div class="app">
	<Header />
	<main>
		<slot />
	</main>

	<footer>
		<p>This is footer</p>
	</footer>
</div>
