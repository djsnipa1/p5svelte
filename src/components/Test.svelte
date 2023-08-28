<script lang="ts">
	import { onMount, onDestroy } from 'svelte'
	let sketch: object

	onMount(() => {
		import('p5')
			.then((module) => {
				const p5 = module.default

				sketch = new p5((p) => {
					let fontRegular: string

					// function p.preload() {
					p.preload = () => {
						fontRegular = p.loadFont('/fonts/super_donuts.ttf')
						console.log(`fontRegular = ${fontRegular}`)
					}
					p.setup = () => {
						const size = p.min(p.windowWidth, p.windowHeight)
						p.createCanvas(size, size)
						// p.background(0, 0, 0, 0)
						// p.createCanvas(500, 500);
						// p.createCanvas(p.windowWidth, p.windowHeight);
						// p.colorMode(p.RGB, 1);
						// p.noStroke();
					}

					p.draw = () => {
						// p.clear()
						// p.rectMode(p.CENTER);
						p.background(70, 100, 146)
						// p.noStroke()
						// p.stroke(51)
						p.fill(0)
						p.rect(20, 20, 60, 60)
						function textMessage() {
							// p.background('orange')
							p.fill(150)
							p.strokeWeight(3)
							p.stroke(255)
							p.textAlign(p.CENTER, p.CENTER)
							p.translate(p.width / 2, p.height / 2)
							// p.textSize(40)
							// p.text('one', 10, 30)
							// p.fill(255, 102, 153)
							// p.text('two', 10, 80)
							// p.fill(255, 102, 153)
							// p.text('three', 10, 130)

							p.textFont(fontRegular)
							p.rect(20, 220, 150, 150)

							let baseTextSize = 32 // Define a base text size
							let scaleFactor = 0.01 // Define a scaling factor

							// Set the text size depending on window width
							p.textSize(baseTextSize + p.windowWidth * scaleFactor)
							p.text('Happy Birthday', 0, -25)
							p.textSize(baseTextSize + p.windowWidth * (scaleFactor * 2))
							p.text('Maria!', 0, 25)

							// p.text('This text size changes with window width!', 50, 50)
						}

						textMessage()
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

<!-- {@debug sketch} -->
<div id="container" />

<style>
	#container {
		width: 100vw;
		height: 100%;
	}
</style>
