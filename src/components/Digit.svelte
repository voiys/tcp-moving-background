<script>
	import { Chance } from 'chance';
	export let digit;
	const c = new Chance();

	const animationName = c.bool() ? 'left' : 'right';

	const top = `${c.integer({
		min: 2,
		max: 97,
	})}%`;

	const isPhone = window.innerWidth < 768;

	const durations = isPhone ? [2, 2, 4, 4, 6, 8] : [8, 8, 8, 16, 16, 32];

	const duration = `${
		durations[
			c.integer({
				min: 0,
				max: durations.length - 1,
			})
		]
	}s`;

	const easing = 'linear';

	const offset = `${c.integer({
		min: -100,
		max: isPhone ? 200 : 400,
	})}px`;

	const opacity = `${c.integer({
		min: 0.5,
		max: 0.9,
	})}`;

	const fontSize = `${c.integer({
		min: 9,
		max: isPhone ? 16 : 20,
	})}px`;

	const delay = `${c.integer({
		min: 0.1,
		max: 1,
	})}s`;
</script>

<span
	class="digit {animationName}"
	style="--top: {top}; --duration: {duration}; --offset: {offset}; --opacity: {opacity}; --font-size: {fontSize}; --easing: {easing}; --delay: {delay}"
	>{digit}</span
>

<style>
	.digit {
		opacity: 0;
		font-weight: bold;
		font-size: var(--font-size);

		position: absolute;
		top: var(--top);

		will-change: left right;
	}

	.left {
		left: 0;
		animation: left-to-right var(--duration) var(--easing) infinite;
	}

	.right {
		right: 0;
		animation: right-to-left var(--duration) var(--easing) infinite;
	}

	@keyframes left-to-right {
		0% {
			left: var(--offset);
			opacity: 0;
		}

		5% {
			opacity: 0;
		}

		45% {
			opacity: var(--opacity);
		}

		100% {
			left: 100%;
		}
	}

	@keyframes right-to-left {
		0% {
			right: var(--offset);
			opacity: 0;
		}

		5% {
			opacity: 0;
		}

		45% {
			opacity: var(--opacity);
		}

		100% {
			right: 100%;
			opacity: 0;
		}
	}
</style>
