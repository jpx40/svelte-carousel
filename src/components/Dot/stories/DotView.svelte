<script>
  import Dot from '../Dot.svelte'

  
  /** @type {{active?: boolean}} */
  let { active = $bindable(false) } = $props();

  function handleDotClick() {
    active = !active
  }
</script>

<Dot
  {active}
  on:click={handleDotClick}
/>
