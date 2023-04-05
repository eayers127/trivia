<script>
 export let categories = ['Sports', 'Geography', 'History'];

 export let selectedCategory = '';

  function selectCategory(category) {
    selectedCategory = category;
  }

</script>

<div>
<h2>Choose a category</h2>
<ul>
{#each categories as category}
      <li on:click={() => selectCategory(category)}>
        {category}
      </li>
      {/each}
</ul>
</div>
