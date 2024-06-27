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

  function onPageChange(event, showPage) {
    showPage(Number(event.target.value))
  }

  const colors = $state([
    '#e5f9f0',
    '#ccf3e2',
    '#b2edd3',
    '#99e7c5',
    '#7fe1b7',
    '#66dba8',
    '#4cd59a',
    '#32cf8b',
    '#19c97d',
    '#00c36f'
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
    let:currentPageIndex
    let:pagesCount
    let:showPage
  >
    {#each colors as color (color)}
      <div
        class="color-container"
        style="background-color: {color};"
      >
        <p>{color}</p>
      </div>
    {/each}
    <div slot="dots">
      <div class="select-container">
        <select
          value={currentPageIndex}
          onchange="{(event) => onPageChange(event, showPage)}"
          onblur="{(event) => onPageChange(event, showPage)}"
        >
          {#each  Array(pagesCount) as _, pageIndex (pageIndex)}
            <option value={pageIndex} class:active={currentPageIndex === pageIndex}>
              {pageIndex}
            </option>
          {/each}
        </select>
      </div>
    </div>
  </Carousel>
</div>

<style>
  .main-container {
    display: flex;
    width: 100%;
  }
  .color-container {
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .color-container > p {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-style: italic;
    font-size: 18px;
  }
  .active {
    background-color: grey;
    color: white;
  }

  .select-container {
    padding: 5px 0;
  }
  .select-container > select {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-style: italic;
    height: 25px;
    width: 100px;
    border-radius: 5px;
  }
</style>
