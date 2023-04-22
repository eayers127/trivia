<script>
import category from './Category.svelte'
import difficulty from './Difficulty.svelte'

let questions = [];
  async function startGame(){
        const response = await fetch(`https://opentdb.com/api.php?amount=10&category=${category}&difficulty=${difficulty}`);
        const data = await response.json()
        questions = [];

        for (let questionObject of data.results) {
          const questionText = questionObject.question;
          const questionType = questionObject.type;
          const questionCategory = questionObject.category;
          const answersArray = [questionObject.correct_answer, ...questionObject.incorrect_answers];
          questions = [...questions,
          {
            text: questionText,
            type: questionType,
            category: questionCategory,
            answers: answersArray,
            correctAnswer: questionObject.correct_answer
          }]
        }
        console.log(questions[3])
  }
let correct = 0
let incorrect = 0


  function selectedAnswer(event) {
		const questionText = event.target.parentElement.parentElement.firstChild.textContent;
		const answerText = event.target.value;
		const questionObject = currentQuestions.find(question => question.text === questionText);
		if(answerText === questionObject.correctAnswer) {
			correctCount++;
		}
		else {
			incorrectCount++;
		}
	}


</script>
<button class='start' on:click={startGame}>
  Start Game
</button>


<div>
{#each questions as question}
  <div>
    <h3>{question.text}</h3>
    <ul>
      {#each question.answers as answer}
        <li><button on:click={selectedAnswer}>{answer}</button></li>
      {/each}
    </ul>
  </div>
{/each}
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
    background-color: green;
    color: white;
    margin: 5rem 0;
  }
</style>