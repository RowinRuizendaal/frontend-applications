<script>
  import { geoMercator } from 'd3'

  import {
    handleMouseOver,
    handleMouseOut,
    mouseMove,
  } from '../../scripts/mouse-actions'

  export let dots

  const projection = geoMercator().scale(6000).center([5.116667, 52.17])
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
