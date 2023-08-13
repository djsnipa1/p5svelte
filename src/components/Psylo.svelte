<script>
  import { onMount, onDestroy } from 'svelte';
  let sketch;
  let chad = 0

  onMount(() => {
    import('p5').then(module => {
      const p5 = module.default;
  
      sketch = new p5(p => {
  
        p.setup = () => {
  const size = p.min(p.windowWidth, p.windowHeight);
          p.createCanvas(size, size);
          p.colorMode(p.RGB, 1);
          p.noStroke();
        };

const radius = Math.sqrt(0.5);
const PHI = (1 + Math.sqrt(5)) / 2;

        p.draw = () => {
          p.scale(p.width, p.height);
          p.background(0);
          p.fill(1);
          
          const count = 200;
          for (let i = 0; i < count; i++) {
            const f = i / count;
          const a = i / PHI;
          const dist = f * radius;
          const x = 0.5 + p.cos(a * p.TWO_PI) * dist;
          const y = 0.5 + p.sin(a * p.TWO_PI) * dist;
          const r = 0.01;
          p.circle(x, y, r);
          }
        };

        p.windowResized = () => {
          p.resizeCanvas(p.windowWidth, p.windowHeight);
        };
      }, '#container');
    }).catch(err => {
      console.error('Failed to load p5', err);
    });
  });



  

  


  onDestroy(() => {
    // Make sure to remove the canvas when the component is
    if (sketch) {
      sketch.remove();
    }
  });
    </script>
    

    {@debug chad}
    <div id="container"></div>

    
<style>
#container {
  width: "100%";
  height: "100%";
}


</style>

