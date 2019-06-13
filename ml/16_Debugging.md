# Debugging von Supervised Learning

## Motivation

- Debugging muss betrieben werden, falls eine Machine Learning nicht die gewünschte oder erwartete Genauigkeit liefert.
- Dies beschränkt sich nicht zwingend nur auf die Genauigkeit, es kann auch ein Error-Wert ausschlaggebend für ein Debugging sein

### Möglichkeiten um das Data Set zu debuggen

- Mehr oder "bessere" Trainingsdaten
- kleineres Set an Features
- grösseres Set an Features
- komplett differente Features
- anpassen der Learning Rate
- mehr Iterationen für das Gradienten Abstiegsverfahren
- Differente Optimierungsalgorithmen ausprobieren
- Differente Hyperparameter
- Differente Machine Learning Algorithmen

Wichtig dabei ist es nicht zufällige Veränderugnen durchzuführen. Änderungen sollten durch fundierte Analyse begründet werden können.

## Bias und Varianz

Falls das Datenset verschiedene Fehlerquellen hat ist es schwierig diese zu isolieren. Die Learning Algorithmen werden durch solche Fehler Probleme haben, auch neben dem Trainings Set zu generalisieren.

- **Bias**: Der Bias gibt den Wert für Falsche Annehmen eines Learning Algortihmus an. Ein hoher Bias führt dazu, dass der Algorithmus die eigentlichen relevanten Strukturen der Daten zwischen Features und Output nicht finden kann.

- **Varianz**: Die Varianz gibt den Einfluss von kleinsten Änderungen im Datenset an. Bei einer höheren Varianz gewichtet der Learning Algorithmus eher die zufälligen, kleinen Unterschiede als die eigentlichen Features und den Output.

Aufgrund von Bias und Varianz kann bestummen werden ob ein Model Underfitted oder aber Overfitted. Folgende Koorelation zwischen Model, Bias und Varainz bestehen.

- **hoher Bias** und **tiefe Varianz** führen zu **Underfitting** des Models. Die Modele sind zwar Konsistent jedoch Ungenau auf den Durchschnitt.
- **tiefer Bias** und **hohe Varianz** führen zu **Overfitting** des Models. Die Modele sind zwar genau auf den Durchschnitt, jedoch inkonsistent.

## Underfitting und Overfitting

- **Underfitting**: Das Model findet keine geeignete Lösung für das Problem. Das Model bietet schlechte Resultate auf dem Trainings-, Test- sowie auf dem Evaluationset. Es wird eine zuwenig komplexe Lösung gefunden.

- **Overfitting**: Das Model findet eines zu optimierte Lösung für das Trainingset. Dies führt dazu, dass auf dem Trainingsset eine sehr hohe Genauigkeit erreicht wird. Auf dem Test- sowie vorallem auf dem Evaluationsset schlecht performen wird. Das Model optimiert die Lösung zu stark an die Trainingsdaten.

$$ \includegraphics[width=0.7\columnwidth]{images/under_overfitting.png} $$

### Underfitting

Untenstehend ein Bild das die Learning Curve eines Models, welches Underfitted, zeigt. Man sieht die Error-Kurven schmiegen sich gegenseitig an. Die gewünschte Performance ist nur früh im Training-Set ersichtlich. Anschliessend konvergieren beide Kurven zu einem zu hohen Error.

$$ \includegraphics[width=0.5\columnwidth]{images/learningcurve_underfitting.png} $$

#### Gegenmassnahmen für Underfitting

Modele mit Underfitting sind grundsätzlich einfacher zu verbessern. Die relevanten (Daten)-Strukturen sind in sich zu wenig komplex. Daher könnten folgende Massnahmen abhilfe schaffen.

- Grösseres Set an Features
- Differentes Set an Features
- Komplexere Machine Learning Algorithmen

### Overfitting

Beim Overfitting kann eine Lernkurve eines Model wie folgt aussehen. Die Performenz auf den Trainingsdaten ist sehr gut (klassisches Overfitting Phänomen) der Validation Error ist jedoch nicht an der gewünschten Performenz. Die Error-Kurven flachen ab. Und werden sich nicht an die Gewünschte Performenz annähern.

$$ \includegraphics[width=0.5\columnwidth]{images/learningcurve_overfitting.png} $$

#### Gegenmassnahmen für Overfitting

