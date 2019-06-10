# Regularization

## Under- and Overfitting

- **Underfitting** (high bias) bedeutet, dass das Modell nicht komplex genug ist, um genügend Muster im Trainingsset zu erkennen und zeigt daher schlechte Performanz auf dem Testset, ungesehenen Daten
- **Overfitting** bedeutet, dass das Modell gute Performanz auf den Trainingsdaten hat, aber nicht gute Performanz auf dem Testset, ungesehenen Daten. Es wird auch als **high variance** bezeichnet, was bedeutet, dass eine kleine Änderung in dem Trainingsset den Parameter des Modells drastisch ändert

$$ \includegraphics[width=0.7\columnwidth]{images/under_overfitting.png} $$

## High/Low Bias and High/Low Variance

- **Low Bias**: Durchschnittswert ist im Zentrum (korrekt)
- **High Bias**: Durchschnittswert ist weit weg vom Zentrum (nicht korrekt)
- **Low Variance**: Werte sind nicht weit verteilt
- **High Variance**: Werte sind weit verteilt

$$ \includegraphics[width=0.7\columnwidth]{images/high_low_bias_and_high_low_variance.png} $$

## Adressing Overfitting

- Mögliche Optionen
  - Reduzieren der Anzahl an Features (Parameter)
    - Manuell selektieren, welche Features behalten werden
    - Model selection algorithm
  - Regularisierung
    - Alle Features behalten, aber die Grösse der Parameter $\theta_i$ verringern
    - Funktioniert gut, wenn es viele Features gibt, und jedes davon nur ein wenig zur Vorhersage von $y$ beiträgt

## Ridge Regularisierung

$$ J(\theta) = \frac{1}{2n} \Bigg[\sum_{i=1}^n (h(\theta, x^{(i)}) - y^{(i)})^2 + \lambda\sum_{j=1}^m \theta_i^2 \Bigg] $$

- Die zweite Summe geht von 1 bis zu der Anzahl an Features $m$ und beinhaltet $\theta_0$ nicht
- Regularisierungsparameter sind $\theta_1, \theta_2, ..., \theta_n$
- Der Regularisierungshyperparameter $\lambda$ kontrolliert die Menge an Regularisierung
  - $\lambda = 0$, keine Regularisierung
  - $\lambda = \infty$, Underfitting, weil nur $\theta_0$ nicht 0 ist
- In der Ridge Regularisierung wählt man $\theta$, so dass man $J(\theta)$ minimiert

## Allgemeines Verfahren: Parameter Norm Penalties

- Einführung der Normstrafe $\Omega(\theta)$, die grosse Werte von $\theta$ bestraft
- Brauchen der regularisierten Kostenfunktion

$$ \tilde{J}(\theta; X, y) = J(\theta; X, y) + \lambda\Omega(\theta) $$

- Die gewöhnlichste Normstrafe $\Omega(\theta)$ ($L^2$ parameter (oder Ridge) Regularisierung):

$$ \Omega_R(\theta) = \frac{1}{2n} \sum_{k=1}^m \theta_k^2 $$

- $L^1$ parameter (oder LASSO) Regularisierung

$$ \Omega_L(\theta) = \frac{1}{n} \sum_{k=1}^m |\theta_k| $$

## Allgemeines Verfahren: Elastische Regularisierung

- Wird eine Kombination von Ridge und LASSO Regularisierung gebraucht
- Im Fall von $r = 0$ hat man eine pure Ridge Regularisierung
- Im Fall von $r = 1$ hat man eine pure LASSO Regularisierung

$$ \tilde{J} = J(\theta;X,y) + \lambda[r\Omega_L(\theta) +  (1 - r)\Omega(\theta)] $$

## Wie wählt man den Regularisierungshyperparameter $\lambda$

- Aufteilen der Daten in
  - Trainingsset (60 %), $(x^{(i)}, y^{(i)}), i = 1,...,n$
  - Cross Validation Set (20 %), $(x_{cv}^{(i)}, y_{cv}^{(i)}), i = 1,...,n_{cv}$
  - Testset (20 %), $(x_t^{(i)}, y_t^{(i)}), i = 1,...,n_t$
- Für jeden Wert des Regularisierungshyperparameters $\lambda$ berechnen des Parametervektors $\theta$, indem man den Trainingserror $J_{train}(\theta)$ minimiert
  - Pfad 1: $\lambda = 0 \rightarrow min J_{train}(\theta) \rightarrow \theta^{(1)} \rightarrow J_{CV}(\theta^{(1)})$
  - Pfad 2: $\lambda = 0.01 \rightarrow min J_{train}(\theta) \rightarrow \theta^{(2)} \rightarrow J_{CV}(\theta^{(2)})$
  - Pfad 3: $\lambda = 0.01 \rightarrow min J_{train}(\theta) \rightarrow \theta^{(3)} \rightarrow J_{CV}(\theta^{(3)})$
  - ...
- Für jeden Wert des Regularisierungshyperparameters $\lambda$ zeichne den Fehler auf dem Trainingsset $J_{train}(\lambda^{(\lambda)}$ und den Fehler auf dem Cross Validation Set $J_{CV}(\theta^{(\lambda)}$
- Wähle $\lambda$ so, dass der Fehler auf dem Cross Validation Set am kleinsten ist

## Wie verhindert man Under- oder Overfitting

### Hold-out (oder Simple) Cross Validation

1. Zufälliges aufteilen von $S$ in $S_{train}$ (70% der Daten) und $S_{cv}$ (30% der Daten)
2. Für jedes $k$ (Grad des Polynoms), trainiere das Modell $M_k$ auf dem $S_{train}$ um $\theta_k$ zu bekommen (Parametervektor für das Polynom mit Grad $k$)
3. Wähle $\theta_k$ so, dass es den kleinsten Fehler auf dem Cross Validation Set hat

$$ k = \text{argmin } \hat{\epsilon}_{S_{cv}}(\theta_k) $$

Problem: Verschwendet 30% der Daten

### k-fold Cross Validation

1. Zufälliges aufteilen von $S$ in $l$ disjunkte Subsets $S_1, S_2, ..., S_l$ mit $\frac{n}{l}$ Trainingssamples in jedem Subset
2. Für jedes $k$ (Grad des Polynoms), trainiere das Modell $M_k$ auf allen Subsets, bis auf ein Subset und teste das Modell auf dem einen Subset
3. Wähle das Modell $M_k$ mit den kleinsten Fehler und trainiere es auf dem ganzen $S$
