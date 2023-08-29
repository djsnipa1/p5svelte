<script>
	import { onMount, onDestroy } from 'svelte'
	let sketch
	let chad = 0

	onMount(() => {
		import('p5')
			.then((module) => {
				const p5 = module.default

				sketch = new p5((p) => {
					let fontRegular, fontTwo

					// function p.preload() {
					p.preload = () => {
						fontRegular = p.loadFont('/fonts/super_donuts.ttf')
						console.log(`fontRegular = ${fontRegular}`)
					}
					p.setup = () => {
						const size = p.min(p.windowWidth, p.windowHeight)
						p.createCanvas(size, size)
						// p.createCanvas(p.windowWidth, p.windowHeight);
						p.colorMode(p.HSL, 1)
						p.noStroke()
					}

					function cosn(v) {
						return p.cos(v * p.TWO_PI) * 0.5 + 0.5
					}

					function invCosn(v) {
						return 1 - cosn(v)
					}

					const dotSize = 0.1
					const radius = Math.sqrt(0.5) + dotSize
					const PHI = (1 + Math.sqrt(5)) / 2

					let t
					const frames = 1000

					p.draw = () => {
						t = p.fract(p.frameCount / frames)
						// t = p.mouseX / p.width;

						p.scale(p.width, p.height)
						p.background(0)
						p.fill(1)

						function textMessage() {
							// p.background(70);
							p.fill(255)
							p.strokeWeight(0)
							p.textSize(40)
							p.textFont(fontRegular)
							p.text('Font Style Normal', 10, 30)
							p.rect(20, 220, 150, 150)
						}

						const count = 2000 * invCosn(t)
						for (let i = 0; i < count; i++) {
							const f = i / count
							const a = i / PHI
							const dist = f * radius
							const x = 0.5 + p.cos(a * p.TWO_PI) * dist
							const y = 0.5 + p.sin(a * p.TWO_PI) * dist

							const sig = cosn(f - t * 6)
							const r = sig * f * dotSize

							const hue = p.fract(f * 0.5 + t)
							const sat = 1
							const light = 0.6 * sig + 0.25
							const clr = p.color(hue, sat, light)

							p.fill(clr)

							p.circle(x, y, r)
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
		width: '100%';
		height: '100%';
	}
</style>
