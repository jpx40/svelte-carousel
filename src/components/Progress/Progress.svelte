<script>
  const MAX_PERCENT = 100;

  
  /** @type {{value?: number}} */
  let { value = 0 } = $props();

  let width = $derived(Math.min(Math.max(value * MAX_PERCENT, 0), MAX_PERCENT));
</script>

<div
  class="sc-carousel-progress__indicator"
  style="
    width: {width}%;
  "
></div>

<style>
  .sc-carousel-progress__indicator {
    height: 100%;
    background-color: var(--sc-color-hex-dark-50p);
  }
</style>
