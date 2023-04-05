<script>
 let difficulties = ['Easy', 'Medium', 'Hard'];

 export let selectedCategory = '';

  function selectCategory(category) {
    selectedCategory = category;
    console.log(selectedCategory)
  }


</script>

<div>
 <h2>Choose a Category:</h2>

<ul>
    {#each categories as category}
      <li>
        <button on:click={() => selectCategory(category)}>{category}</button>
      </li>
    {/each}
  </ul>
</div>