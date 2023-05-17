<script>
	import { onMount } from 'svelte';
	import Digit from './Digit.svelte';
	export let index;

	const isFirst = index === 0;

	let isShowing = isFirst;

	const isPhone = window.innerWidth < 768;

	onMount(() => {
		if (!isFirst) {
			setTimeout(() => {
				isShowing = true;
			}, index * 500);
		}
	});

	let digits = Array.from({ length: isPhone ? 25 : 40 })
		.map((_) => Math.random())
		.map((item) => (item > 0.5 ? '1' : '0'));
</script>

{#if isShowing}
	{#each digits as digit}
		<Digit {digit} />
	{/each}
{/if}
