<script>
  import { position } from "../../model";
  export let offset;

  let screenWidth = 0;
  let screenHight = 0;
  $: Xstart = offset;
  $: Xend = Xstart + 80;
  $: Ystart = getRandomInt(screenHight);
  $: Yend = Ystart + 160


  $: if (($position.x > Xstart && $position.x < Xend)) {
    if(($position.y < Ystart) || ($position.y > Yend))
      console.log('YOURE DEAD')
  }

  function getRandomInt(max) {
    let numb = Math.floor(Math.random() * (max - 160))
    if (numb < 160) {
      numb = 160;
    } return numb; 
  }

  setInterval(() => {
    Xstart++;
  }, 10);

  $: {
    if (Xstart === screenWidth) {
      Xstart = 0;
    }
  }
</script>

<svelte:window bind:innerWidth={screenWidth} bind:innerHeight={screenHight}/>

<div
  class="absolute left-0 bg-green h-screen w-20"
  style="transform: translateX({Xstart}px);"
>
  <div class="absolute bg-blue w-full h-40 left-0 top-1/2" style:top="{Ystart}px" />
</div>
