<script>
	
	import {lists} from "./Nav.json"
	let scrollY;
	let isNavActive = false
	const handleNavbar = () => {
		if(scrollY > 100) {
			isNavActive = true
		} else if (scrollY < 10){
			isNavActive = false;
		}
	}
	export let segment;

	$: {
		scrollY
		handleNavbar()
	}
</script>

<style>
	nav {
		padding: 0 20px;
	}
	.nav-bar {
		position: fixed;
		border-radius: 16px;
		margin-top: 35px;
		top: 0;
		left: 0;
		right: 0;
		transform: translate(0%, 0%);
		font-weight: 300;
		transition: all 0.5s;
		z-index: 100;
		display: flex;
		align-items: center;
		padding: 0;
	}

	.nav-active {
		position: fixed;
		background-color: rgba(255, 255, 255, 0.9);
		box-shadow: 0px 7px 15px -6px #cdcdcd;
		color: #333;
		z-index: 100;
		max-width: 800px;
		margin: 0 auto;
		top: 0;
		left: 0;
		right: 0;
		padding: 12px 20px;
		transform: translate(0%, 30%);
		transition: all 0.5s;
	}

	li {
		margin-left: 10px;
		font-size: 14px;
	}
	li:first-child {
		margin: 0 auto 0 0;
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
		display: block;
	}

	.nav-alert {
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: #666666;
		border-radius: 5px;
		margin: 70px auto 20px;
		padding: 10px 0;
		text-align: center;
		font-size: 14px;
		z-index: 100;
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


	@media (max-width: 1024px) {
		.nav-active  {
			max-width: 700px;
		}
		.nav-bar {
			padding: 10px 20px;
		}
	}
	@media (max-width: 768px) {
		.nav-active  {
			max-width: 550px;
		}
	}
	@media (max-width: 480px) {
		.nav-active  {
			max-width: 340px;
		}
	}

</style>
<nav>
	<ul id="navigationBar" class:nav-active={isNavActive} class="nav-bar container">
		{#each lists as list}
			<li><a aria-current="{segment === list.segment ? 'page' : undefined}" href="{list.href}">{list.name}</a></li>
		{/each}
	</ul>
	<div class="nav-alert container"><a href="/safety">안전사이트</a>&nbsp;<p>모집! 선착순 혜택 신규 배너 이벤트!</p></div>
</nav>


<svelte:window bind:scrollY={scrollY} />