
<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Hard from './lib/Hard.svelte'
  import Easy from './lib/Easy.svelte'
  import Category from './lib/Category.svelte'
  import Start from './lib/Start.svelte'
  import Difficulty from './lib/Difficulty.svelte'
</script>

<main>
  <div>
    <h1></h1>
  </div>
  <h1>Svelte Trivia</h1>

  <div class="card">
    <Difficulty />
  </div>
  <div>
  <Category />
  </div>

  <div>
  <Start />
  </div>

</main>


<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
  ul{
    list-style-type: none;
  }
</style>
