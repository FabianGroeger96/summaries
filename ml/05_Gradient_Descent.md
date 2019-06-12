# Gradient Descent


## Partial Derivates

- Vorstellen, dass die Funktion nur von $x$ abhängt, alle anderen Variablen (z.B. $y$) sind Konstanten, danach gewöhnliche Ableitung berechnen
- Das Resultat wird als partielle Ableitung von $f$ mit Respekt zu $x$ bezeichnet

$$ \frac{df}{dx}|_{y=constant} $$

### Beispiel

Berechne die partielle Ableitung von $f(x,y) = (3x + 2y)^2$ mit Respekt zu $x$ und $y$ und vorallem im Punkt $(x,y) = (1,2)$

$$
\begin{aligned}
    \text{using chain rule:} \\
    \frac{df}{dx} &= 2(3x+2y) * \frac{d}{dx} (3x+2y) = 2(3x+2y) * 3 = 6(3x+2y) \\
    \frac{df}{dy} &= 2(3x+2y) * \frac{d}{dy} (3x+2y) = 2(3x+2y) * 2 = 4(3x+2y) \\
    \text{im Punkt (1,2):} \\
    \frac{df}{dx}|_{(x,y) = (1,2)} &= 6(3x+2y)|_{(x,y) = (1,2)} = 6(3*1 + 2*2) = 42 \\
    \frac{df}{dy}|_{(x,y) = (1,2)} &= 4(3x+2y)|_{(x,y) = (1,2)} = 4(3*1 + 2*2) = 28
\end{aligned}
 $$

## Gradient

- Der Gradient $\nabla f$ ist ein Vektor, welcher aus den partiellen Ableitungen zusammengesetzt wird

$$ \nabla f(x,y) = \Bigg[\frac{f_x (x,y)}{f_y (x,y)}\Bigg] $$

### Beispiel

Berechne den Gradienten von $f(x,y) = (3x + 2y)^2$ und vorallem im Punkt $(x,y) = (1,2)$

$$
\begin{aligned}
    \nabla f(x,y) &= \Bigg[\frac{6(3x+2y)}{4(3x+2y)}\Bigg] \\
    \text{im Punkt (1,2):} \\
    \nabla f(1,2) &= \Bigg[\frac{42}{28}\Bigg]
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

## Batch Gradient Descent

- Minimieren der Kostenfunktion

$$ J(\theta) = \frac{1}{2n} \sum_{i=1}^n (h(\theta, x^{(i)}) - y^{(i)})^2 $$

$$ h(\theta, x^{(i)}) = \hat{y}^{(i)} = \theta_0 + \theta_1x_1^{(i)} + ... + \theta_mx_m^{(i)} $$

- Wir starten mit einem initialen Parametervektor $\theta_0$ und wiederholen

$$ \theta_{k+1} = \theta_k - \alpha\nabla J(\theta_k), k = 1,2,3,... $$

**Nur python code können, muss nicht auf Papier angewandt werden**

### Eigenschaften

- Die Aktualisierung des Parametervektors $\theta$ erfolgt auf einmal mit Hilfe des gesamten Satzes von $n$ Trainigspunkten
- Wenn $n$ grösser als $10^6$ ist, wird es langsam
- Mögliche Alternative wäre ein upgrade von $\theta$ für jedes einzelne Trainingsbeispiel, wird normalerweise durch zufälliges Mischen der Trainingspunkte gemacht und aktualisieren von $\theta$ nach jedem Trainingspunkt
- Diese Methode kann schneller sein als die Batch Methode

## Stochastic Gradient Descent

- Wähle einen initialen Vektor von Parametern $\theta$ und learning rate $\alpha$
- Wiederholen bis ein ungefähres Minimum erhalten wurde
- **Der Unterschied zu Batch Gradient Descent ist, dass nur ein Teil des Datasets gebraucht wird um den zu aktualisierenden Parameter zu berechnen, und dieser einer Teil wird zufällig gewählt**

**Nur python code können, muss nicht auf Papier angewandt werden**

## Polynomiale Regression

- Wenn wir keine lineare Beziehung zwischen den Features und dem erwarteten Ergebnis haben, z.B. wie

$$ h(\theta,x) = \theta_0 + \theta_1x + \theta_1x^2 + \theta_1x^3 $$

- Könnten wir die gewählten Features $x_1 = x, x_2 = x^2, x_3 = x^3$ wählen und wir haben wieder eine lineare Regression

$$ h(\theta,x) = \theta_0 + \theta_1x_1 + \theta_1x_2 + \theta_1x_3 $$

- **Umbedingt zuerst feature scaling anwenden!**

### Feature Scaling

- Die Merkmale müssen in ähnlicher Grössenordnung sind und bringen Sie jedes Merkmal in ungefähr ein $-1 \leq x_i \leq 1$ Bereich
- Ersetzen von $x_i$ mit $x_i - \bar{x}_i$ so dass die Merkmale in etwa einem Mittelwert von 0 bekommen, nicht $x_0 = 1$ anwenden
- Dividieren von $x_i - \bar{x_i}$ durch $\text{max } x_i - \text{min } x_i$ oder durch die Standardabweichung von $x_i$
- **Wird gebraucht um das Konvergenzverhalt zu verbessern von GD**

### Checking Convergence

- Um zu testen ob GD korrekt funktioniert, plottet man die Kostenfunktion $J(\theta)$ gegen die Nummer an Iterationen
- Konvergenz erklähren, wenn $J(\theta)$ um weniger als $10^{-3}$ in einer Iteration abnimmt
- Für sehr kleine $\alpha$, $J(\theta)$ sollte sich in jeder Iteration verringern
- Zu kleine $\alpha$ für zu sehr langsamen Konvergenz
- Bei zu grossem $\alpha$ kann es sein, dass GD nicht konvergiert
- Starten mit $\alpha = 0.001$ und danach mit 0.003, 0.01, 0.03, 0.1, ...
