# Support Vector Machines

## Hessian Normal Form

$$
    n \bullet (x - x_0) \Leftrightarrow n \perp (x - x_0)
$$

### Beispiel

$$ \includegraphics[width=0.5\columnwidth]{../images/hessian_normal_form_exercise.png} $$

Write down the HNF of $g$ (red line in right figure) which is perpendicular to $w$ and compute, using the HNF, the distance of point (2,5) from $g$. Identify +HP and -HP.
Make sure to normalize $w$ to length 1. Convert the HNF to the form

$$ ax + by + c = 0$$

Check Your results by inserting points on the line into the corresponding equations!

1. Normalisieren von $w = [3,4]^T$

$$
\begin{aligned}
    \text{Länge von w} = \sqrt{3^2 + 4^2} = 5 \\
    n = \frac{1}{5}\begin{bmatrix}
    3 \\
    4
    \end{bmatrix}
\end{aligned}
$$

2. Berechnen der Hessian normal form (HNF) der geraden Linie in Vektornotation

$$
\begin{aligned}
    \vec{n} \bullet (\vec{x} - \vec{x_0}) &= \frac{1}{5}
    \begin{bmatrix}
    3 \\
    4
    \end{bmatrix} \bullet \Bigg(\begin{bmatrix}
    x \\
    y
    \end{bmatrix} -
    \begin{bmatrix}
    2 \\
    1
    \end{bmatrix}\Bigg) \\
    &= \frac{1}{5}
    \begin{bmatrix}
    3 \\
    4
    \end{bmatrix} \bullet \begin{bmatrix}
    x - 2 \\
    y - 1
    \end{bmatrix} = 0
\end{aligned}
$$

3. Berechnen der HNF in Koordinatenform

$$
\begin{aligned}
    &\frac{1}{5}
    \begin{bmatrix}
    3 \\
    4
    \end{bmatrix} \bullet \begin{bmatrix}
    x - 2 \\
    y - 1
    \end{bmatrix} = \frac{1}{5}(3(x-2) + (4(y-1))) \\
    &= \frac{1}{5}(3x + 4y -10) = \frac{3}{5}x + \frac{4}{5}y - 2 = 0 \\
    &d = -2 \rightarrow \text{Ursprung auf der negativen Halbseite ist}
\end{aligned}
$$

4. Überprüfen des Resultats mit dem Punkt $[-2,4]^T$

$$ \frac{3}{5}(-2) + \frac{4}{5}4 - 2 = -\frac{6}{5} + \frac{16}{5} - 2 = 0 $$

$$ \text{Punkt erfüllt die Gleichung, liegt demnach auf der Gerade} $$
