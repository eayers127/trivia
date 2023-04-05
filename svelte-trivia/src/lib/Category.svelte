<script>
 let categories = [
  {id: 21, name: 'Sports'}, 
  {id: 11, name:'Movies'}, 
  {id: 17, name: 'Science'}
  ];

 export let selectedCategory= undefined;

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
</style>