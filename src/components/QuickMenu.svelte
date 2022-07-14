<script>
    import  Fa  from  'svelte-fa' 
    import  {  }  from  '@fortawesome/free-solid-svg-icons' 
    import  {  faTelegram  }  from  '@fortawesome/free-brands-svg-icons' ; 
</script>

<style>
    .telegram-button {
        position: fixed;
        bottom: 10%;
        right: 10%;
        border-radius: 100%;
        padding: 0;
        border: none;
    }

    .telegram-icon {
        width: 60px;
        height: 60px;
        font-size: 60px;
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
        width: 58px;
        height: 60px;
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

<button class="telegram-button">
    <a href="/">
        <div class="spinner"></div>
        <span class="telegram-icon">
            <Fa icon={faTelegram} />
        </span>
    </a>
</button>