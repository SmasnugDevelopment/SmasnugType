<script lang="ts">
	let inputText = $state('');
	let display = $state('type');
	let startTime = $state(0);
	let time = $state(0);

	function startTimer() {
		startTime = Date.now();
		console.log('start');
	}

	function endTimer() {
		const endTime = Date.now();
		const timeDiff = endTime - startTime;
		return timeDiff;
	}

	function keyDown(e: KeyboardEvent) {
		if (display == 'type') {
			if (e.key === 'Backspace') {
				inputText = inputText.slice(0, -1);
			}
			if (e.key.length === 1) {
				if (inputText === '') {
					startTimer();
				}

				inputText += e.key;
			}

			if (inputText === 'smasnug') {
				display = 'result';
				inputText = '';
			}
		} else if (display == 'result') {
			if (e.key.length === 1) {
				if (inputText === '') {
					startTimer();
				}

				display = 'type';
				inputText = e.key;
			}
		}
		if (e.key === 'Tab' || e.key === 'Escape') {
			inputText = '';
			display = 'type';
			e.preventDefault();
		}
	}
</script>

<svelte:head>
	<title>SmasnugType</title>
</svelte:head>

<svelte:document onkeydown={keyDown} />

{#if display === 'type'}
	<div class="text-4xl">
		<div class="absolute">{inputText}</div>
		<div class="text-gray-500">smasnug</div>
	</div>
{:else if display === 'result'}
	<div>🎉</div>
{:else}{/if}
