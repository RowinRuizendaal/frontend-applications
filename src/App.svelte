<script>
  import fetchData from './scripts/fetchData'
  import MakeMap from './components/make-map.svelte'

  const data = fetchData(
    'https://gist.githubusercontent.com/RowinRuizendaal/44405f1b3a4de6099b901ba474c380b4/raw/7fe71a6ab4ef3f9d04e197054a7777c877b6ae6a/betaalmethode.json'
  )
</script>

<main>
  {#await data}
    <p>Data is being fetched, please hold on...</p>
  {:then ParkData}
    <MakeMap />
  {/await}
</main>
