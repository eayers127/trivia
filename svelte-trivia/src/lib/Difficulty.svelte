<script>
 let difficulties = ['easy', 'medium', 'hard'];

 export let selectedDifficulty = 'easy';

  function selectDifficulty(difficulty) {
    selectedDifficulty = difficulty;
    console.log(selectedDifficulty)
  }


</script>

<div>
 <h2>Select a Difficulty:</h2>
        <button class="{selectedDifficulty === 'easy' ? 'selected' : ''}" on:click={() => selectDifficulty(difficulty)}>easy</button>
        <button class="{selectedDifficulty === 'medium' ? 'selected' : ''}" on:click={() => selectedDifficulty = 'medium'}>medium</button>
        <button class="{selectedDifficulty === 'hard' ? 'selected' : ''}" on:click={() => selectedDifficulty = 'hard'}>hard</button>

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