Overfitting tritt im Vergleich zu Underfitting weit öfter auf. Auch ist der Aufwand Overfitting zu verhindern weitgrössser als gegenüber Underfitting. Ein Model was Overfitted ist zu sehr auf die Trainingsdaten eingestellt. Mögliche Massnahmen dies zu verhindern.

- Mehr Trainingsdaten
- Besseres Data Cleaning (z.B. Outliners eliminieren)
- Kleineres Set an Features
- Early Stopping
- Anpassen der Regularizierungs Parameter
- Ausprobieren von zusammengesetzten Machine Learning Methoden

## Early Stopping

Beim Early Stopping wird das Training des Models an einem Punkt gestoppt, an dem das Overfitting für das Model noch nicht eingetreten ist. Dabei kann man für ein Model, welches Overfitten würde, doch noch ein brauchbares Resultat ziehen. Bedeutet jedoch nicht, dass mit dem Early Stopping ein Top-Resultat bietet. Early Stopping hat vorallemn Relevanz und Wichtigkeit im Bereich von Deep Learning.

$$ \includegraphics[width=0.5\columnwidth]{images/earlystopping.png} $$

## Machine Learning Projekt Lösungsansatz

Von M. Pouly wird vorgeschlagen folgendermassen für Machine Learning Projekte vorzugehen.

1. Data Quality Assessment ist seine Zeit IMMER Wert
2. Daten visualisieren
3. Quality Assessment Workflow verwenden der gut durchdacht und spezifiert ist
4. Ausprobieren mit einfachen ML Ansätzen. Wie das schnelle erstellen eines einfachen Classifier oder Regressor
5. Fehlerquellen-Analyse und Diagnostik anwenden
6. Iterative das Model verbessern. Auch durch eventuelle kombination von Ansätzen

## Fluch der Dimensionalität

"As the number of features or dimensions grows, the amount of data we need to generalize accurately grows exponentially."

- In the 1-D case, each data point represents a neighborhood of area 1/10
- In the 2-D case, we need 100 data points for a similar coverage
- In the 3-D case, we need 1000 data points

Dafür gibt es folgende Ursachen,

- Die meisten statistischen Lernalgorithmen benötigen Zählfunktionen. z.B. bei einem Decision Tree und der Verwendung von Majority Voting
- Um bei wachsender Dimension (Features) die selbe Abdeckung zu erhalten, mehr Daten sind nötig. Wird dies nicht geführt verringert sich die Dichte der Daten. Sprich für ein zusätzliches Feature gibt es zu wenig "gültige" Koorelation zum Datensatz.

Daraus folgt,

- Das hinzufügen von mehr Daten ist nicht immer die Lösung oder Konstruktiv
- Wichtig ist das redundante und unwichtige Features entfernt werden!

Unter der Annahme das folgende Feature für einen Datensatz vorliegen.

1. Anzahl Unfälle
2. Anzahl Wasserrohrbrüche
3. Anzahl geschlossener Schulen
4. Anzahl Patienten mit einem Hitzeschlag
5. Ausgaben für die Schneeräumung in CHF

- Der Datensatz beruht hier auf fünf Features. Der eigentliche grosse Koorelations Faktor ist jedoch der Temperaturwert (Hidden Variable).
- Alle fünf Features korrelieren stark mit der Temperatur. Covarianz zeigt hier Redundanz.

Um dies zu lösen kann Principal Component Analysis (PCA) genutzt werden. Dadurch wird ein reduziertes Datenset erstellt.

## Feature Selection

Für das selektieren sollte an Datensetz erstellt werden welcher möglichst nur relevante Features für das Problem des Model beinhaltet. Dabei soll folgendes beachtet werden.

- **Redundante** Features vermeiden
- **Irrelevante** Features vermeiden
- PCA kann genutzt werden um neue Features aus dem Datensatz zu erstellen. So können andere Features reduziert werden.

Gutes Features Selection bekämpft auch den "Fluch der Dimensionalität". Weiter hilft es jedoch verbessertes auch im allgemeinen die Effizienz von Machine Learning.

- weniger Feature sind weniger Daten. Daher kürzere Trainingszeiten
- Weniger Feature führen zu einfacheren und besser interpretierbaren Models
- Weniger Feature kann der Generalisierung dienen und verringert so eventuell Overfitting

Folgende Techniken können für die Feature Selection genutzt werden.

- Korrelations Analyse, **Gute Features korrelieren stark mit dem Label, jedoch nicht untereinandner.**
- Decisions Tree
