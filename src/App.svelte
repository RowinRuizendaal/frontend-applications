<script>
  import Info from './components/infobar/info.svelte'
  import Map from './components/d3-map/map.svelte'
  import Footer from './components/footer/footer.svelte'
</script>

<style>
  main {
    max-width: 60rem;
    margin: 0 auto;
    padding: 3rem 0.8rem;
  }
  .header {
    max-width: 60rem;
    margin: 0 auto;
    padding: 3rem 0.8rem;
    padding-bottom: 0;
  }

  h1 {
    font-size: calc(2rem + 1vmin);
    font-weight: 700;
    text-align: center;
    color: var(--blauw);
  }

  h2 {
    margin-top: 3em;
    text-align: center;
    font-size: 1.6rem;
    font-weight: 400;
    margin-bottom: 0.3em;
    margin-top: 2em;
    color: var(--blauw);
  }

  p {
    font-size: 1rem;
    margin-bottom: 1em;
    margin-top: 2em;
    font-weight: 300;
  }
</style>

<body>
  <main>
    <div class="header">
      <h1>Waar kan je nog vandaag de dag nog contant betalen?</h1>
    </div>
    <section class="waar-kun-je-hoe-betalen">
      <h2>Waar kun je hoe betalen?</h2>
      <p>
        Onderstaande Kaart laat zien waar je nog kan betalen met een specifieke
        betaalmethode, u kunt op de kaart inzoomen door hier op te klikken.
      </p>
      <Info message={'Dit is een bericht met props in Svelte #dummytekst'} />
      <Map />
    </section>
    <section class="vergelijk-prijzen">
      <p>
        Onderstaande Kaart laat zien waar je nog kan betalen met een specifieke
        betaalmethode, u kunt op de kaart inzoomen door hier op te klikken.
      </p>
      <Info message={'Dit is een nieuwe melding, TODO adding better text'} />
    </section>
  </main>
  <Footer />
</body>
