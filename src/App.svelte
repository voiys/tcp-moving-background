<script>
	import { onMount } from 'svelte';
	import Digit from './components/Digit.svelte';
	import Digits from './components/Digits.svelte';

	const arr = Array.from({ length: 20 });
</script>

<div class="container">
	{#each arr as _item, index}
		<Digits {index} />
	{/each}
</div>

<style>
	.container {
		position: relative;
		width: 100vw;
		height: 100vh;
		display: flex;
		background: var(--black);
		color: var(--primary-color);
		overflow: hidden;
	}
</style>
