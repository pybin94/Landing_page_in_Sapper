<script>
	import {onMount} from 'svelte'

	onMount(() => {
		let card = document.querySelectorAll('.card')
		console.log(card.length)

		setTimeout(() => { 
			for(var i =0 ; i < card.length; i++) {
				card[i].classList.remove("preShow")
			}
		},2000);
	})



</script>

<style>
	h1, figure, p {
		text-align: center;
		margin: 0 auto;
	}

	h1 {
		font-size: 2.8em;
		text-transform: uppercase;
		font-weight: 700;
		margin: 0 0 0.5em 0;
	}

	figure {
		margin: 0 0 1em 0;
	}

	p {
		margin: 1em auto;
	}

	ul {
		display: flex;
		flex-wrap: wrap;
		margin: 20px 0;
	}

	.card {
		position: relative;
		width: 400px;
		height: 100px;
		margin: 20px;
		border: 1px solid #fff;
		background-color: #fff;
		cursor: pointer;
		overflow: hidden
	}
	.card-top {
		position: absolute;
		top: 0;
		left: 0;
		transition: all 0.3s;
	}
	.card:hover .card-top{
		opacity: 0;
	}
	.card-bottom {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: #00ffaa;
		transition: all 0.3s;
		opacity: 0;
	}
	.card:hover .card-bottom {
		margin-top: 0;
		opacity: 1;
	}
	.card-bottom p {
		margin-top: -5px;
		transition: all 0.3s;
	}
	.card:hover .card-bottom p {
		margin-top: 0;
	}
	.card:nth-child(2n-1) {
		margin-top: -20px;
	}

	.preShow {
		position: relative;
		opacity: 0;
		will-change: transform;
		transform: translateX(-30px);
		animation: preShow 1.8s cubic-bezier(0.19, 1, 0.22, 1) forwards;
	}
	.preShow:before {
		content: "";
		z-index: 999;
		position: absolute;
		left: 0;
		top: 0;
		display: block;
		width: 100%;
		height: 100%;
		background-color: #1c2c42;
		transform-origin: right;
		will-change: transform;
		animation-delay: 1s;
		animation: preShowMove 1.8s cubic-bezier(0.19, 1, 0.22, 1) forwards;
	}


	@keyframes preShowMove {
		to {
			transform: scaleX(0);
		}
	}

	@keyframes preShow {
		0% {
			box-shadow: none;
			
		}
		60% {
			box-shadow: none;
			opacity: 1;
			transform: translateX(0);
		}
		100% {
			opacity: 1;
			transform: translateX(0);
		}
	}


	@media (min-width: 480px) {
		h1 {
			font-size: 4em;
		}
	}
</style>

<svelte:head>
	<title>Sapper project template</title>
</svelte:head>

<h1>Great success!</h1>

<figure>
	<ul>
		<li class="card preShow">
			<div class="card-top"><img src="" alt="dlalwl"></div>
			<div class="card-bottom">
				<p>DeepKnow</p>
				<p>
				Interactive safety autoimmune system based on full link
				</p>
			</div>
		</li>
		<li class="card preShow">
			<div class="card-top"><img src="" alt="dlalwl"></div>
			<div class="card-bottom">
				<p>DeepKnow</p>
				<p>
				Interactive safety autoimmune system based on full link
				</p>
			</div>
		</li>
		<li class="card preShow">
			<div class="card-top"><img src="" alt="dlalwl"></div>
			<div class="card-bottom">
				<p>DeepKnow</p>
				<p>
				Interactive safety autoimmune system based on full link
				</p>
			</div>
		</li>
		<li class="card preShow">
			<div class="card-top"><img src="" alt="dlalwl"></div>
			<div class="card-bottom">
				<p>DeepKnow</p>
				<p>
				Interactive safety autoimmune system based on full link
				</p>
			</div>
		</li>
		<li class="card preShow">
			<div class="card-top"><img src="" alt="dlalwl"></div>
			<div class="card-bottom">
				<p>DeepKnow</p>
				<p>
				Interactive safety autoimmune system based on full link
				</p>
			</div>
		</li>
		<li class="card preShow">
			<div class="card-top"><img src="" alt="dlalwl"></div>
			<div class="card-bottom">
				<p>DeepKnow</p>
				<p>
				Interactive safety autoimmune system based on full link
				</p>
			</div>
		</li>
	</ul>
	<figcaption>Have fun with Sapper!</figcaption>
</figure>

<p><strong>Try editing this file (src/routes/index.svelte) to test live reloading.</strong></p>
