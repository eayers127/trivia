<script>
 let categories = [
  {id: 21, name: 'Sports'}, 
  {id: 11, name:'Movies'}, 
  {id: 17, name: 'Science'}
  ];

 let category = 21;

  function selectCategory(category) {
    category = category.id;
    console.log(category)
  }

let difficulties = ['easy', 'medium', 'hard'];

let difficulty = 'easy';

  function selectDifficulty(difficulty) {
    difficulty = difficulty;
    console.log(difficulty)
  }

let questions = [];
  async function startGame(){
        const response = await fetch(`https://opentdb.com/api.php?amount=10&category=${category}&difficulty=${difficulty}`);
        const data = await response.json()
        questions = [];

        for (let questionObject of data.results) {
          const questionText = questionObject.question;
          const questionType = questionObject.type;
          const questionCategory = questionObject.category;
          const correctAnswer = questionObject.correct_answer
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
		const questionObject = questions.find(question => question.text === questionText);
		if(questions.correctAnswer) {
			correct++;
		}
		else {
			incorrect++;
		}
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
<button class='start' on:click={startGame}>
  Start Game
</button>


<div>
{#each questions as question}
  <div>
    <h3>{question.text}</h3>
    <ul>
      {#each question.answers as answer}
        <li><button value={answer} on:click={selectedAnswer}>{answer}</button></li>
      {/each}
    </ul>
  </div>
{/each}
<div>
<h3>Correct Answers:</h3>
{correct}
<h3>Incorrect Answers:</h3>
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