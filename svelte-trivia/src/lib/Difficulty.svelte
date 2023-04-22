<script>
 export let difficulties = ['easy', 'medium', 'hard'];

 export let difficulty = '';

  function selectDifficulty(difficulty) {
    difficulty = difficulty;
    console.log(difficulty)
  }


</script>

<div>
 <h2>Select a Difficulty:</h2>
        

        <ul>
    {#each difficulties as difficulty}
      <li class = "selectDifficulty ? 'selected' : ''">
        <button on:click={() => selectDifficulty(difficulty)}>{difficulty}</button>
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