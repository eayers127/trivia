<script>
 let categories = [
  {id: 21, name: 'Sports'}, 
  {id: 11, name:'Movies'}, 
  {id: 17, name: 'Science'}
  ];

 export let category= '';

  function selectCategory(category) {
    category = category.name;
    console.log(category)
  }


</script>


<div>
 <h2>Choose a Category:</h2>

        <ul>
    {#each categories as category}
      <li>
        <button on:click={() => selectCategory(category)}>{category.name}</button>
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