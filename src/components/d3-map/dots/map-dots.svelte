<script>
  import { select, geoMercator, geoPath } from 'd3'
  import { onMount } from 'svelte'

  let dots = []

  const projection = geoMercator().scale(6000).center([5.116667, 52.17])
  onMount(async () => {
    const response = await fetch(
      'https://gist.githubusercontent.com/RowinRuizendaal/4db72bcb197b05ac444d281da70110ae/raw/dc3bce0996bc8f0ffb70d06999a8b0cfd1ea75a8/betaalmethode_new.json'
    )
    const json = await response.json()
    // const g = select('svg')
    // const projection = geoMercator().scale(6000).center([5.116667, 52.17])
    dots = json
    console.log(dots)

    // g.selectAll('circle')
    //   .data(json)
    //   .enter()
    //   .append('circle')
    //   .attr('class', 'circles')
    //   .attr('cx', function (d) {
    //     return projection([d.location.longitude, d.location.latitude])[0]
    //   })
    //   .attr('cy', function (d) {
    //     return projection([d.location.longitude, d.location.latitude])[1]
    //   })
    //   .attr('r', '4px')
    //   .attr('fill', '#e94560')
  })
</script>

<style>
  .circle {
    fill: var(--roze);
    border-radius: 4px;
  }
</style>

{#each dots as plot}
  <circle
    class="circle"
    cx={projection([plot.location.longitude, plot.location.latitude])[0]}
    cy={projection([plot.location.longitude, plot.location.latitude])[1]}
  />
{/each}
