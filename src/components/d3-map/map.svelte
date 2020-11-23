<script>
  import { geoMercator, geoPath } from 'd3'
  import { onMount } from 'svelte'
  import { feature } from 'topojson'
  import Dots from '../d3-map/dots/map-dots.svelte'

  let data = []
  const projection = geoMercator().scale(6000).center([5.116667, 52.17])

  let currentProj = projection
  let path = geoPath().projection(currentProj)

  onMount(async function () {
    const response = await fetch(
      'https://cartomap.github.io/nl/wgs84/gemeente_2020.topojson'
    )
    const json = await response.json()
    const topoData = feature(json, json.objects.gemeente_2020)
    const land = {
      ...topoData,
      features: topoData.features,
    }

    data = land.features
  })
</script>

<style>
  path {
    fill: var(--blauw);
    stroke: var(--roze);
    stroke-opacity: 0.2;
  }

  svg {
    margin-top: 5rem;
  }
</style>

<svg width="960" height="500">
  {#each data as feature}
    <path
      d={path(feature)}
      on:mouseover={() => console.log(feature.properties.statnaam)}
    />
  {/each}
  <Dots />
</svg>
