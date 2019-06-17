# Gradient Descent

## Ableitungsregeln

$$
\begin{aligned}
    x^n &\rightarrow n \cdot x^{n-1} \\
    g(x) \cdot h(x) &\rightarrow g(x) \cdot h^{\prime}(x) + g^{\prime}(x) \cdot h(x) \\
    (g(x))^n &\rightarrow n\cdot (g(x))^{n-1} \cdot g^{\prime}(x) \\
    \frac{g(x)}{h(x)} &\rightarrow \frac{h(x) \cdot g^{\prime}(x)-g(x)\cdot h^{\prime}(x)}{(h(x))^2} \\
    h(g(x)) &\rightarrow h^{\prime}(g(x)) \cdot g^{\prime}(x)
\end{aligned}
$$

## Partielle Ableitung

Berechne die partielle Ableitung von $f(x,y) = (3x + 2y)^2$ mit Respekt zu $x$ und $y$ und vorallem im Punkt $(x,y) = (1,2)$

$$
\begin{aligned}
    \text{using chain rule:} \\
    \frac{df}{dx} &= 2(3x+2y) \cdot \frac{d}{dx} (3x+2y) \\
    &= 2(3x+2y) \cdot 3 = \underline{\underline{6(3x+2y)}} \\
    \frac{df}{dy} &= 2(3x+2y) \cdot \frac{d}{dy} (3x+2y) \\
    &= 2(3x+2y) \cdot 2 = \underline{\underline{4(3x+2y)}} \\
    \text{im Punkt (1,2):} \\
    \frac{df}{dx}|_{(x,y) = (1,2)} &= 6(3x+2y)|_{(x,y) = (1,2)} \\
    &= 6(3\cdot1 + 2\cdot2) = \underline{\underline{42}} \\
    \frac{df}{dy}|_{(x,y) = (1,2)} &= 4(3x+2y)|_{(x,y) = (1,2)} \\
    &= 4(3\cdot1 + 2\cdot2) = \underline{\underline{28}}
\end{aligned}
 $$

## Gradient

- Der Gradient $\nabla f$ ist ein Vektor, welcher aus den partiellen Ableitungen zusammengesetzt wird

$$ \nabla f(x,y) = \begin{bmatrix}
    f_x (x,y) \\
    f_y (x,y)
\end{bmatrix}
$$

### Beispiel

Berechne den Gradienten von $f(x,y) = (3x + 2y)^2$ und vorallem im Punkt $(x,y) = (1,2)$

$$
\begin{aligned}
    \nabla f(x,y) &= \underline{\underline{
        \begin{bmatrix}
            6(3x+2y) \\
            4(3x+2y)
        \end{bmatrix}}} \\
    \text{im Punkt (1,2):} \\
    \nabla f(1,2) &= \underline{\underline{
        \begin{bmatrix}
            42 \\
            28
        \end{bmatrix}}}
\end{aligned}
$$

### Eigenschaften

- Der Gradient zeigt in die Richtung der maximalen Zunahme der Funktion
- Der negative Gradient zeigt in die Richtung der maximalen Abnahme der Funktion
- Wenn der Gradient an einem Punkt 0 ist, ist es ein lokales Extrema (lokales Minimum oder lokales Maximum)
- Der Gradient einer Funktion steht senkrecht zu den Konturlinien dieser Funktion

### Contour Lines

- Konturlinien einer Funktion $z = f(x,y)$ sind Kurven in der Domäne von $f$ welche die Funktion $f(x,y) = c$ erfüllen, wobei $c$ eine Konstante ist

## Gradient Descent

- Wenn wir ein (lokales) Minimum einer Funktion finden wollen, müssen wir uns in die Richtung des negativen Gradient bewegen
- Weil der Gradient sich ständig ändert, muss man sehr kleine Schritte nehmen

### Beispiel

$$
\begin{aligned}
    f(x,y) &= x^2 + 2xy + 4y^2 \\
    \nabla f(x,y) &= 
        \begin{bmatrix}
            2x + 2y \\
            2x + 8y
        \end{bmatrix}
\end{aligned}
$$

- wir starten am Punkt $x_0 = (2,2)$ und gehen in die Richtung des negativen Gradienten
- wir haben $\alpha = 0.1$ gewählt (Learningrate)

$$
\begin{aligned}
    x_1 &= x_0 - \alpha\nabla f(x_0) \\
    &= \begin{bmatrix}
            2 \\
            2
        \end{bmatrix} - \alpha \begin{bmatrix}
            8 \\
            20
        \end{bmatrix} = \begin{bmatrix}
            1.2 \\
            0
        \end{bmatrix} \\
    \\
    x_2 &= x_1 - \alpha\nabla f (x_1)\\
    &= \begin{bmatrix}
            1.2 \\
            0
        \end{bmatrix} - \alpha \begin{bmatrix}
            2.4 \\
            2.4
        \end{bmatrix} = \begin{bmatrix}
            0.96 \\
            -0.24
        \end{bmatrix}
\end{aligned}
$$
