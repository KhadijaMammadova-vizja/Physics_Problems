## 6. Field at a Point from a System of Charges

Two point charges are given:

- $+q$ at point $(-a,0)$
- $+2q$ at point $(a,0)$

Determine:

1. $\vec{E}(0,y)$, $\vec{E}(x,0)$, and generally $\vec{E}(x,y)$
2. The condition for which $E_x = 0$, $E_y = 0$, and $\vec{E} = 0$
3. The field for: $a = 0.2\,\text{m}$, $y = 0.3\,\text{m}$, $q = 2\,\mu\text{C}$
4. The limit when $y \gg a$

---

### Step 1: Electric field formula for a point charge

For a point charge $Q$ located at $(x_0,y_0)$, the electric field at $(x,y)$ is

$$
\vec{E} = kQ \frac{(x-x_0)\hat{i} + (y-y_0)\hat{j}}{\left[(x-x_0)^2 + (y-y_0)^2\right]^{3/2}}
$$

where

$$
k = \frac{1}{4\pi\varepsilon_0}
$$

---

## 1. General field $\vec{E}(x,y)$

### Field due to charge $+q$ at $(-a,0)$

$$
\vec{E}_1 = kq \frac{(x+a)\hat{i} + y\hat{j}}{\left[(x+a)^2 + y^2\right]^{3/2}}
$$

### Field due to charge $+2q$ at $(a,0)$

$$
\vec{E}_2 = k(2q) \frac{(x-a)\hat{i} + y\hat{j}}{\left[(x-a)^2 + y^2\right]^{3/2}}
$$

### Total field

$$
\vec{E}(x,y) = \vec{E}_1 + \vec{E}_2
$$

So,

$$
\vec{E}(x,y) =
kq \frac{(x+a)\hat{i} + y\hat{j}}{\left[(x+a)^2 + y^2\right]^{3/2}}
+
2kq \frac{(x-a)\hat{i} + y\hat{j}}{\left[(x-a)^2 + y^2\right]^{3/2}}
$$

Hence the components are

$$
E_x =
kq\frac{x+a}{\left[(x+a)^2+y^2\right]^{3/2}}
+
2kq\frac{x-a}{\left[(x-a)^2+y^2\right]^{3/2}}
$$

$$
E_y =
kq\frac{y}{\left[(x+a)^2+y^2\right]^{3/2}}
+
2kq\frac{y}{\left[(x-a)^2+y^2\right]^{3/2}}
$$

---

## 2. Field on the $y$-axis: $\vec{E}(0,y)$

Set $x=0$ in the general expression:

$$
\vec{E}(0,y)
=
kq \frac{a\hat{i}+y\hat{j}}{(a^2+y^2)^{3/2}}
+
2kq \frac{-a\hat{i}+y\hat{j}}{(a^2+y^2)^{3/2}}
$$

Combine terms:

$$
\vec{E}(0,y)
=
\frac{kq}{(a^2+y^2)^{3/2}}
\left[
(a-2a)\hat{i} + (y+2y)\hat{j}
\right]
$$

$$
\vec{E}(0,y)
=
\frac{kq}{(a^2+y^2)^{3/2}}
\left[
-a\hat{i} + 3y\hat{j}
\right]
$$

Therefore,

$$
\boxed{
\vec{E}(0,y)=
\frac{kq}{(a^2+y^2)^{3/2}}
\left(-a\hat{i}+3y\hat{j}\right)
}
$$

---

## 3. Field on the $x$-axis: $\vec{E}(x,0)$

Set $y=0$ in the general formula:

$$
\vec{E}(x,0)
=
kq\frac{x+a}{|x+a|^3}\hat{i}
+
2kq\frac{x-a}{|x-a|^3}\hat{i}
$$

So,

$$
\boxed{
\vec{E}(x,0)=
\left[
kq\frac{x+a}{|x+a|^3}
+
2kq\frac{x-a}{|x-a|^3}
\right]\hat{i}
}
$$

Also,

$$
E_y(x,0)=0
$$

---

## 4. Conditions for $E_x=0$, $E_y=0$, and $\vec{E}=0$

### Condition for $E_y=0$

From the general formula,

$$
E_y =
kq\frac{y}{\left[(x+a)^2+y^2\right]^{3/2}}
+
2kq\frac{y}{\left[(x-a)^2+y^2\right]^{3/2}}
$$

Factor out $kqy$:

$$
E_y = kqy
\left[
\frac{1}{\left[(x+a)^2+y^2\right]^{3/2}}
+
\frac{2}{\left[(x-a)^2+y^2\right]^{3/2}}
\right]
$$

The bracket is always positive, so

$$
E_y = 0 \iff y=0
$$

Thus,

$$
\boxed{E_y=0 \text{ only on the } x\text{-axis}}
$$

---

### Condition for $E_x=0$ on the $x$-axis

Since $\vec{E}=0$ can only happen when $y=0$, solve along the $x$-axis:

$$
kq\frac{x+a}{|x+a|^3}
+
2kq\frac{x-a}{|x-a|^3}
=0
$$

Cancel $kq$:

$$
\frac{x+a}{|x+a|^3}
+
2\frac{x-a}{|x-a|^3}
=0
$$

The zero point lies between the charges, so assume

$$
-a < x < a
$$

Then

$$
|x+a| = x+a,\qquad |x-a| = a-x
$$

and

