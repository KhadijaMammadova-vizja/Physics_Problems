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
