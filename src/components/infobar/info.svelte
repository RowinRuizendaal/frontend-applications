<script>
  export let message
</script>

<style>
  .info {
    margin-top: 2rem;
    background-color: var(--roze);
    padding: 0.8rem 1rem;
    border-radius: 0.5rem;
    color: white;
    opacity: 0.9;
  }

  .info::before {
    content: 'i';
    color: white;
    background-color: var(--roze);
    display: inline-block;
    text-align: center;
    width: 1.5rem;
    height: 1.5rem;
    border-radius: 1.5rem;
    margin-right: 0.5rem;
  }
</style>

<p class="info">{message}</p>
