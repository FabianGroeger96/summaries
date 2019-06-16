# Gradient Descent

### Partielle Ableitung

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

$$ \nabla f(x,y) = \Bigg[\frac{f_x (x,y)}{f_y (x,y)}\Bigg] $$

### Beispiel

Berechne den Gradienten von $f(x,y) = (3x + 2y)^2$ und vorallem im Punkt $(x,y) = (1,2)$

$$
\begin{aligned}
    \nabla f(x,y) &= \underline{\underline{\Bigg[\frac{6(3x+2y)}{4(3x+2y)}\Bigg]}} \\
    \text{im Punkt (1,2):} \\
    \nabla f(1,2) &= \underline{\underline{\Bigg[\frac{42}{28}\Bigg]}}
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
    \nabla f(x,y) &= \Bigg[\frac{2x + 2y}{2x + 8y}\Bigg]\\
\end{aligned}
$$

- wir starten am Punkt $x_0 = (2,2)$ und gehen in die Richtung des negativen Gradienten

$$
\begin{aligned}
    x_1 &= x_0 - \alpha\nabla f(x_0) \\
    &= \Bigg[\frac{2}{2}\Bigg] - \alpha \Bigg[\frac{8}{20}\Bigg] = \Bigg[\frac{1.2}{0}\Bigg] \\
\end{aligned}
$$

- wir haben $\alpha = 0.1$ gewählt (Learningrate)

$$
\begin{aligned}
    x_2 &= x_1 - \alpha\nabla f (x_1)\\
    &= \Bigg[\frac{1.2}{0}\Bigg] - \alpha \Bigg[\frac{2.4}{2.4}\Bigg] = \Bigg[\frac{0.96}{-0.24}\Bigg]
\end{aligned}
$$
