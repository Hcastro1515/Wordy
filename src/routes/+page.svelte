<script lang="ts">
	$: letters = ['-', '-', '-', '-'];
	$: combinedLetters = letters.join('');
	let visible = false;

	function addLetter(index: number) {
		letters = [
			...letters.slice(0, index + 1), 
			"_",
			...letters.slice(index + 1)
		]
	}
	
</script>

<main class="text-white flex flex-col justify-center items-center h-screen w-screen space-y-10">
	<h1 class="text-3xl font-extrabold uppercase">Words Game</h1>

	<div class="flex space-x-2 items-center">
		{#each letters as letter, idx}
			<div class="w-14 h-14 border border-dashed p-3 grid place-items-center rounded-lg">
				<input bind:value={letter} type="text" class="w-4 bg-transparent text-center border-none" />
			</div>

			{#if idx < letters.length - 1}
				<button on:click={() => addLetter(idx)}>+</button>
			{/if}
		{/each}
	</div>

	<span>{combinedLetters}</span>
</main>
