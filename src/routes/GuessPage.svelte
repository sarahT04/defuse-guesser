<script lang="ts">
	import { onMount } from 'svelte';
	export let setMenuPage: () => void;
	let audio: HTMLAudioElement;
	let guesses = { correct: 0, done: 0 };

	const full = 'full';
	const half = 'half';
	let answer = full;

	function randomizeSound() {
		if (randInt()) {
			answer = full;
			return;
		}
		answer = half;
		return;
	}

	onMount(() => randomizeSound);

	const playSound = () => audio.play();
	const randInt = () => Math.round(Math.random());
	const pickGuess = (guess: string) => {
		if (guess === answer) {
			guesses = { done: guesses.done + 1, correct: guesses.correct + 1 };
		} else {
			guesses = { ...guesses, done: guesses.done + 1 };
		}
		randomizeSound();
	};
</script>

<audio src={`/sounds/${answer}.mp3`} id="audio" bind:this={audio} />
<button class="mb-8 button block mx-auto bg-green-800" on:click={playSound}>Play the sound</button>
<h1>Score</h1>
<p class="mt-2">{guesses.correct} / {guesses.done}</p>
<div class="w-56 flex justify-around mt-4">
	<button class="button" on:click={() => pickGuess(half)}>Half</button>
	<button class="button" on:click={() => pickGuess(full)}>Full</button>
</div>
<button class="mt-8 button block mx-auto bg-red-800" on:click={setMenuPage}>Restart</button>
