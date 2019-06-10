# Formelsammlung LINALG

## Matrizen

### Rechenregeln

- Vorsicht! Addition nur mit Matrizen von gleichem Format möglich
- Vorsicht! Multiplikation nur möglich, wenn die Anzahl Spalten der ersten Matrix gleich der Anzahl Zeilen der zweiten ist $(m \times n) \bullet (n \times p) = (m \times p)$
- $(A + B) + C = A + (B + C)$
- $A + B = B + A$
- $A(BC) = (AB)C$
- $\bold{AB \neq BA}$ auch nicht für quadratische Matrizen!
- $A(B + C) = AB + AC$
- $A^p A^q = A^{p+q}$
- $AA^{-1} = A^{-1}A = I \text{ nur für quadratische Matrizen}$
- $(AB)^{-1} = A^{-1} B^{-1}$
- $(AB)^{T} = A^{T} B^{T}$

### Transponieren

$$
\begin{aligned}
    A &=
    \begin{bmatrix}
    1 & 0 & 3 \\
    2 & 3 & 5
    \end{bmatrix} \\
    A^T &=
    \begin{bmatrix}
    1 & 2 \\
    0 & 3 \\
    3 & 5
    \end{bmatrix}
\end{aligned}
$$

Matrix $A$ gilt als **symmetrisch**, falls $A^T = A$