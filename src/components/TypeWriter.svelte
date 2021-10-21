<script lang="ts">
	import Typewriter from 'typewriter-effect/dist/core';
	import { onMount } from 'svelte';

	export let delay = 'noraml';
	let from;
	let content;

	onMount(() => {
		let typewriter = new Typewriter(content, { cursor: '▌', delay });
		typewriter.typeString(from.innerHTML).start();
	});
</script>

<main>
	<div bind:this={from} class="buffer"><slot /></div>
	<div bind:this={content} class="content" />
</main>

<style>
	.buffer {
		display: none;
		top: 0;
	}

	@keyframes cursorFade {
		0%,
		100% {
			opacity: 1;
		}
		80% {
			opacity: 0;
		}
	}
</style>
