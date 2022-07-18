<script>
	export let segment;
	let scrollY;
	let isNavActive = false
	const handleNavbar = () => {
		if(scrollY > 100) {
			isNavActive = true
		} else if (scrollY < 10){
			isNavActive = false;
		}
	}

	$: {
		scrollY
		handleNavbar()
	}
</script>

<style>
	nav {
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
		padding: 12px 20px;
		transform: translate(0%, 30%);
		transition: all 0.5s;
	}

	ul {
		display: flex;
		align-items: center;
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
		margin-right: 10px;
		font-size: 14px;
	}
	li:first-child {
		margin-right: auto;
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

</style>
<nav id="navigationBar" class:nav-active={isNavActive} class="container">
	<ul>
		<li><a aria-current="{segment === undefined ? 'page' : undefined}" href=".">Mukti Filter</a></li>
		<li><a aria-current="{segment === 'about' ? 'page' : undefined}" href="about">안전사이트</a></li>
		<li><a rel=prefetch aria-current="{segment === 'info' ? 'page' : undefined}" href="info">먹튀필터 소개</a></li>
	</ul>
</nav>

<div class="nav-alert container">선착순 혜택 신규 배너 모집 이벤트!</div>

<svelte:window bind:scrollY={scrollY} />