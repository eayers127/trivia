<script>
 let categories = [
  {id: 21, name: 'Sports'}, 
  {id: 11, name:'Movies'}, 
  {id: 17, name: 'Science'}
  ];

 export let selectedCategory= 'Sports';

  function selectCategory(category) {
    selectedCategory = category.name;
    console.log(selectedCategory)
  }


</script>


<div>
 <h2>Choose a Category:</h2>
        <button class="{selectedCategory === 'Sports' ? 'selected' : ''}" on:click={() => selectedCategory = 'Sports'}>Sports</button>
        <button class="{selectedCategory === 'Movies' ? 'selected' : ''}" on:click={() => selectedCategory = 'Movies'}>Movies</button>
        <button class="{selectedCategory === 'Science' ? 'selected' : ''}" on:click={() => selectedCategory = 'Science'}>Science</button>

        <ul>
    {#each categories as category}
      <li>
        <button on:click={() => selectCategory(category.id)}>{category.name}</button>
      </li>
    {/each}
  </ul>
</div>



<style>
ul{
    list-style-type: none;
  }
  button{
    background-color: blue;
    color: white;
    margin: .5rem 0;
  }
  button.selected{
    background-color: white;
    color: blue;
    border: solid 2px blue;
  }


</style>