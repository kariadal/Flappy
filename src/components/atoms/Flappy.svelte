<script>
    import { position } from "../../model";

    let screenHeight = 0;
    let y = window.innerHeight / 2;
    let x = window.innerWidth / 1.5;
    export let color = "red";
    
    setInterval(() => {
        if (y < screenHeight) {
            y++;
        }
    }, 10);

    function fly() {
        y -= 100
    }

    function handleKeydown() {
        fly()
    }

    $: $position = { x, y }
</script>

<svelte:window on:keydown={handleKeydown} bind:innerHeight={screenHeight}/>

<div
    class="fixed w-12 h-12 rounded-full transition z-2 top-0 left-0"
    style:transform="translate({x}px, {y}px)" style:background={color}
/>
