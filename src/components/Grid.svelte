function setup() {
  createCanvas(400, 400);
  noLoop();
}

function draw() {
  background(220);
  let size = 40; // size of the shapes
  let offset = size / 2; // offset for the staggered rows

  for (let x = 0; x < width; x += size) {
    for (let y = 0; y < height; y += size) {
      // check if the current row is even or odd
      let evenRow = (y / size) % 2 === 0;
      if (evenRow) {
        // draw the shape at (x, y)
        rect(x, y, size, size);
      } else {
        // draw the shape at (x + offset, y)
        rect(x + offset, y, size, size);
      }
    }
  }
}
function setup() {
  createCanvas(400, 400);
  noLoop();
}

function draw() {
  background(220);
  let size = 40; // size of the shapes
  let offset = size / 2; // offset for the staggered rows

  for (let x = 0; x < width; x += size) {
    for (let y = 0; y < height; y += size) {
      // check if the current row is even or odd
      let evenRow = (y / size) % 2 === 0;
      if (evenRow) {
        // draw the shape at (x, y)
        rect(x, y, size, size);
      } else {
        // draw the shape at (x + offset, y)
        rect(x + offset, y, size, size);
      }
    }
  }
l