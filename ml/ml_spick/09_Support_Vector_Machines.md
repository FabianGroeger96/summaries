# Support Vector Machines

## Hessian Normal Form

$$
    n \bullet (x - x_0) \Leftrightarrow n \perp (x - x_0)
$$

### Beispiel

$$ \includegraphics[width=0.4\columnwidth]{images/hessian_normal_form_example.png} $$

Berechne die hessische Normalform von $\vec{n} = \frac{1}{\sqrt{13}}\begin{bmatrix}2 \\3\end{bmatrix}$

$$
\begin{aligned}
    0 = \vec{n} \bullet (\vec{x} - \vec{x_0}) &= \frac{1}{\sqrt{13}}
    \begin{bmatrix}
    2 \\
    3
    \end{bmatrix} \bullet \Bigg(\begin{bmatrix}
    x \\
    y
    \end{bmatrix} - 
    \begin{bmatrix}
    0.5 \\
    2
    \end{bmatrix}\Bigg) =
    \frac{1}{\sqrt{13}}
    \begin{bmatrix}
    2 \\
    3
    \end{bmatrix} \bullet \begin{bmatrix}
    x - 0.5 \\
    y - 2
    \end{bmatrix} \\
    &= \frac{1}{\sqrt{13}} (2(x-0.5) + 3(y-2)) \\
    &= \frac{1}{\sqrt{13}} (2x + 3y -1 -6) \\
    &= \frac{2}{\sqrt{13}}x + \frac{3}{\sqrt{13}}y - \frac{7}{\sqrt{13}} \\
    &\text{(von der Form ax + by + c = 0)} \\
    \\
    \vec{n} &= \begin{bmatrix}
    \frac{2}{\sqrt{13}} \\
    \frac{3}{\sqrt{13}}
    \end{bmatrix}
\end{aligned}
$$