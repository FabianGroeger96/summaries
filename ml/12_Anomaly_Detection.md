# Unsupervised Learning: Anomaly or Outlier Detection

## Anomalies & Outliers

- Sind Muster in Daten, die nicht mit einem bestimmten klar definierten Ansatz von normalem Verhalten übereinstimmen

$$ \includegraphics[width=0.4\columnwidth]{images/anomalies_definition.png} $$

## Beispiele

- Anomales TCP-Verkehrsmuster aufgrund eines gehackten Computers, der sensible Daten an ein unbefugtes Ziel sendet
- Anomales MRT-Bild kann auf das Vorhandensein eines bösartigen Tumors hinweisen
- Anomalien bei Kreditkartentransaktionen deuten auf Betrug oder Identitätsdiebstahl hin

## Typen von Anomalien

1. **Globale Ausreisser**: weichen deutlich vom Rest des Datensatzes ab (z.B. Muster einer bösartigen Kreditkartentransaktion)
2. **Kontektuelle Ausreisser**: weichen in Bezug auf einen bestimmten Kontekt erheblich voneinander ab (z.B. Temperatur 25 in der Schweiz, für Mai normal, für Dezember ein Ausreisser)
3. **Kollektive Ausreisser**: weichen als Gruppe vom gesamten Datensatz ab, aber nicht unbedingt als Individuen (z.B. ein Manager betrachtet einen verzögerten Auftrag nicht als Ausreisser, jedoch 100 verzögerte Ausreisser am selben Tag sind aussergewöhnlich)

## Outlier Erkennung mit Machine Learning

- Supervised Learning: Outlier Erkennung kann als Klassifikationsproblem angeschaut werden (normal vs. outlier)
  - Wenn Anomalien selten sind, genügend Daten davon zu sammeln kann ein Problem sein
  - Es müssen besondere Massnahmen ergriffen werden weil die beiden Klassen extrem unausgewogen sind
- Unsupervised Learning: Geht davon aus, dass Ausreisser vom Strukturmuster normaler Datenobjekte abweichen, wir unterscheiden:
  - Statistische Methoden
  - Proximity-Based Methoden
  - Clustering Methoden

### Classification-Based Methode

- Trainiere einen Klassifikator (z.B. eine Support Vector Machine) um zwischen normalen Daten und Ausreissern zu unterscheiden
- Generiere eine Decision Boundary um die normalen Daten
- Punkte ausserhalb der Decision Boundary sind Ausreisser

### Statistische Methoden

- Gehen davon aus, dass normale Datenobjekte durch ein stochastisches Modell erzeugt werden und dass Daten, die diesem Modell nicht folgen, Ausreisser sind
- z.B. **24.0**, 28.9, 28.9, 29.0, 29.1, 29.1, 29.2, 29.2, 29.3, 29.4

### Proximity-Based Methoden

- Punkte, die weit entfernt von anderen sind, gelten als Ausreisser
- Zwei Typen von Proximity-Based Methoden
  - Entfernungsabhängige Methode in Bezug auf das globale Dataset
  - Dichteabhängige Methode in Bezug auf die lokale Nachbarschaft

$$ \includegraphics[width=0.7\columnwidth]{images/anomaly_detection_proximity_based.png} $$

#### Local Outlier Factor (LOF)

- Wert der aussagt, wie wahrscheinlich ein gewisser Punkt ein Ausreisser ist
- Local reachability density eines Punktes im Vergleich zu seinen k Nachbarn
- $LOF(x) \approx 1$, normal
- $LOF(x) > 1$, outlier
- $LOF(x) < 1$, inlier

$$ \includegraphics[width=0.7\columnwidth]{images/local_outlier_factor.png} $$

#### K-Distance

- Distanz von einem Punkt zu seinem k-ten Nachbarn

#### Reachability Distance

- Maximum aus der Entfernung von zwei Punkten und der k-Distanz des zweiten Punktes
- Glättungsbegriff, d.h. eine niedrige Entfernungsgrenze, die von der Nachbarschaftsdichte abhängt

#### Local Reachability Density (lrd)

- Berechnen der reachability distance von $a$ zu all seinen k-nächsten Nachbarn und berechnen des Mittelwerts
- Transformieren des Abstands in Dichte, indem man die umgekehrte Richtung nimmt
- Intuitiv sagt die local reachability density aus, wie weit man reisen muss, um den nächsten Punkt oder Gruppe von Punkten zu erreichen
- Je niedriger die local reachability density eines Punktes, desto weniger dicht ist seine Region, desto länger muss man reisen

## Clustering-Based Methoden

- Clustering-Based Methoden erkennen Ausreisser indem die Beziehung zwischen dem Punkt und dem Cluster untersucht wird
- Drei generelle Ansätze:
  - Punkte die nicht zu einem Cluster gehören sind Ausreisser
  - Punkte mit grossen Distanzen zu ihrem nächsten Clusterzentrum sind Ausreisser
  - Alle Punkte in einem kleinen und spärlichen Cluster sind Ausreisser
