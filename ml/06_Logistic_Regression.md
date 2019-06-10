# Logistic Regression

## Wieso Logistic Regression

- Die logistische Regressionsanalyse wird gebraucht um zu überprüfen ob und wie eine abhängige variable $y = {0, 1}$ von einer oder mehreren unabhängigen Variablen $x$ abhängt
- Beispiel abhängige Variablen:
  - Email: Spam ($y = 1$) oder kein Spam ($y = 0$)
  - Person: Krimineller ($y = 1$) oder kein Krimineller ($y = 0$)
  - Student: besteht Prüfung ($y = 1$) oder besteht nicht ($y = 0$)
- unabhängige Variablen sind Metriken oder Encoded Dummy-Variablen im Fall von kategorischen Variablen, zum Beispiel:
  - Email: Vorkommen von Wörtern, Rechtschreibfehler, etc.
  - Person: Aktivitäten, Kollegen, Arbeit, etc.
  - Student: Gelernte Stunden, Partys, genügend Schlaf, etc.
- unabhängige Variablen sollten nicht gross Korreliert sein
- Im Kern der Methode wird die logistische Funktion verwendet, auch Sigmoidfunktion genannt

## Logistische Funktion (Sigmoid)

- Logistische Regression sagt Wahrscheinlichkeiten vorher
- Aufgrund dieser Wahrscheinlichkeiten kann man klassifizieren

$$ \sigma(z) = \frac{1}{1 + e^{-z}}, z \in \mathbb{R} $$

$$ \sigma^{\prime}(z) = \sigma(z)(1 - \sigma(z)) $$

$$ \sigma^{\prime\prime}(z) = \sigma(z)(1 - \sigma(z))(1 - 2\sigma(z)) $$

Beispiel einer logistischen regressions Funktion, mit einer input Variable $x$:

$$ y = \sigma(\theta_0 + \theta_1x) = \frac{1}{1 + e^{-(\theta_0 + \theta_1x)}} $$

$$ z = \theta_0 + \theta_1x $$

$$ \includegraphics[width=0.7\columnwidth]{images/sigmoid_funktion.png} $$

- blaue Punkte: $y = 1$, Prüfung bestanden
- grüne Punkte: $y = 0$, Prüfung nicht bestanden
- Sigmoid Funktion liefert eine Wahrscheinlichkeit zu welcher Klasse $y = 1$ oder $y = 0$ der Datenpunkt gehört
- Alles mit einer Wahrscheinlichkeit höher als 0.5 gehört zu der Klasse $y = 1$ und alles kleiner als 0.5 gehört zu der Klasse $y = 0$

### Beispiel

Model sagt vorher ob ein Student eine Frau oder ein Mann ist, aufgrund seiner/ihrer Körpergrösse. Gehört die Grösse $h = 155cm$ zu einer weiblichen Studentin oder einem männlichen?

Wir gehen davon aus, dass der Algorithmus $\theta_0 = -100$ und $\theta_1 = 0.6cm^-1$ gelernt. Aufgrund dieser Parameter kann man die Wahrscheinlichkeit $P(male|h = 155cm)$ ausrechnen.

$$ 
\begin{aligned}
    P(male|h = 155cm) &= \hat{y} = \frac{1}{1 + exp(-(\theta_0 + \theta_1x))} = \frac{1}{1 + exp(100 - 0.6 * 155)} \\
    &= \frac{1}{1 + exp(7)} = 0.9 x 10^{-3}
\end{aligned}
$$

Die Wahrscheinlichkeit ist fast 0, dass der Student männlich ist.

## Linear Descision Boundaries

$$ h(\theta, x) = x^T\theta = \theta_0 + \theta_1x_1 + \theta_2x_2 = 0 $$

- Falls $\vec{x}$ gegeben, kann man bestimmen zu welcher Klasse $\vec{x}$ gehört
- Wir sagen $y = 1$ vorher, wenn $x^T\theta \geq 0$ und $y = 0$ wenn $x^T\theta < 0$

### Beispiel

$$ \includegraphics[width=0.7\columnwidth]{images/linear_decision_boundaries.png} $$

Decision Boundary ist gegeben durch $\theta = [-1.8, -3.9, 4.5]^T$, dies ergibt die Gleichung der roten Linie $-1.8 - 3.9x_1 + 4.5x_2 = 0$

Die Wahrscheinlichkeit des feature Vektors $(x_1, x_2) = (2.2, 2.7)$ (blauer Kreis) ist gegeben durch:

$$
\begin{aligned}
    \sigma(-1.8 - 3.9 \cdot 2.2 + 4.5 \cdot 2.7) = \sigma(3.57) = 0.973 \geq 0.5 \\
    \text{Gehört somit zur Klasse: } y = 1
\end{aligned}
$$

Die Wahrscheinlichkeit des feature Vektors $(x_1, x_2) = (3.5, 3)$ (grüner Kreis) ist gegeben durch:

$$ 
\begin{aligned}
    \sigma(-1.8 - 3.9 \cdot 3.5 + 4.5 \cdot 3) = \sigma(-1.95) = 0.125 < 0.5 \\
    \text{Gehört somit zur Klasse: } y = 0
\end{aligned}
$$

## Maximum Likelihood Estimation (MLE)

- Wie gross ist die Wahrscheinlichkeit, dass ein $x$ richtig klassifiziert wird?

$$ p(y|x) = \hat{y}^y (1 - \hat{y})^{1 - y} $$

## Gradient Descent

Es sind $n$ Beispiele im Trainingsset gegeben, $(x^{(i)}, y^{(i)}), i = 1,2,..., n$ mit einem binären Klassifikationsproblem $(y \in {0,1})$, wird gebraucht um den Parametervektor $\theta$ zu finden

1. Starte mit einem zufälligen Parametervektor $\theta_0$
2. Iteriere bis es konvergiert

$$ 
\begin{aligned}
    \theta_{k+1} = \theta_k - \alpha \frac{1}{n} \sum_{i=1}^n (h(\theta_k, x^{(i)}) - y^{(i)}) x^{(i)}, k = 0,1,2,3,... \\
    \text{mit: } h(\theta, x^{(i)}) = \sigma((x^{(i)})^T\theta) \\
    \text{und: } \sigma(z) = \frac{1}{1 + e^{-z}}
\end{aligned}
$$

## (Binary) Classification

- Wenn wir mehr als zwei Klassen haben, müssen wir die Methode "einer gegen die anderen" anwenden
- Wenn wir drei Klassen haben: 1. Klasse gegen 2. & 3. Klasse / 2. Klasse gegen 1. & 3. Klasse / 3. Klasse gegen 1. & 2. Klasse
- Für alle diese 3 Fälle findet man einen Parametervektor $\theta_i (i = 1,2,3)$
- Feature Vektor $x$ ist in der Klasse $i$, wenn der Wert von $\sigma(x^T\theta_k)$ in der Klasse $i$ am grössten ist

$$ i = argmax \sigma(x^T\theta_k) $$

### Beispiel

| k   | $\sigma(x^T\theta_k)$ |
| --- | --------------------- |
| 1   | 0.2                   |
| 2   | 0.3                   |
| 3   | 0.8                   |

$\rightarrow i = 3$, weil $\sigma(x^T\theta_k)$ am grössten ist
