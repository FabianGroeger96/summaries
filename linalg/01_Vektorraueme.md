# Vektorräume

## Vektorraum

Menge $V$ heisst **Vektorraum**, wenn zwei Operationen definiert sind:

$$
\begin{aligned}
    v, w \in V &\mapsto v + w \in V &\quad \text{(Addition)} \\
    v \in V, s \in \mathbb{R} &\mapsto sv \in V &\quad \text{(skalare Multiplikation)}
\end{aligned}
$$

- Nullraum $V = {0}$, ist der kleinste Vektorraum
- Menge der reellen Zahlen $V = \mathbb{R}$ ist ein Vektorraum
- Für alle $m,n \in \mathbb{N}$ ist die Menge $V = \mathbb{R}^{m\times n}$ ein Vektorraum

## Funktionenraum

- verhalten sich bezüglich der Addition und skalaren Multiplikation genau wie Vektoren
- Der Nullvektor wird im Funktionenraum als Nullfunktion bezeichnet, Funktion welche jedem $x$ den Wert $0$ zuordnet

$$
\begin{aligned}
    (f + g)(x) &= f(x) + g(x) \qquad &\text{für alle } x \in \mathbb{R} \\
    (s f)(x) &= sf(x) \qquad &\text{für alle } x \in \mathbb{R}
\end{aligned}
$$

## Unterraum

- Teilmenge eines Vektorraums, die ihrerseits wieder ein Vektorraum ist
- Teilmenge $U \subseteq V$ eines Vektorraums $V$ heisst Unterraum, falls:

$$
\begin{aligned}
    &U_1) \quad \vec{0} \in U \\
    &U_2) \quad v,w \in U \mapsto v + w \in U \\
    &U_3) \quad v \in U, s \in \mathbb{R} \mapsto sv \in U
\end{aligned}
$$

### Beispiel

$$
\begin{aligned}
    &U = \left\{
        \begin{bmatrix}
        x_1 \\
        x_2
        \end{bmatrix}
        \in \mathbb{R}^2 \Bigg\vert x_1 + 2x_2 = 0
    \right\} \\
    &\text{Ist $U$ ein Unterraum von $\mathbb{R}^2$?} \\
    \\
    &U_1) \quad x = \begin{bmatrix}
        0 \\
        0
    \end{bmatrix} \\
    &U_1) \quad x_1 + 2x_2 = 0 \quad \rightarrow \quad 0 + 2 \cdot 0 = 0  \quad \checkmark \\
    \\
    &U_2) \quad x = \begin{bmatrix}
        x_1 \\
        x_2
    \end{bmatrix}, \quad y = \begin{bmatrix}
        y_1 \\
        y_2
    \end{bmatrix} \in U \\
    &U_2) \quad x_1 + 2x_2 = 0, \quad y_1 + 2y_2 = 0 \\
    &U_2) \quad (x_1 + y_1) + 2(x_2 + y_2) = 0 \\
    &U_2) \quad = x_1 + y_1 + 2x_2 + 2y_2 = (x_1 + 2x_2) + (y_1 + 2y_2) = 0 \quad \checkmark \\
    \\
    &U_3) \quad x = \begin{bmatrix}
        x_1 \\
        x_2
    \end{bmatrix} \\
    &U_3) \quad x_1 + 2x_2 = 0 \\
    &U_3) \quad s(x_1 + 2x_2) = 0 \\
    &U_3) \quad = s\cdot x_1 + s\cdot2x_2 = (sx_1) + 2(sx_2) = 0 \quad \checkmark \\
\end{aligned}
$$

## Aufgespannte Unterraum

- Der von einer Menge Vektoren aufgespannte Unterraum ist der kleinste Unterraum, der diese Vektoren enthält
- Der von einem Vektor $v$ erzeugte Unterraum ist also eine Gerade, wenn $v \neq 0$
- Der von zwei Vektoren aufgespannte Unterraum ist eine Ebene, wenn die beiden Vektoren linear unabhängig sind (kein skalares Vielfaches gibt um aus dem einten Vektor den anderen zu machen)