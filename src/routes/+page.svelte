<script>
	import { onMount } from 'svelte';
	import styles from './page.module.css';
	let targetNumber;
	let guessNumber = '';
	let message = '';

	// function to generate a random number
	function generateTargetNumber() {
		targetNumber = Math.floor(Math.random() * 101);
		message = 'Guess a number between 0 to 100!';
	}

	// function to check
	function checkGuess() {
		if (parseInt(guessNumber) === targetNumber) {
			message = 'Congratualtions! you guessed it right!';
		} else if (parseInt(guessNumber) < targetNumber) {
			message = 'Too Low! Try again';
		} else {
			message = 'Too High! Try again';
		}
	}

	// Function to reset
	function resetGame() {
		generateTargetNumber();
		guessNumber = '';
		message = '';
	}

	// initialize the game
	onMount(() => {
		resetGame();
	});
</script>

<div class={styles.bigDiv}>
	<h1 class={styles.welcomeHeader}>Welcome to SvelteKit</h1>

	<div>
		<input type="number" bind:value={guessNumber} placeholder="Enter your guess" />
		<button on:click={checkGuess}>Check</button>
		<button on:click={resetGame}>Reset</button>
	</div>

	<p>{message}</p>
</div>
