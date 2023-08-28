<script>
	import { onMount, onDestroy } from 'svelte'
	let sketch
	let chad = 0

	onMount(() => {
		import('p5')
			.then((module) => {
				const p5 = module.default

				sketch = new p5((p) => {
					p.setup = () => {
						const size = p.min(p.windowWidth, p.windowHeight)
						p.createCanvas(size, size)
						p.colorMode(p.RGB, 1)
						p.noLoop()
					}

					p.draw = () => {
						p.background(220)
						let size = 40 // size of the shapes
						let offset = size / 2 // offset for the staggered rows

						for (let x = 0; x < p.width; x += size) {
							for (let y = 0; y < p.height; y += size) {
								// check if the current row is even or odd
								let evenRow = (y / size) % 2 === 0
								if (evenRow) {
									// draw the shape at (x, y)
									p.rect(x, y, size, size)
								} else {
									// draw the shape at (x + offset, y)
									p.rect(x + offset, y, size, size)
								}
							}
						}
					}

					p.windowResized = () => {
						p.resizeCanvas(p.windowWidth, p.windowHeight)
					}
				}, '#container')
			})
			.catch((err) => {
				console.error('Failed to load p5', err)
			})
	})

	onDestroy(() => {
		// Make sure to remove the canvas when the component is
		if (sketch) {
			sketch.remove()
		}
	})
</script>

{@debug chad}
<div id="container" />

<style>
	#container {
		width: 100%;
		height: 100%;
	}
</style>
