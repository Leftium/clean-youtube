<script>
	import { page } from '$app/state';
	import Youtube from '$lib/Youtube.svelte';

	let devInfo = $state({});
	let mediaAspectRatio = $state(16 / 9);
	let id = $state('dt-SqNL4z3w');

	if (page.url.searchParams.has('vertical')) {
		id = 'IF_7SLHdreQ';
		mediaAspectRatio = 1000 / 1778;
	}
</script>

<pre hidden>{JSON.stringify(devInfo, null, 4)}</pre>

<main>
	<div class="player">
		<Youtube bind:devInfo {id} {mediaAspectRatio} />
	</div>
</main>

<style lang="scss">
	:global(html),
	:global(body) {
		margin: 0;
		scrollbar-width: none;
	}

	main {
		display: flex;
		flex-direction: column;
		width: 100%;
		height: calc(100svh);

		margin: auto;
	}

	.player {
		display: flex;
		justify-content: space-evenly;

		height: 100%;

		//object-fit: contain;

		contain: size;
	}
</style>
