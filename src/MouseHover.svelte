<script>
import { noop } from "svelte/internal";


    let m = {x:0, y:0};
    let lightElement;
    let overlayElement;


    $: overlayElement && overlayElement.style.setProperty('display', 'none')
    $: lightElement && lightElement.style.setProperty('background', 'radial-gradient(circle at ' + m.x + 'px ' + m.y + 'px, transparent, #000 10%)')
</script>

<style>
    section {
    position: relative;
    width: 100%;
    height: 100vh;
    background: url('https://images.pexels.com/photos/414612/pexels-photo-414612.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260');
    background-size: cover;
    overflow: hidden;
    }
    .overlay {
    background: #000;
    width: 100%;
    height: 100vh;
    /* display: none; */
    }
    .light {
    position: absolute;
    width: 100%;
    height: 100%;
    }
</style>
<div>
    <h1>MOUSE HOVER FLASH LIGHT TEST</h1>
    The section mouse position is x: {m.x} y: {m.y}
    <section on:mousemove="{e => m = {x: e.clientX - e.currentTarget.getBoundingClientRect().x, 
        y: e.clientY - e.currentTarget.getBoundingClientRect().y}}">
        <div class="overlay" bind:this={overlayElement}></div>
        <div class="light" bind:this={lightElement}></div>
    </section>
</div>