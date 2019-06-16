# Diverses

## Maximum Likelihood Estimation (MLE)

- Wie gross ist die Wahrscheinlichkeit, dass ein $x$ richtig klassifiziert wird?

$$ p(y|x) = \hat{y}^y (1 - \hat{y})^{1 - y} $$

## Normalisierung

- Der Prozess, jedes Attribut auf ungefähr die gleiche Skala zu bringen
- Die Skala in jeder Dimension hängt von den Daten ab: der größte Preis in einer Autodatenbank ist 698000 CHF, die größte Anzahl der Türen beträgt nur 6
- Eine Preisabweichung von 15% hat einen viel stärkeren Einfluss auf Ähnlichkeit und Entfernung als eine Abweichung von 15% in der Anzahl der Türen
- Solche starken Einflüsse auf die Attribute verfälschen die Ergebnisse der Algorithmen insbesondere wenn sie auf Distanz oder Ähnlichkeit beruhen
- Strategien:
  - **Min-Max Normalisierung**, transformiert die Daten in einen Intervall [0,1]
  $$ X_{norm} = \frac{X - X_{min}}{X_{max}-X_{min}} $$
  - **Z-Score Normalisierung**, transformiert die Daten so, dass der Mittelwert 0 und die Standardabweichung 1 wird
  $$ z = \frac{x - \mu}{\sigma} $$

## Levenshtein Distanz

Zählen der minimalen Anzahl von Änderungen, die erforderlich sind, um eine Zeichenkette in eine andere umzuwandeln:

- Anzahl +1 beim Löschen eines Zeichens
- Anzahl +1 beim Hinzufügen eines Zeichens
- Anzahl +2 beim Ändern eines Zeichens

## Wie misst man Regressionsfehler

- Residuum (residuals) sind berechnete Grössen welche den vertikalen Abstand zwischen Beobachtungspunkt und der Regressionsgerade messen
- Mean Absolut Error (MAE), macht Sinn

$$ \frac{1}{m} \sum_{i=1}^m |y_i - \hat{y_i}| $$

- Mean Squared Error (MSE), macht Sinn

$$ \frac{1}{m} \sum_{i=1}^m (y_i - \hat{y_i})^2 $$

## $R^2$ Coefficient of Determination

$$ R^2 = 1 - \frac{\frac{1}{m} \sum_{i=1}^{m}(y_i - f_i)^2}{\frac{1}{m} \sum_{i=1}^m(y_i - \bar{y})^2} = 1 - \frac{\sum_{i=1}^{m}(y_i - f_i)^2}{\sum_{i=1}^m(y_i - \bar{y})^2} $$

- $R^2$ ist ein statistisches Mass dafür, wie gut die Vorhersagen den realen Datenpunkten entsprechen
- $R^2 = 1$ bedeutet, dass die Vorhersagen perfekt zu den Daten passen
- $R^2 = 0.53$ bedeutet, dass 53% der Varianz in den Daten durch das Modell erklärt werden
- $R^2 < 0$ können auftreten, wenn das Modell zu den Daten schlechter passt als eine horizontale Hyperebene

## Standardisierung oder Neuskalierung von Variablen

- Wenn die unabhängigen Variablen von sehr unterschiedlicher Grösse und Streuung sind, muss man diese standarisieren
- Standardisierte Variable hat einen Mittelwert von 0 und eine Standardabweichung von 1

1. Berechnen des Stichprobenmittelwerts und der Stichprobenabweichung

$$
\begin{aligned}
    \hat{\mu}_x &= \bar{x} = \frac{1}{n} \sum_{i=1}^n x^{(i)} \\
    \hat{\sigma}_x &= s_x = \sqrt{\frac{1}{n - 1} \sum_{i=1}^n (x^{(i)} - \hat{\mu}_x)^2}
\end{aligned}
$$

2. Anschliessend die standardisierte (normierte) Variable

$$ \tilde{x}^{(i)} = \frac{1}{s_x} (x^{(i)} - \bar{x}) $$

## Vor- und Nachteile von Decision Trees

### Vorteile

- Entscheidungsbäume sind einfach zu verstehen und interpretieren
    -   Dient dem Menschen. Vertraut eher Ansätzen die er versteht.
- Entscheidungsbäume können nummerische sowie kategorische Probleme lösen
    -   Egal ob Features oder Labels
