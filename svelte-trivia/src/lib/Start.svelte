<script>
import selectedCategory from './Category.svelte'
import selectedDifficulty from './Difficulty.svelte'

let questions = [];
  async function startGame(){
      const response = await fetch(`https://opentdb.com/api.php?amount=10&?category=${selectedCategory}&?difficulty=${selectedDifficulty}&type=multiple`);
        const data = await response.json()
        questions = data.results
        console.log(questions[3])
  }
let correct = 0
let incorrect = 0

function selectedAnswer(){

}
  function submitAnswer(){
    if(selectedAnswer = question.correct_answer){
        correct++
    }else{
        incorrect++
    }
  }


</script>
<button class='start' on:click={startGame}>
  Start Game
</button>

<div>
{#each questions as question}
  <div>
    <h3>{question.question}</h3>
    <ul>
      {#each question.incorrect_answers as answer}
        <li><button on:click={selectedAnswer}>{answer}</button></li>
      {/each}
      <li><button on:click={selectedAnswer}>{question.correct_answer}</button></li>
    </ul>
  </div>
{/each}
<button on:click={submitAnswer}>Submit</button>
<div>
{correct}
{incorrect}
</div>
</div>



<style>
ul{
    list-style-type: none;
  }
  button.start{
    width: 100%;
    background-color: green;
    color: white;
    margin: 5rem 0;
  }
</style>