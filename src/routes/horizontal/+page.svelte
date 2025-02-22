<script>
	import Youtube from '$lib/Youtube.svelte';
</script>

<main>
	<div class="player-horizontal">
		<Youtube mediaAspectRatio={1000 / 563} />
	</div>

	<div class="player-vertical">
		<Youtube id="IF_7SLHdreQ" mediaAspectRatio={1000 / 1778} />
	</div>

	<div class="player-vertical">
		<Youtube mediaAspectRatio={1000 / 563} />
	</div>

	<div class="player-horizontal">
		<Youtube id="IF_7SLHdreQ" mediaAspectRatio={1000 / 1778} devMode={false} />
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

		justify-content: space-evenly;

		height: 19vw;

		//border: 4px solid red;
	}

	.player-horizontal,
	.player-vertical {
		//box-sizing: border-box;

		display: flex;
		justify-content: space-evenly;
		margin-block: 150px;

		height: 100%;

		contain: size;

		aspect-ratio: 16 / 9;

		//border: 4px solid purple;
	}

	.player-vertical {
		aspect-ratio: 9 / 16;
	}
</style>
