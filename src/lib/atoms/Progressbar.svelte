<script>
	let progressbar;
	let labelValue;

	import { onMount } from 'svelte';

	// runs after the component is first rendered to the DOM.
	onMount(() => {
		let random = Math.floor(Math.random() * 100);

		progressbar.value = random;
		labelValue.innerHTML = random + '%';
	});
</script>

<div class="progress-container">
	<progress id="progress-partner" max="100" value="0" bind:this={progressbar} />
	<label class="progress-percentage" for="progress-partner" bind:this={labelValue}>0%</label>
</div>

<style>
	/* progress bar */
	.progress-container {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: flex-end;
		gap: 1em;
		margin-top: 0.25em;
	}

	progress {
		width: 100%;
	}

	progress[value] {
		/* Reset the default appearance */
		-webkit-appearance: none;
		appearance: none;
		height: 60%;
	}

	/* chrome/safari */
	progress[value]::-webkit-progress-bar {
		background-color: var(--c-container-stroke);
		border-radius: 0.5em;
	}

	progress[value]::-webkit-progress-value {
		background-color: var(--c-pink);
		border-radius: 0.5em;
		transition: 1s ease-out;
	}

	.progress-percentage {
		height: 85%;
	}
</style>
