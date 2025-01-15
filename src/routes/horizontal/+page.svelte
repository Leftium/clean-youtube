<script>
	import Youtube from '$lib/Youtube.svelte';
</script>

<main>
	<div class="player-horizontal">
		<Youtube mediaAspectRatio={1000 / 563} />
	</div>

	<div class="player-vertical">
		<Youtube mediaAspectRatio={1000 / 563} />
	</div>

	<div class="player-horizontal">
		<Youtube id="IF_7SLHdreQ" mediaAspectRatio={1000 / 1778} />
	</div>

	<div class="player-vertical">
		<Youtube id="IF_7SLHdreQ" mediaAspectRatio={1000 / 1778} />
	</div>
</main>

<style lang="scss">
	main {
		display: flex;

		justify-content: space-evenly;

		height: 19vw;
	}

	.player-horizontal,
	.player-vertical {
		display: flex;
		justify-content: space-evenly;
		margin-block: 200px;

		height: 100%;

		contain: size;

		aspect-ratio: 16 / 9;
	}

	.player-vertical {
		aspect-ratio: 9 / 16;
	}
</style>
