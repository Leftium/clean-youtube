<script lang="ts">
	let {
		id: youtubeId = 'dt-SqNL4z3w',
		mediaAspectRatio = 16 / 9,
		devMode = false,
		devInfo = $bindable({})
	} = $props();

	const urlParams = new URLSearchParams({
		autoplay: '0',
		mute: '1',
		loop: '1',
		color: 'white',
		controls: '0',
		modestbranding: '1',
		playsinline: '1',
		rel: '0',
		enablejsapi: '1',
		playlist: youtubeId
	});
	const src = `https://www.youtube.com/embed/${youtubeId}?${urlParams}`;

	const allow = [
		'accelerometer',
		'autoplay',
		'clipboard-write',
		'encrypted-media',
		'gyroscope',
		'picture-in-picture'
	].join('; ');

	let w = $state(0);
	let h = $state(0);
	let playerAspectRatio = $state(0);

	$effect(() => {
		playerAspectRatio = (w ?? h) ? w / h : 16 / 9;

		devInfo = {
			w,
			h,
			mediaAspectRatio,
			playerAspectRatio
		};
	});
</script>

<youtube-player
	style:aspect-ratio={playerAspectRatio}
	style:height={playerAspectRatio > 1 ? '100%' : ''}
	class={{ devMode }}
	bind:clientWidth={w}
	bind:clientHeight={h}
>
	<youtube-content
		style:aspect-ratio={mediaAspectRatio}
		style:width={mediaAspectRatio > playerAspectRatio ? '100%' : ''}
	>
		<iframe {src} title="" frameborder="0" {allow} allowfullscreen></iframe>
	</youtube-content>
</youtube-player>

<style lang="scss">
	// The player will fill the parent element's dimensions.
	youtube-player {
		display: flex;
		justify-content: center;

		width: 100%;

		background-color: black;
	}

	// The content is cropped to the (vertical) aspect ratio as necessary.
	// The width is only expanded to 100% for horizontal content.
	// (See style: directives in HTML above.)
	youtube-content {
		display: flex;
		align-items: center;

		overflow: hidden;

		// No clicking/hover effects
		// pointer-events: none;

		iframe {
			width: 100%;
			flex-shrink: 0;
			height: calc(100% + 400px);
		}
	}

	youtube-player.devMode {
		border: 4px solid cyan;

		youtube-content {
			overflow: visible;

			iframe {
				opacity: 0.6;
			}
		}
	}
</style>
