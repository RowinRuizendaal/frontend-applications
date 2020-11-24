<script>
  import { onMount, createEventDispatcher } from 'svelte'
  import { ascending } from 'd3'

  const dispatch = createEventDispatcher()

  let dots = []
  let arraywithvalues = []
  let filterUnique = []

  onMount(async () => {
    const response = await fetch(
      'https://gist.githubusercontent.com/RowinRuizendaal/4db72bcb197b05ac444d281da70110ae/raw/ccf99e232fcfe63fc2f2953459744b7dce608589/betaalmethode_new.json'
    )
    const json = await response.json()
    dots = json

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
    sayHello(paymentmethods)
  }

  function sayHello(data) {
    dispatch('updateMap', {
      text: data,
    })
  }
</script>

<div class="filter">
  <form>
    {#each filterUnique as payment}
      <div class="radioBtn">
        <input
          type="radio"
          name="radio"
          id={payment}
          on:change={() => updatemap(payment)}
        />
        <!-- svelte-ignore a11y-label-has-associated-control -->
        <label> {payment} </label>
      </div>
    {/each}
  </form>
</div>
