  <body>
    <main>
    </main>
    <script src="sketch.js"></script>
  </body>

# page

```js
let x, y;
let sliderX, sliderY;
let gridSize = 20; // Tamaño de la cuadrícula
let canvasSize = 600; // Tamaño del canvas

function setup() {
  createCanvas(canvasSize, canvasSize + 50); // Añadir 50 píxeles de alto para los sliders
  
  // Crear sliders fuera de la cuadrícula
  sliderX = createSlider(0, width, width / 2);
  sliderX.position(50, height - 40); // Posicionar sliderX fuera de la cuadrícula
  sliderX.style('width', '200px');
  
  sliderY = createSlider(0, height - 50, (height - 50) / 2); // Ajustar el rango de sliderY
  sliderY.position(300, height - 40); // Posicionar sliderY fuera de la cuadrícula
  sliderY.style('width', '200px');
  
  // Inicializar valores
  x = width / 2;
  y = (height - 50) / 2;
}

function draw() {
  background(255);
  
  // Dibujar la cuadrícula
  stroke(200);
  for (let i = 0; i <= width; i += gridSize) {
    line(i, 0, i, height - 50);  // Líneas verticales, ajustadas para que no ocupen el área de los sliders
  }
  for (let j = 0; j <= height - 50; j += gridSize) {
    line(0, j, width, j);   // Líneas horizontales
  }
  
  // Actualizar coordenadas del punto
  x = sliderX.value();
  y = sliderY.value();
  
  // Dibujar el plano cartesiano
  stroke(0);
  line(0, (height - 50) / 2, width, (height - 50) / 2); // Línea horizontal
  line(width / 2, 0, width / 2, height - 50); // Línea vertical
  
  // Dibujar el punto
  fill(255, 0, 0);
  noStroke();
  ellipse(x, y, 10, 10);
  
  // Mostrar coordenadas
  fill(0);
  text("X: " + x + ", Y: " + y, 50, 30);
}

function mousePressed() {
  // Verificar si se hace clic en el área del plano cartesiano
  if (mouseX >= 0 && mouseX <= width && mouseY >= 0 && mouseY <= height - 50) {
    sliderX.value(mouseX);
    sliderY.value(mouseY);
  }
}
```

