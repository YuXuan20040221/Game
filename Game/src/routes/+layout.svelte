<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="app" style="margin: 0%;padding:0%">
	<Header />

	<main>
		<slot />
	</main>

	<footer>
		
	</footer>
</div>

<style>
	
</style>
