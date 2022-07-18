<script>
    import Fa from 'svelte-fa';
    import { faCompassDrafting, faFishFins } from '@fortawesome/free-solid-svg-icons';
    import {  } from '@fortawesome/free-brands-svg-icons';
</script>

<style>
    .bar {
        display: flex;
        align-items: center;
        color: #69faaa;
        padding: 20px 0;
    }
    .contour-line {
        background: linear-gradient(to right, #69faaa, #81f5b5);
        margin-left: 20px;
        width: 100%;
        height: 5px;
        border-radius: 20px 100px;
    }
</style>

<div class="bar container">
    <div>
        <Fa icon={faFishFins} />
    </div>
    <div class="contour-line"></div>
</div>