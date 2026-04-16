## 10. Animation: Wave Sources

This HTML program simulates multiple point sources of waves.  
Each source is placed by clicking on the canvas. The displacement at any point is computed using the superposition principle:

u(r,t) = Σ [A / |r - r₀|^a] sin(k|r - r₀| - ωt)

where:
- r₀ is the position of a source,
- a is the decay exponent, adjustable in the range [0,2],
- k = 2π/λ is the wave number,
- ω is the angular frequency.

### Features
- Click to add wave sources
- Real-time visualization of interference
- Slider to control decay parameter a
- Slider to control wavelength λ
- Slider to control angular frequency ω
- Button to clear all sources

The animation shows the total displacement produced by the superposition of waves from all placed sources.

<!-- 10. Animation: Wave Sources -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Wave Sources Superposition</title>
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
      cursor: crosshair;
    }

    button {
      padding: 8px 14px;
      border: none;
      border-radius: 6px;
      background: #2563eb;
      color: white;
      cursor: pointer;
    }

    button:hover {
      background: #1d4ed8;
    }

    .info {
      max-width: 900px;
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
  <h1>Wave Sources Animation</h1>

  <div class="controls">
    <label>
      a (decay exponent)
      <input type="range" id="alpha" min="0" max="2" step="0.01" value="1" />
      <span id="alphaValue">1.00</span>
    </label>

    <label>
      Wavelength λ
      <input type="range" id="lambda" min="20" max="120" step="1" value="60" />
      <span id="lambdaValue">60</span>
    </label>

    <label>
      Angular frequency ω
      <input type="range" id="omega" min="0.02" max="0.30" step="0.01" value="0.12" />
      <span id="omegaValue">0.12</span>
    </label>

    <button id="clearBtn">Clear Sources</button>
  </div>

  <canvas id="canvas" width="900" height="500"></canvas>

  <div class="info">
    Click anywhere on the canvas to place wave sources.  
    The total displacement is the superposition of all sources:
    <br /><br />
    <code>
      u(r,t) = Σ [ A / |r - r₀|<sup>a</sup> ] sin(k|r - r₀| - ωt)
    </code>
    <br /><br />
    where <code>r₀</code> is the position of each source and
    <code>a ∈ [0,2]</code>.
  </div>

  <script>
    const canvas = document.getElementById("canvas");
    const ctx = canvas.getContext("2d");

    const alphaSlider = document.getElementById("alpha");
    const lambdaSlider = document.getElementById("lambda");
    const omegaSlider = document.getElementById("omega");

    const alphaValue = document.getElementById("alphaValue");
    const lambdaValue = document.getElementById("lambdaValue");
    const omegaValue = document.getElementById("omegaValue");

    const clearBtn = document.getElementById("clearBtn");

    const width = canvas.width;
    const height = canvas.height;

    const sources = [];
    const A = 1200;
    let time = 0;

    alphaSlider.addEventListener("input", () => {
      alphaValue.textContent = Number(alphaSlider.value).toFixed(2);
    });

    lambdaSlider.addEventListener("input", () => {
      lambdaValue.textContent = lambdaSlider.value;
    });

    omegaSlider.addEventListener("input", () => {
      omegaValue.textContent = Number(omegaSlider.value).toFixed(2);
    });

    canvas.addEventListener("click", (e) => {
      const rect = canvas.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      sources.push({ x, y });
    });

    clearBtn.addEventListener("click", () => {
      sources.length = 0;
    });

    function draw() {
      const image = ctx.createImageData(width, height);
      const data = image.data;

      const alpha = parseFloat(alphaSlider.value);
      const lambda = parseFloat(lambdaSlider.value);
      const omega = parseFloat(omegaSlider.value);
      const k = 2 * Math.PI / lambda;

      for (let y = 0; y < height; y += 2) {
        for (let x = 0; x < width; x += 2) {
          let u = 0;

          for (const s of sources) {
            const dx = x - s.x;
            const dy = y - s.y;
            let r = Math.sqrt(dx * dx + dy * dy);

            if (r < 1) r = 1;

            u += (A / Math.pow(r, alpha)) * Math.sin(k * r - omega * time);
          }

          const color = Math.max(0, Math.min(255, 128 + u));
          const index = (y * width + x) * 4;

          for (let dy = 0; dy < 2; dy++) {
            for (let dx = 0; dx < 2; dx++) {
              const px = x + dx;
              const py = y + dy;
              if (px < width && py < height) {
                const i = (py * width + px) * 4;
                data[i] = color;
                data[i + 1] = color;
                data[i + 2] = 255 - color;
                data[i + 3] = 255;
              }
            }
          }
        }
      }

      ctx.putImageData(image, 0, 0);

      for (const s of sources) {
        ctx.beginPath();
        ctx.arc(s.x, s.y, 5, 0, 2 * Math.PI);
        ctx.fillStyle = "red";
        ctx.fill();
      }

      time += 1;
      requestAnimationFrame(draw);
    }

    draw();
  </script>
</body>
</html>
