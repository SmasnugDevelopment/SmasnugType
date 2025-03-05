<script lang="ts">
	let inputText = $state('');

	function keyDown(e: KeyboardEvent) {
		inputText += e.key;
		console.log(inputText);
	}
</script>

<svelte:head>
	<title>SmasnugType</title>
</svelte:head>

<svelte:document onkeypress={keyDown} />
