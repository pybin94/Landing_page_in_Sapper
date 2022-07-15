<script>
	export let segment;
	let scrollHeight;
	let isNavActive = false
	const handleNavbar = () => {
		if(scrollHeight > 100) {
			isNavActive = true
		} else if (scrollHeight < 10){
			isNavActive = false;
		}
	}

	$: {
		scrollHeight
		handleNavbar()
	}
</script>

<style>
	nav {
		width: 1000px;
		margin: 0 auto;
		position: fixed;
		border-radius: 16px;
		top: 0;
		left: 0;
		right: 0;
		transform: translate(0%, 0%);
		font-weight: 300;
		padding: 0 1em;
		transition: all 0.5s;
	}

	.nav-active {
		position: fixed;
		background-color: rgba(255, 255, 255, 0.9);
		box-shadow: 0px 7px 15px -6px #cdcdcd;
		color: #333;
		z-index: 100;
		width: 800px;
		margin: 0 auto;
		top: 0;
		left: 0;
		right: 0;
		transform: translate(0%, 30%);
		transition: all 0.5s;
	}

	ul {
		margin: 0;
		padding: 0;
	}

	/* clearfix */
	ul::after {
		content: '';
		display: block;
		clear: both;
	}

	li {
		display: block;
		float: left;
	}


	[aria-current] {
		position: relative;
		display: inline-block;
	}

	[aria-current]::after {
		position: absolute;
		content: '';
		width: calc(100% - 1em);
		height: 2px;
		color: #000;
		display: block;
		bottom: -1px;
	}

	a {
		text-decoration: none;
		padding: 1em 0.5em;
		display: block;
	}

	@keyframes animatedgradient {
		0% {
			background-position: 0% 50%;
		}
		50% {
			background-position: 100% 50%;
		}
		100% {
			background-position: 0% 50%;
		}
	}

</style>
<nav id="navigationBar" class:nav-active={isNavActive}>
	<ul>
		<li><img src="" alt=""></li>
		<li><a aria-current="{segment === undefined ? 'page' : undefined}" href=".">home</a></li>
		<li><a aria-current="{segment === 'about' ? 'page' : undefined}" href="about">about</a></li>

		<!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
		     the blog data when we hover over the link or tap it on a touchscreen -->
		<li><a rel=prefetch aria-current="{segment === 'blog' ? 'page' : undefined}" href="blog">blog</a></li>
	</ul>
</nav>

<svelte:window bind:scrollY={scrollHeight} />