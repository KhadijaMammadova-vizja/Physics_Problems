## 9. Damped Oscillator

Given the damped harmonic oscillator equation:

m d²x/dt² + b dx/dt + kx = 0

We first divide by `m`:

d²x/dt² + (b/m) dx/dt + (k/m)x = 0

Define:

- `γ = b/(2m)`
- `ω₀ = sqrt(k/m)`

Then the equation becomes:

d²x/dt² + 2γ dx/dt + ω₀² x = 0

---

### 1. General solution

Assume a solution of the form:

x(t) = e^(rt)

Substituting into the differential equation gives the characteristic equation:

r² + 2γr + ω₀² = 0

So,

r = -γ ± sqrt(γ² - ω₀²)

The nature of the motion depends on the discriminant:

#### (a) Underdamped case: `γ < ω₀`
Roots are complex:

r = -γ ± iω_d

where

ω_d = sqrt(ω₀² - γ²)

So the solution is:

x(t) = e^(-γt) [C₁ cos(ω_d t) + C₂ sin(ω_d t)]

This describes oscillation with exponentially decreasing amplitude.

#### (b) Critically damped case: `γ = ω₀`
There is one repeated root:

r = -γ

So the solution is:

x(t) = (C₁ + C₂ t)e^(-γt)

This is the boundary between oscillatory and non-oscillatory motion.

#### (c) Overdamped case: `γ > ω₀`
Roots are real and distinct:

r₁ = -γ + sqrt(γ² - ω₀²)
r₂ = -γ - sqrt(γ² - ω₀²)

So the solution is:

x(t) = C₁ e^(r₁ t) + C₂ e^(r₂ t)

This does not oscillate; it returns to equilibrium slowly.

---

### 2. Classification of cases

The classification depends on the value of the damping coefficient `b`.

Since

γ = b/(2m)

the critical value occurs when:

γ = ω₀

So,

b/(2m) = sqrt(k/m)

which gives the **critical damping coefficient**:

b_c = 2 sqrt(km)

Therefore:

- **Underdamped:** `b < 2sqrt(km)`
- **Critically damped:** `b = 2sqrt(km)`
- **Overdamped:** `b > 2sqrt(km)`

---

### 3. First-order system for numerical solution

To solve numerically using RK4, define:

- `x₁ = x`
- `x₂ = dx/dt`

Then:

dx₁/dt = x₂
dx₂/dt = -(b/m)x₂ - (k/m)x₁

So the system becomes:

x' = v
v' = -(b/m)v - (k/m)x

This is the system to integrate with the Runge–Kutta 4th-order method.

---

### 4. Effect of parameter `b`

The damping coefficient `b` controls how quickly the motion loses energy.

- For **small `b`**, the system oscillates for a long time before settling.
- At the **critical value** `b = 2sqrt(km)`, the system returns to equilibrium as fast as possible without oscillating.
- For **large `b`**, the system returns to equilibrium without oscillation, but more slowly than in the critical case.

So increasing `b`:
- reduces oscillations,
- increases energy loss,
- changes the motion from underdamped to critically damped to overdamped.

---

### 5. Graph of `x(t)`

- **Underdamped:** decaying oscillatory curve
- **Critically damped:** fastest non-oscillatory return to zero
- **Overdamped:** slow non-oscillatory return to zero

---

### 6. Phase portrait

The phase portrait is the plot of velocity `v` versus position `x`.

- **Underdamped:** spiral inward toward the origin
- **Critically damped:** curve approaches the origin without spiraling
- **Overdamped:** trajectories move directly toward the origin without oscillation

The origin `(x, v) = (0, 0)` is the stable equilibrium point.

---

### Final Answer

For the damped oscillator

m d²x/dt² + b dx/dt + kx = 0

the motion depends on the damping coefficient `b` relative to the critical value

b_c = 2sqrt(km)

- If `b < b_c`, the motion is **underdamped**:
  x(t) = e^(-γt) [C₁ cos(ω_d t) + C₂ sin(ω_d t)]

- If `b = b_c`, the motion is **critically damped**:
  x(t) = (C₁ + C₂ t)e^(-γt)

- If `b > b_c`, the motion is **overdamped**:
  x(t) = C₁ e^(r₁ t) + C₂ e^(r₂ t)

For numerical RK4 simulation, use the first-order system:

x' = v  
v' = -(b/m)v - (k/m)x

As `b` increases, the system changes from oscillatory motion to non-oscillatory motion, and the phase portrait changes from a spiral to a direct approach toward equilibrium.
