<script lang="ts">
	import Menu from './Menu.svelte';
	import GuessPage from './GuessPage.svelte';
	let inMenuPage: boolean = true;

	function setGuessPage() {
		inMenuPage = false;
	}

	function setMenuPage() {
		inMenuPage = true;
	}
</script>

{#if inMenuPage}
	<Menu {setGuessPage} />
{:else}
	<GuessPage {setMenuPage} />
{/if}
