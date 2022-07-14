<script>
	import Nav from '../components/Nav.svelte';
	import QuickMenu from '../components/QuickMenu.svelte';

	export let segment;

</script>

<style>
	main {
		top: 56px;
		position: relative;
		max-width: 56em;
		margin: 0 auto;
		height: 200vh;
	}

</style>

<Nav {segment}/>
<QuickMenu />
<main>	
	<slot></slot>
</main>

