<script>
import selectedCategory from './Category.svelte'

let questions = [];
  async function startGame(){
      const response = await fetch(`https://opentdb.com/api.php?amount=10&?category=${selectedCategory}`);
        const data = await response.json()
        questions = data.results
        console.log(questions[3])
  }

</script>
<button on:click={startGame}>
  Start Game
</button>

{#each questions as question}
  <div>
    <h3>{question.question}</h3>
    <ul>
      {#each question.incorrect_answers as answer}
        <li>{answer}</li>
      {/each}
      <li>{question.correct_answer}</li>
    </ul>
  </div>
{/each}
