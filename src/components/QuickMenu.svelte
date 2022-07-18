<script>
    import Fa from 'svelte-fa';
    import { faCircleArrowUp } from '@fortawesome/free-solid-svg-icons';
    import { faTelegram } from '@fortawesome/free-brands-svg-icons';
</script>

<style>
    .quick-menu {
        position: fixed;
        border-radius: 100%;
        padding: 0;
        border: none;
        z-index: 100;
        cursor: pointer;
    }
    .telegram-button {
        bottom: 14%;
        right: 10%;
    }
    .top-button {
        bottom: 5%;
        right: 10%;
    }

    .button-icon {
        font-size: 55px;
        border-radius: 100%;
        line-height: 0;
        animation: animatedgradient 3s alternate infinite;
        z-index: 100;
    }

    .spinner {
        position: absolute;
        top: 0;
        left: 0;
        margin: 0 auto;
        width: 54px;
        height: 56px;
        border:solid #dedef7;
        animation: spin 1s ease infinite;
        border-radius: 50%;
        box-shadow: 0px 0px 11px 2px #d8deff;
    }

    @keyframes spin {
        0% { transform: rotate(0deg); }
        100% { transform: rotate(360deg); }
    }

    @keyframes animatedgradient {
		0% {
			color: #f79533;
		}
		50% {
			color: #f37055;
		}
		100% {
			color: #ef4e7b;
		}
	}
</style>

<button class="quick-menu telegram-button">
    <a href="/">
        <div class="spinner"></div>
        <span class="button-icon">
            <Fa icon={faTelegram} />
        </span>
    </a>
</button>
<button class="quick-menu top-button" on:click={() => {window.scrollTo(0,0)}}>
    <div class="spinner"></div>
    <span class="button-icon">
        <Fa icon={faCircleArrowUp} />
    </span>
</button>
