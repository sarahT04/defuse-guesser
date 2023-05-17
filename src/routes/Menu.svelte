<script lang="ts">
	export let setGuessPage: () => void;
</script>

<h1>
	Welcome to defuse guesser.
	<br />
	You have to guess between half defuse or full defuse.
</h1>
<h3>Are you ready?</h3>
<button class="button mt-2 bg-green-800" on:click={setGuessPage}>Ready!</button>
