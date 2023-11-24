<script lang="ts">
	import { onMount } from 'svelte';

	export let bg: string = '';
	let blurAmount = 0;
	let perspectiveAmount = 0;

	function toggleBlur() {
		blurAmount = blurAmount === 0 ? 10 : 0;
	}

	function togglePerspective() {
		perspectiveAmount = perspectiveAmount === 0 ? 50 : 0;
	}

	onMount(() => {
		// Code to run after the component is mounted
	});
</script>

<div
	style="background-image: url({bg}); filter: blur({blurAmount}px)"
	class="surface"
	on:click={toggleBlur}
	on:dblclick={togglePerspective}
>
	<slot />
</div>

<style>
	.surface {
		background-size: fit;
		background-repeat: no-repeat;
		background-position: center;
	}
</style>
