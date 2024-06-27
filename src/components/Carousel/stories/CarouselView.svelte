<script>
  import Carousel from '../Carousel.svelte'

  

  
  
  

  

  

  

  

  
  
  

  

  

  

  

  
  /** @type {{timingFunction?: string, arrows?: boolean, infinite?: boolean, initialPageIndex?: number, duration?: number, autoplay?: boolean, autoplayDuration?: number, autoplayDirection?: string, pauseOnFocus?: boolean, autoplayProgressVisible?: boolean, dots?: boolean, swiping?: boolean, particlesToShow?: number, particlesToScroll?: number}} */
  let {
    timingFunction = 'ease-in-out',
    arrows = true,
    infinite = true,
    initialPageIndex = 1,
    duration = 500,
    autoplay = false,
    autoplayDuration = 3000,
    autoplayDirection = 'next',
    pauseOnFocus = false,
    autoplayProgressVisible = false,
    dots = true,
    swiping = true,
    particlesToShow = 1,
    particlesToScroll = 1
  } = $props();

  const colors = $state([
    { color: '#e5f9f0', text: '0' },
    { color: '#ccf3e2', text: '1' },
    { color: '#b2edd3', text: '2' },
    { color: '#99e7c5', text: '3' },
    { color: '#7fe1b7', text: '4' },
    { color: '#66dba8', text: '5' },
    { color: '#4cd59a', text: '6' },
    { color: '#32cf8b', text: '7' },
    { color: '#19c97d', text: '8' },
    { color: '#00c36f', text: '9' }
  ])

  const colors2 = $state([
    { color: '#e5f9f0', text: '0' },
    { color: '#ccf3e2', text: '1' },
    { color: '#b2edd3', text: '2' }
  ])
</script>

<div class="main-container">
  <Carousel
    {timingFunction}
    {arrows}
    {infinite}
    {initialPageIndex}
    {duration}
    {autoplay}
    {autoplayDuration}
    {autoplayDirection}
    {pauseOnFocus}
    {autoplayProgressVisible}
    {dots}
    {swiping}
    {particlesToShow}
    {particlesToScroll}
    on:pageChange={
      event => console.log(`Current page index: ${event.detail}`)
    }
  >
    {#each colors as { color, text } (color)}
      <div
        class="color-container"
        style="background-color: {color};"
      >
        <p>{text}</p>
      </div>
    {/each}
  </Carousel>

  <Carousel
    {timingFunction}
    {arrows}
    {infinite}
    {initialPageIndex}
    {duration}
    {autoplay}
    {autoplayDuration}
    {autoplayDirection}
    {pauseOnFocus}
    {autoplayProgressVisible}
    {dots}
    {swiping}
    {particlesToShow}
    {particlesToScroll}
  >
    {#each colors2 as { color, text } (color)}
      <div
        class="color-container"
        style="background-color: {color};"
      >
        <p>{text}</p>
      </div>
    {/each}
  </Carousel>
</div>

<style>
  .main-container {
    display: flex;
    flex-direction: column;
    width: 100%;
  }
  .color-container {
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    user-select: none;
  }
  .color-container > p {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-style: italic;
    font-size: 18px;
  }
</style>
