<script>
  const options = ["rock", "paper", "scissors"];
  let playerChoice = "empty";
  let results = " ";
  let computerScore = 0;
  let playerScore = 1;

  const play = (player) => {
    const choiceNumber = Math.floor(Math.random() * 3);
    let computer = options[choiceNumber];
    let computerMessage = `Computer Chose: ${computer}. `;

    if (player == computer) {
      results = `${computerMessage}It's a tie.`;
    } else if (player == "rock") {
      if (computer == "paper") {
        results = `${computerMessage}You lose...`;
        computerScore++;
      } else {
        results = `${computerMessage}You win!`;
        playerScore++;
      }
    } else if (player == "paper") {
      if (computer == "scissors") {
        results = `${computerMessage}You lose...`;
        computerScore++;
      } else {
        results = `${computerMessage}You win!`;
        playerScore++;
      }
    } else {
      if (computer == "rock") {
        results = `${computerMessage}You lose...`;
        computerScore++;
      } else {
        results = `${computerMessage}You win!`;
        playerScore++;
      }
    }
    playerChoice = "empty";
  };

  const clearScore = () => {
    playerScore = 0;
    computerScore = 0;
    results = "";
  };
</script>

<main>
  <h1>Rock Paper Scissors</h1>
  <p>Player Choice: {playerChoice}</p>
  <div>
    <p>player: {playerScore}</p>
    <p>computer: {computerScore}</p>
  </div>
  <p>Choose rock, paper, scissors</p>
  <p>{results}</p>
  {#each options as option}
    <button on:click={() => (playerChoice = option)}>{option}</button>
  {/each}
  <button disabled={playerChoice == "empty"} on:click={() => play(playerChoice)}
    >Play Round</button
  >
  <button on:click={clearScore}>Clear</button>
  <p>For shits and giggles</p>
</main>

<style>
  div {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
  }
</style>
