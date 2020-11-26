<script>
  import { createEventDispatcher } from 'svelte'
  import { ascending, selectAll } from 'd3'

  
  export let data
  const dispatch = createEventDispatcher()

  let orignalData = data
  let arraywithvalues = []
  let filterUnique = []
  

  data.forEach((el) => {
    arraywithvalues.push(el.paymentmethod)
  })

  const unique = (value, index, self) => {
    return self.indexOf(value) === index
  }

  filterUnique = arraywithvalues.filter(unique)
  filterUnique.sort(ascending) // built in with D3


  const updatemap = (method) => {
    const paymentmethods = data.filter((row) => row.paymentmethod == method)
    newMapData(paymentmethods)
  }
  const newMapData = (data)  =>{
    dispatch('updateMap', {
      array: data,
      length: data.length
    })
}
const resetRadioButtons = () => {
    const radioBtns = selectAll('input[type=radio]')
    radioBtns
      .property('checked', false)
  }
</script>

<style>
  input {
    display: none;
  }

  form {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    flex-direction: row;
}

.radioBtn {
  margin-top: 1.4rem;
  margin-right: 1.4rem;
  margin-bottom: 1.4rem;
  overflow: hidden;
  height: 5rem;
}

label {
  padding: 1.5rem;
  text-align: center;
  cursor: pointer;
  background: var(--blauw);
  border-radius: 5px;
  color: #fff;
  display: block;
  text-align: center;
}

label:hover {
  background: var(--roze);
}

input:checked+label {
    background: var(--roze);
    color: var(--wit);
}

.container {
  display: flex;
  justify-content: center;
  margin-top: 1.4rem;
}

.reset {
    background: var(--blauw);
    border: 3px solid var(--blauw);
    padding: .6rem 3rem;
    color: #fff;
    font-size: .9rem;
    cursor: pointer;
    transition: .2s;
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
  <div class="container">
  <button
  on:click={() => (newMapData(orignalData))}
  on:click={() => (resetRadioButtons())}  
  class="reset">Reset het filter</button>
</div>
</div>
