# Supervised Learning

## Genauigkeit (Accuracy) und Fehlerquote (Error Rate)

- Genauigkeit misst wie oft der Klassifikator recht hatte
- Fehlerquote misst wie oft der Klassifikator nicht recht hatte

$$
\begin{aligned}
    \text{Accuracy} &= \frac{TP + TN}{\text{Total}} \\
    \\
    \text{Error Rate} &= \frac{FP + FN}{\text{Total}} = 1 - \text{Accuracy}
\end{aligned}
$$

- Genauigkeit nicht für unausgewogene Daten verwenden, sonst hat die Genauigkeit keine Aussagekraft!

## Empfindlichkeit (Sensitivity)

- Wenn der wahre Wert JA ist, wie oft hat das Modell JA vorhergesagt
- Wird auch True-Positive Rate oder Recall genannt

$$ \text{Sensitivity} = \frac{TP}{\text{Actual YES}} = \frac{TP}{TP + FN} $$

## Spezifität (Specificity)

- Wenn der wahre Wert NEIN ist, wie oft hat das Modell NEIN vorhergesagt

$$ \text{Specificity} = \frac{TN}{\text{Actual NO}} = \frac{TN}{TN + FP} $$

## Präzision (Precision)

- Ein Problem mit Genauigkeit und Spezifität ist, dass TN nicht immer gezählt werden kann
  - Beispiel: TN einer Google-Suchanfrage?
- Stattdessen Präzision verwenden, wenn das Modell JA voraussagt, wie oft ist es korrekt?

$$ \text{Precision} = \frac{TP}{\text{Predicted YES}} = \frac{TP}{TP + FP} $$

## F1 Score

- F1 ist das harmonische Mittel zwischen Präzision und Empfindlichkeit
- F1 berücksichtigt keine TN!
- Eigenschaft: F1 ist stark voreingenommen in Richtung der schlechteren Punktzahl
- Bei einem Klassifizierungsproblem mit schiefen Daten verwenden


$$ \text{F1} = \frac{2 \cdot \text{precision} \cdot \text{sensitivity}}{\text{precision} + \text{sensitivity}} $$

- Es existieren zwei Methoden des F1-Score. Durchschnitt F1 über alle K-Fold. Oder F1-Score über alle zusammengesetzen Predictions. Zweiteres liefert eher weniger einen undefinierten F1-Score

## Einfachster Machine Learning Workflow

- Teile das Dataset in Trainings- und Test-Daten
- Trainiere ein Regressor / Klassifikator auf dem Trainingsset
- Evaluiere die Performance des Modells anhand noch nie gesehenen Daten vom Testset
- funktioniert nur mit viel Daten und fixen Hyperparametern

## Cross Validation

- Wenn nicht genügend Daten vorhanden sind um einen Trainings/Validierungs/Test Split zu machen, sollte man eine Cross Validation verwenden
- Teilen der Daten in Trainings- (80%) und Testdaten (20%), die Testdaten werden weggesperrt
- Das Trainingsset wird nun in $k$ verschiedene Blöcke unterteilt, aus denen bei jedem Durchgang einer gewählt wird und als Validierungsset verwendet wird, der Rest wird als Trainingsset verwendet
- Dabei kann auch ein Leave-One-Out cross-validation getätigt werden. Dort ist $k = N$ mit $N = \text{Anzahl der Elemente}$
