## 11. Animation: Two-Slit Interference

This HTML program simulates Young’s double-slit experiment using two coherent wave sources.  
The total displacement is modeled by:

u(r,t) = A/|r-r₁| sin(k|r-r₁| - ωt) + A/|r-r₂| sin(k|r-r₂| - ωt)

where:
- `r₁` and `r₂` are the positions of the two slits,
- `d = |r₁ - r₂|` is the distance between the slits,
- `k = 2π/λ` is the wave number,
- `λ` is the wavelength,
- `ω` is the angular frequency.

### Features
- Real-time interference pattern
- Slider to change slit separation `d`
- Slider to change wavelength `λ`
- Slider to change angular frequency `ω`
- Visualization of the two slits and resulting wave superposition

The bright and dark regions in the animation represent constructive and destructive interference.

<!-- 11. Animation: Two-Slit Interference -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Two-Slit Interference</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #0b1020;
      color: white;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    h1 {
      margin: 16px 0 8px;
    }

    .controls {
      display: flex;
      gap: 20px;
      flex-wrap: wrap;
      justify-content: center;
      margin-bottom: 10px;
      padding: 10px;
    }

    label {
      display: flex;
      flex-direction: column;
      font-size: 14px;
      gap: 4px;
    }

    canvas {
      border: 1px solid #444;
      background: black;
    }

    .info {
      max-width: 950px;
      margin: 12px;
      line-height: 1.6;
      font-size: 15px;
    }

    code {
      color: #93c5fd;
    }
  </style>
</head>
<body>
  <h1>Two-Slit Interference Animation</h1>

  <div class="controls">
    <label>
      Slit separation d
      <input type="range" id="distance" min="20" max="200" step="1" value="80" />
      <span id="distanceValue">80</span>
    </label>

    <label>
      Wavelength λ
      <input type="range" id="lambda" min="20" max="120" step="1" value="50" />
      <span id="lambdaValue">50</span>
    </label>

    <label>
      Angular frequency ω
      <input type="range" id="omega" min="0.02" max="0.30" step="0.01" value="0.12" />
      <span id="omegaValue">0.12</span>
    </label>
  </div>

  <canvas id="canvas" width="900" height="500"></canvas>

  <div class="info">
    This animation simulates Young's double-slit experiment using two coherent point sources.
    The total displacement is:
    <br><br>
    <code>
      u(r,t) = A/|r-r₁| sin(k|r-r₁| - ωt) + A/|r-r₂| sin(k|r-r₂| - ωt)
    </code>
    <br><br>
    where <code>r₁</code> and <code>r₂</code> are the positions of the two slits,
    <code>d = |r₁-r₂|</code> is the slit separation, and
    <code>k = 2π/λ</code>.
  </div>

  <script>
    const canvas = document.getElementById("canvas");
    const ctx = canvas.getContext("2d");

    const distanceSlider = document.getElementById("distance");
    const lambdaSlider = document.getElementById("lambda");
    const omegaSlider = document.getElementById("omega");

    const distanceValue = document.getElementById("distanceValue");
    const lambdaValue = document.getElementById("lambdaValue");
    const omegaValue = document.getElementById("omegaValue");

    const width = canvas.width;
    const height = canvas.height;

    const A = 1000;
    let time = 0;

    function updateLabels() {
      distanceValue.textContent = distanceSlider.value;
      lambdaValue.textContent = lambdaSlider.value;
      omegaValue.textContent = Number(omegaSlider.value).toFixed(2);
    }

    distanceSlider.addEventListener("input", updateLabels);
    lambdaSlider.addEventListener("input", updateLabels);
    omegaSlider.addEventListener("input", updateLabels);
    updateLabels();

    function draw() {
      const image = ctx.createImageData(width, height);
      const data = image.data;

      const d = parseFloat(distanceSlider.value);
      const lambda = parseFloat(lambdaSlider.value);
      const omega = parseFloat(omegaSlider.value);
      const k = 2 * Math.PI / lambda;

      const xSlit = 150;
      const yCenter = height / 2;

      const r1 = { x: xSlit, y: yCenter - d / 2 };
      const r2 = { x: xSlit, y: yCenter + d / 2 };

      for (let y = 0; y < height; y += 2) {
        for (let x = 0; x < width; x += 2) {
          let dx1 = x - r1.x;
          let dy1 = y - r1.y;
          let dist1 = Math.sqrt(dx1 * dx1 + dy1 * dy1);
          if (dist1 < 1) dist1 = 1;

          let dx2 = x - r2.x;
          let dy2 = y - r2.y;
          let dist2 = Math.sqrt(dx2 * dx2 + dy2 * dy2);
          if (dist2 < 1) dist2 = 1;

          const u1 = (A / dist1) * Math.sin(k * dist1 - omega * time);
          const u2 = (A / dist2) * Math.sin(k * dist2 - omega * time);
          const u = u1 + u2;

          const intensity = Math.max(0, Math.min(255, 128 + u));
          
          for (let oy = 0; oy < 2; oy++) {
            for (let ox = 0; ox < 2; ox++) {
              const px = x + ox;
              const py = y + oy;
              if (px < width && py < height) {
                const i = (py * width + px) * 4;
                data[i] = intensity;
                data[i + 1] = intensity;
                data[i + 2] = 255 - intensity;
                data[i + 3] = 255;
              }
            }
          }
        }
      }

      ctx.putImageData(image, 0, 0);

      ctx.fillStyle = "white";
      ctx.fillRect(xSlit - 8, 0, 16, height);

      ctx.fillStyle = "black";
      ctx.fillRect(xSlit - 8, r1.y - 12, 16, 24);
      ctx.fillRect(xSlit - 8, r2.y - 12, 16, 24);

      ctx.fillStyle = "red";
      ctx.beginPath();
      ctx.arc(r1.x, r1.y, 5, 0, 2 * Math.PI);
      ctx.fill();

      ctx.beginPath();
      ctx.arc(r2.x, r2.y, 5, 0, 2 * Math.PI);
      ctx.fill();

      time += 1;
      requestAnimationFrame(draw);
    }

    draw();
  </script>
</body>
</html>
