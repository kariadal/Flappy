<script>
    import Tube from "../atoms/Tube.svelte";

    let screenWidth = 0;
    let list = [1, 2, 3, 4, 5]

</script>

<svelte:window bind:innerWidth={screenWidth} />

{#each list as tube}
    <Tube offset={(screenWidth / list.length) * tube} />
{/each}