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
		<Youtube id="IF_7SLHdreQ" mediaAspectRatio={1000 / 1778} />
	</div>
</main>

<style lang="scss">
	:global(html),
	:global(body) {
		margin: 0;
	}

	main {
		display: flex;
		flex-direction: column;
		width: min(100vw, 400px);
		margin: auto;

		//border: 4px solid red;
	}

	.player-horizontal,
	.player-vertical {
		display: flex;
		justify-content: space-evenly;

		width: 100%;

		contain: size;

		margin-block: 200px;

		aspect-ratio: 16 / 9;
	}

	.player-vertical {
		aspect-ratio: 9 / 16;
	}
</style>
