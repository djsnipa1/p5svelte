<script>
  import { onMount, onDestroy } from 'svelte';
  let sketch;
  let chad = 0

  onMount(() => {
    import('p5').then(module => {
      const p5 = module.default;

      var emojis = ['🎮', '💗', '🦷', '🏓', '🧿']; // Add more emojis as you need
      var n = 0;
  
      sketch = new p5(p => {
  
        p.setup = () => {
          const size = min(p.widthWidth, p.windowHeight);
          p.createCanvas(size, size);
          p.colorMode(RGB, 1);
          p.noStroke;
        };

        p.draw = () => {
          p.scale(p.width, p.height);
          p.background(51);
          p.fill(1);
          
          const a= 0;
          const radius = 0.1;
          const x = cos(a * p.TWO_PI) * radius;
          const y = sin(a * p.TWO_PI) * radius;
          const r = 0.01;
          p.circle(x, y, z);
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
    
    <div id="suck"></div>
    
    
<style>
#container {
  background-color: "#999"
}

#suck {
  width: "200px";
  height: "200px";
  background-color: "red";
}
</style>