- Entscheidungsbäume brauchen kaum Data Preperation
- Entscheidungsbäume haben auch bei grossen Datensets eine akzeptable Performanz

### Nachteile

- Entscheidungsbäume sind meistens Ungenauer als andere Ansätze
- Meistens werden zu komplexe Bäume, welche nicht genug genralisieren aufgebaut
    - Pruning ist sehr zentral beim trainieren eines Entscheidungsbaum
- Kleine Änderungen im Datenset können zu grossen Änderungen im Entscheidungsbaum führen.
    - Sehr sensitiv auf Data quality

## Möglichkeiten um das Data Set zu debuggen

- Mehr oder "bessere" Trainingsdaten
- kleineres Set an Features
- grösseres Set an Features
- komplett differente Features
- anpassen der Learning Rate
- mehr Iterationen für das Gradienten Abstiegsverfahren
- Differente Optimierungsalgorithmen ausprobieren
- Differente Hyperparameter
- Differente Machine Learning Algorithmen

## Bias und Varianz

Falls das Datenset verschiedene Fehlerquellen hat ist es schwierig diese zu isolieren. Die Learning Algorithmen werden durch solche Fehler Probleme haben, auch neben dem Trainings Set zu generalisieren.

- **Bias**: Der Bias gibt den Wert für Falsche Annehmen eines Learning Algortihmus an. Ein hoher Bias führt dazu, dass der Algorithmus die eigentlichen relevanten Strukturen der Daten zwischen Features und Output nicht finden kann.

- **Varianz**: Die Varianz gibt den Einfluss von kleinsten Änderungen im Datenset an. Bei einer höheren Varianz gewichtet der Learning Algorithmus eher die zufälligen, kleinen Unterschiede als die eigentlichen Features und den Output.

Aufgrund von Bias und Varianz kann bestummen werden ob ein Model Underfitted oder aber Overfitted. Folgende Koorelation zwischen Model, Bias und Varainz bestehen.

- **hoher Bias** und **tiefe Varianz** führen zu **Underfitting** des Models. Die Modele sind zwar Konsistent jedoch Ungenau auf den Durchschnitt.
- **tiefer Bias** und **hohe Varianz** führen zu **Overfitting** des Models. Die Modele sind zwar genau auf den Durchschnitt, jedoch inkonsistent.

## Underfitting und Overfitting

- **Underfitting**: Das Model findet keine geeignete Lösung für das Problem. Das Model bietet schlechte Resultate auf dem Trainings-, Test- sowie auf dem Evaluationset. Es wird eine zuwenig komplexe Lösung gefunden.

- Grösseres Set an Features
- Differentes Set an Features
- Komplexere Machine Learning Algorithmen

- **Overfitting**: Das Model findet eines zu optimierte Lösung für das Trainingset. Dies führt dazu, dass auf dem Trainingsset eine sehr hohe Genauigkeit erreicht wird. Auf dem Test- sowie vorallem auf dem Evaluationsset schlecht performen wird. Das Model optimiert die Lösung zu stark an die Trainingsdaten.

- Mehr Trainingsdaten
- Besseres Data Cleaning (z.B. Outliners eliminieren)
- Kleineres Set an Features
- Early Stopping
- Anpassen der Regularizierungs Parameter
- Ausprobieren von zusammengesetzten Machine Learning Methoden

## Machine Learning Projekt Lösungsansatz

Von M. Pouly wird vorgeschlagen folgendermassen für Machine Learning Projekte vorzugehen.

1. Data Quality Assessment ist seine Zeit IMMER Wert
2. Daten visualisieren
3. Quality Assessment Workflow verwenden der gut durchdacht und spezifiert ist
4. Ausprobieren mit einfachen ML Ansätzen. Wie das schnelle erstellen eines einfachen Classifier oder Regressor
5. Fehlerquellen-Analyse und Diagnostik anwenden
6. Iterative das Model verbessern. Auch durch eventuelle kombination von Ansätzen

- weniger Feature sind weniger Daten. Daher kürzere Trainingszeiten
- Weniger Feature führen zu einfacheren und besser interpretierbaren Models
- Weniger Feature kann der Generalisierung dienen und verringert so eventuell Overfitting

Folgende Techniken können für die Feature Selection genutzt werden.

- Korrelations Analyse, **Gute Features korrelieren stark mit dem Label, jedoch nicht untereinandner.**
- Decisions Tree

