<script>
  import Header from './components/header/header.svelte'
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

  a {
    text-decoration: none;
    color: var(--roze);
  }
</style>

<body>
  <Header />
  <main>
    <div class="header">
      <h1>Waar kunnen de ouderen vandaag de dag nog in een parkeergarage met contant geld betalen?</h1>
    </div>
    <section class="waar-kun-je-hoe-betalen">
      <h2>Het probleem</h2>
      <p>
        Op 15 Decemeber 2019, maakte <a href="https://nl.wikipedia.org/wiki/Arjen_Lubach" target=_blank>Arjen Lubach</a> een <a href="https://www.youtube.com/watch?v=PuHnSuoooV4&t=272s&ab_channel=vprozondagmetlubach" target=_blank>aflevering</a> genaamd: ouderen & geld.
        Hierin wordt beweerd dat veel ouderen het liefst betalen met contant geld, verder beweerde Arjan Lubach dat slecht 10% van de ouderen niet kan internetbankieren. Terwijl dat er steeds meer pinautomaten verdwijnen in een rap tempo.  
      </p>
      <p>
        Ook word er in de aflevering vermeld dat veel mensen nog steeds met contant geld willen betalen terwijl de techniek er zo op vooruit gaat dat het contant geld in een later stadium zou verdwijnen, en dat ouderen moeite hebben om mee te gaan met de voortangen
        van de technologie.
      </p>
      <h2>Gedachtegang achter de visualisatie</h2>
      <p>
        Met deze visualisatie wil ik erachter komen of ik kan ondervinden of er meer of minder parkeergarages zijn waar je nog contant kan betalen. 
      </p>
      <Info message={'Onderstaand ziet u de kaart van Nederland, u kunt op de filter opties drukken om te kijken waar je met verschillende betaalmiddelen waar kan betalen'} />
      <Map />
    </section>
    <section class="vergelijk-prijzen">
      <p></p>
    </section>
  </main>
  <Footer />
</body>
