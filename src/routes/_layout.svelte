<script>
	import Nav from '../components/Nav.svelte';
	import QuickMenu from '../components/QuickMenu.svelte';
	import Footer from '../components/Footer.svelte';
	export let segment;

</script>

<style>

</style>

<Nav {segment}/>
<QuickMenu />
<main class="container">	
	<slot></slot>
</main>
	<Footer />