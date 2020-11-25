<script>
  import { geoMercator, geoPath } from 'd3'
  import { onMount } from 'svelte'
  import { feature } from 'topojson'
  import Dots from '../d3-map/dots/map-dots.svelte'
  import Filter from '../d3-map/filter/filter.svelte'

  import {
    handleMouseOver,
    handleMouseOut,
    mouseMove,
  } from '../scripts/mouse-actions'

  let plotData = []
  let mapData = []

  const width = 960
  const height = 500
  
  const projection = geoMercator().scale(6000).center([5.116667, 52.17])
  const path = geoPath().projection(projection)

  onMount(async function () {
    const map = await fetch('https://cartomap.github.io/nl/wgs84/gemeente_2020.topojson')
    
    const json = await map.json()
    const topoData = feature(json, json.objects.gemeente_2020)
    const land = {
      ...topoData,
      features: topoData.features,
    }
    mapData = land.features
  })

  const fetchData = async () => {
    if (localStorage.getItem('plotData')) {
      plotData = JSON.parse(localStorage.getItem('plotData'))
      return plotData
    } else {
      const dataset = await fetch('https://gist.githubusercontent.com/RowinRuizendaal/4db72bcb197b05ac444d281da70110ae/raw/ccf99e232fcfe63fc2f2953459744b7dce608589/betaalmethode_new.json')
      const json = await dataset.json()
      plotData = json
      localStorage.setItem('plotData', JSON.stringify(plotData))
      return plotData
    }
  }


  
  const updateMap = (event)  =>{
    plotData = event.detail.array
  }

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

<svg width={width} height={height}>
  {#each mapData as feature}
    <path
      d={path(feature)}
      on:mouseover={handleMouseOver(feature.properties.statnaam)}
      on:mouseout={handleMouseOut}
      on:mousemove={mouseMove}
    />
  {/each}
  <Dots dots={plotData} />
</svg>


{#await fetchData()}
<p>Loading... filter data</p>
{:then data}
<Filter data={data} on:updateMap={updateMap} />
{/await}