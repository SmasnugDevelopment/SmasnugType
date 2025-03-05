<script lang="ts">
	let inputText = $state('');

	function keyDown(e: KeyboardEvent) {
		if (e.key === 'Backspace') {
			inputText = inputText.slice(0, -1);
		} else if (e.key === 'Enter') {
		} else if (e.key === 'Tab' || e.key === 'Escape') {
			inputText = '';
			e.preventDefault();
		} else if (e.key.length === 1) {
			inputText += e.key;
		}
	}
</script>

<svelte:head>
	<title>SmasnugType</title>
</svelte:head>

<svelte:document onkeydown={keyDown} />

<div>{inputText}</div>
