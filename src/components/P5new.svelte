<script>
	import { onMount, onDestroy } from 'svelte'

	let sketch

	onMount(() => {
		import('p5')
			.then((module) => {
				const p5 = module.default

				var emojis = ['😀', '😃', '😄', '😁', '😆'] // Add more emojis as you need

				const sketchFunction = (p) => {
					p.setup = () => {
						p.createCanvas(p.windowWidth, p.windowHeight)
						p.angleMode(p.DEGREES)
						p.textAlign(p.CENTER, p.CENTER)
						p.textSize(40)
					}

					p.draw = () => {
						p.background(51)
						p.translate(p.width / 2, p.height / 2)

						// Calculate animation properties
						var rotation = p.frameCount * 2
						var distance = p.sin(p.frameCount * 0.05) * 100

						// Calculate position
						var x = p.cos(rotation) * distance
						var y = p.sin(rotation) * distance

						// Choose an emoji to draw
						var emoji = emojis[p.frameCount % emojis.length]

						// Draw the chosen emoji
						p.text(emoji, x, y)
					}

					p.windowResized = () => {
						p.resizeCanvas(p.windowWidth, p.windowHeight)
					}
				}

				sketch = new p5(sketchFunction, '#container')
			})
			.catch((err) => {
				console.error('Failed to load p5', err)
			})
	})

	onDestroy(() => {
		// Make sure to remove the canvas when the component is destroyed
		if (sketch) {
			sketch.remove()
		}
	})
</script>

<div id="container" />

<style>
	#container {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
		background-color: #f0f0f0;
	}
</style>
