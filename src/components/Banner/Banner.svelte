<script>
	import {premiums, newBanners, banners} from "./banners.json"
    import {onMount} from 'svelte'

    onMount(() => {
		let card = document.querySelectorAll('.card')

		setTimeout(() => { 
			for(let i = 0 ; i < card.length; i++) {
				card[i].classList.remove("preShow")
			}
		},2000);
	})
</script>

<style>
    	ul {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;

	}

	.card {
		position: relative;
		width: 400px;
		height: 100px;
		margin: 20px;
		cursor: pointer;
		overflow: hidden;
	}

	.card-top {
		position: absolute;
		top: 0;
		left: 0;
		transition: all 0.3s;
	}

	.card-top img {
		width: 100%;
    	height: 100%;
	}

	.card-bottom {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: linear-gradient(to bottom, #28356B, #2f3d72);
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

	.banners {
		margin-top: 60px;
	}

	.banner:nth-child(2n-1) {
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
</style>

<ul class="premiums">
    {#each premiums as premium}
    <li class="card premium preShow shadow">
        <a href="{premium.href}">
            <div class="card-top">
                <img src="{premium.src}" alt="{premium.alt}">
            </div>
            <div class="card-bottom">
                <h5>{premium.title}</h5>
                <p>{premium.content}</p>
            </div>
        </a>
    </li>
    {/each}
</ul>
<h2>New Banners!</h2>
<ul class="newBanners">
    {#each newBanners as newBanner}
    <li class="card newBanner preShow shadow">
        <a href="{newBanner.href}">
            <div class="card-top">
                <img src="{newBanner.src}" alt="{newBanner.alt}">
            </div>
            <div class="card-bottom">
                <h5>{newBanner.title}</h5>
                <p>{newBanner.content}</p>
            </div>
        </a>
    </li>
    {/each}
</ul>
<div class="br"></div>
<h2>Banners!</h2>
<ul class="banners">
    {#each banners as banner}
        <li class="card banner preShow shadow">
            <a href="{banner.href}">
                <div class="card-top">
                    <img src="{banner.src}" alt="{banner.alt}">
                </div>
                <div class="card-bottom">
                    <h5>{banner.title}</h5>
                    <p>{banner.content}</p>
                </div>
            </a>
        </li>
    {/each}
</ul>