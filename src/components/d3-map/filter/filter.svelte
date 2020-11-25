<script>
  import { onMount, createEventDispatcher } from 'svelte'
  import { ascending } from 'd3'

  
  const dispatch = createEventDispatcher()

  let dots = []
  let orignalData = []
  let arraywithvalues = []
  let filterUnique = []
 

  onMount(async () => {
    const response = await fetch(
      'https://gist.githubusercontent.com/RowinRuizendaal/4db72bcb197b05ac444d281da70110ae/raw/ccf99e232fcfe63fc2f2953459744b7dce608589/betaalmethode_new.json'
    )
    const json = await response.json()
    dots = json
    orignalData = json
    dots.forEach((el) => {
      arraywithvalues.push(el.paymentmethod)
    })
    const unique = (value, index, self) => {
      return self.indexOf(value) === index
    }
    filterUnique = arraywithvalues.filter(unique)
    filterUnique.sort(ascending) // built in with D3
  })
  function updatemap(method) {
    const paymentmethods = dots.filter((row) => row.paymentmethod == method)
    newMapData(paymentmethods)
  }
  function newMapData(data) {
    dispatch('updateMap', {
      array: data,
    })
  }
</script>

<style>
  input {
    display: none;
    position: absolute;
    width: 100%;
  }

  form {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
    justify-items: center;
    padding: 20px;
}

.radioBtn {
  margin-bottom: 1.4rem;
  overflow: hidden;
}

label {
  position: relative;
  width: 6rem;
  padding: .5rem 1.9rem;
  text-align: center;
  cursor: pointer;
  background: var(--blauw);
  border-radius: 10px;
  color: #fff;
  font-family: 'Roboto', sans-serif;
}

label:hover {
  background: var(--roze);
}
</style>


<div class="filter">
  <form>
    {#each filterUnique as payment}
      <div class="radioBtn">
        <input
          id={payment}
          type="radio"
          name="radio"
          on:change={() => updatemap(payment)}
        />
        <label for={payment}> {payment} </label>
      </div>
    {/each}
  </form>
  <button
  on:click={() => (newMapData(orignalData))} 
  class="reset">Reset het filter</button>
</div>
