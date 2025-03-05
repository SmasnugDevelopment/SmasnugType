<script lang="ts">
	let inputText = $state('');
	let display = $state('type');

	function keyDown(e: KeyboardEvent) {
		if (e.key === 'Backspace') {
			inputText = inputText.slice(0, -1);
		} else if (e.key === 'Tab' || e.key === 'Escape') {
			inputText = '';
            display = 'type';
			e.preventDefault();
		} else if (e.key.length === 1) {
			inputText += e.key;
		}

		if (inputText === 'smasnug') {
			display = 'result';
			inputText = '';
		}
	}
</script>

<svelte:head>
	<title>SmasnugType</title>
</svelte:head>

<svelte:document onkeydown={keyDown} />

{#if display === 'type'}
	<div>{inputText}</div>
{:else if display === 'result'}
	<div>🎉</div>
{:else}{/if}
