<script>
 let difficulties = ['easy', 'medium', 'hard'];

 export let selectedDifficulty = '';

  function selectDifficulty(difficulty) {
    selectedDifficulty = difficulty;
    console.log(selectedDifficulty)
  }


</script>

<div>
 <h2>Select a Difficulty:</h2>

<ul>
    {#each difficulties as difficulty}
      <li>
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
</style>