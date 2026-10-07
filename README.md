# Clean YouTube

Archived SvelteKit experiment for fitting and cropping YouTube embeds across landscape and portrait videos and containers.

The project explored a CSS-first approach without depending on the YouTube Player API. It includes test layouts for uniform-height, uniform-width, and fullscreen players.

## Findings

- Keep the player/container geometry separate from the video's aspect ratio. A stable outer box with the video fitted or cropped inside avoids layout shifts and resize feedback loops.
- The CSS-only approach needs the media aspect ratio up front. `Youtube.svelte` compares it with the rendered player aspect ratio to decide which dimension should fill the container.
- `contain: size` was useful for isolating experimental player geometry.
- The iframe is intentionally oversized with `height: calc(100% + 400px)` and clipped. This was a pragmatic experiment for cropping YouTube chrome/shading, not a general-purpose sizing constant.
- Resizing exposed a feedback problem where the player could continually grow instead of shrinking again. Later player work reinforced the safer pattern: keep the player box fixed and change how the media fits inside it rather than deriving container size from rendered media.
- Hiding/cropping the YouTube UI does not remove iframe behavior. YouTube's own overlays, controls, focus behavior, and browser-specific quirks can still affect the result.

Demo routes in the app:

- `/fullscreen`
- `/fullscreen?vertical`
- `/horizontal`
- `/vertical`

The useful geometry work has since moved into [YouLoop](https://github.com/Leftium/youloop) and [vee-next](https://github.com/Leftium/vee-next).

## References

- https://stackoverflow.com/q/79341243/117030
- https://github.com/vidstack/player/issues/1445
- https://github.com/vidstack/player/issues/1104#issuecomment-1908991856
