<script>
  import { geoMercator } from 'd3'
  import { onMount } from 'svelte'

  import {
    handleMouseOver,
    handleMouseOut,
    mouseMove,
  } from '../../scripts/mouse-actions'

  let dots = []

  const projection = geoMercator().scale(6000).center([5.116667, 52.17])
  onMount(async () => {
    const response = await fetch(
      'https://gist.githubusercontent.com/RowinRuizendaal/4db72bcb197b05ac444d281da70110ae/raw/dc3bce0996bc8f0ffb70d06999a8b0cfd1ea75a8/betaalmethode_new.json'
    )
    const json = await response.json()
    dots = json
  })
</script>

<style>
  .circle {
    fill: var(--roze);
  }
</style>

{#each dots as plot}
  <circle
    class="circle"
    cx={projection([plot.location.longitude, plot.location.latitude])[0]}
    cy={projection([plot.location.longitude, plot.location.latitude])[1]}
    r="4px"
    on:mouseover={handleMouseOver(plot.areadesc)}
    on:mouseout={handleMouseOut}
    on:mousemove={mouseMove}
  />
{/each}
