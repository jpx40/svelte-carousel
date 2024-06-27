<script>
  import Dots from '../Dots.svelte'

  

  
  /** @type {{pagesCount?: number, currentPageIndex?: number}} */
  let { pagesCount = 5, currentPageIndex = $bindable(3) } = $props();

  function handlePageChange(event) {
    currentPageIndex = event.detail
  }
</script>

<Dots
  {pagesCount}
  {currentPageIndex}
  on:pageChange={handlePageChange}
>
</Dots>