$$
\frac{x+a}{(x+a)^3} + 2\frac{x-a}{(a-x)^3}=0
$$

Since $x-a=-(a-x)$,

$$
\frac{1}{(x+a)^2} - \frac{2}{(a-x)^2}=0
$$

$$
\frac{1}{(x+a)^2} = \frac{2}{(a-x)^2}
$$

$$
(a-x)^2 = 2(x+a)^2
$$

Take square root:

$$
a-x = \sqrt{2}(x+a)
$$

Solve for $x$:

$$
a - x = \sqrt{2}x + \sqrt{2}a
$$

$$
a(1-\sqrt{2}) = x(1+\sqrt{2})
$$

$$
x = a\,\frac{1-\sqrt{2}}{1+\sqrt{2}}
$$

Rationalizing:

$$
x = a(2\sqrt{2}-3)
$$

Therefore,

$$
\boxed{x = a(2\sqrt{2}-3)}
$$

This is negative, so the zero-field point lies between the charges, closer to the smaller charge $+q$.

Hence,

$$
\boxed{\vec{E}=0 \text{ at } \left(a(2\sqrt{2}-3),\,0\right)}
$$

---

## 5. Numerical value of the field at $(0,y)$

Given:

- $a=0.2\,\text{m}$
- $y=0.3\,\text{m}$
- $q=2\,\mu\text{C}=2\times10^{-6}\,\text{C}$
- $k=8.99\times10^9\,\text{N·m}^2/\text{C}^2$

Use

$$
\vec{E}(0,y)=
\frac{kq}{(a^2+y^2)^{3/2}}
\left(-a\hat{i}+3y\hat{j}\right)
$$

First compute:

$$
a^2+y^2 = (0.2)^2+(0.3)^2=0.04+0.09=0.13
$$

$$
(a^2+y^2)^{3/2} = (0.13)^{3/2} \approx 0.0469
$$

$$
kq = (8.99\times10^9)(2\times10^{-6}) = 1.798\times10^4
$$

So the factor is

$$
\frac{kq}{(a^2+y^2)^{3/2}}
\approx
\frac{1.798\times10^4}{0.0469}
\approx 3.83\times10^5
$$

Now multiply:

$$
E_x \approx (3.83\times10^5)(-0.2)
= -7.66\times10^4\,\text{N/C}
$$

$$
E_y \approx (3.83\times10^5)(0.9)
= 3.45\times10^5\,\text{N/C}
$$

Therefore,

$$
\boxed{
\vec{E}(0,0.3)\approx
(-7.66\times10^4\,\hat{i}+3.45\times10^5\,\hat{j})\,\text{N/C}
}
$$

Magnitude:

$$
|\vec{E}| = \sqrt{E_x^2+E_y^2}
\approx \sqrt{(-7.66\times10^4)^2+(3.45\times10^5)^2}
\approx 3.53\times10^5\,\text{N/C}
$$

So,

$$
\boxed{|\vec{E}| \approx 3.53\times10^5\,\text{N/C}}
$$

---

## 6. Limit when $y \gg a$

Using

$$
\vec{E}(0,y)=
\frac{kq}{(a^2+y^2)^{3/2}}
\left(-a\hat{i}+3y\hat{j}\right)
$$

If $y \gg a$, then

$$
(a^2+y^2)^{3/2} \approx y^3
$$

Thus,

$$
\vec{E}(0,y) \approx \frac{kq}{y^3}\left(-a\hat{i}+3y\hat{j}\right)
$$

or

$$
\vec{E}(0,y) \approx -\frac{kqa}{y^3}\hat{i} + \frac{3kq}{y^2}\hat{j}
$$

Since the $x$-component falls off faster, the dominant term is

$$
\boxed{
\vec{E}(0,y)\approx \frac{3kq}{y^2}\hat{j}
\qquad (y\gg a)
}
$$

This matches the field of an effective total charge

$$
q_{\text{tot}} = q + 2q = 3q
$$

located approximately at the origin for very large $y$.

---

## Final Answers

### General field
$$
\boxed{
\vec{E}(x,y)=
kq \frac{(x+a)\hat{i}+y\hat{j}}{\left[(x+a)^2+y^2\right]^{3/2}}
+
2kq \frac{(x-a)\hat{i}+y\hat{j}}{\left[(x-a)^2+y^2\right]^{3/2}}
}
$$

### On the $y$-axis
$$
\boxed{
\vec{E}(0,y)=
\frac{kq}{(a^2+y^2)^{3/2}}
\left(-a\hat{i}+3y\hat{j}\right)
}
$$

### On the $x$-axis
$$
\boxed{
\vec{E}(x,0)=
\left[
kq\frac{x+a}{|x+a|^3}
+
2kq\frac{x-a}{|x-a|^3}
\right]\hat{i}
}
$$

### Zero-field point
$$
\boxed{
\vec{E}=0 \text{ at } \left(a(2\sqrt{2}-3),\,0\right)
}
$$

### Numerical field at $(0,0.3)$ for $a=0.2\,\text{m},\,q=2\,\mu\text{C}$
$$
\boxed{
\vec{E}\approx(-7.66\times10^4\,\hat{i}+3.45\times10^5\,\hat{j})\,\text{N/C}
}
$$

### Far-field limit
$$
\boxed{
\vec{E}(0,y)\approx \frac{3kq}{y^2}\hat{j}
\qquad (y\gg a)
}
$$
