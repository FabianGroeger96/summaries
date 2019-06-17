# Clustering & Association Rules

## K-Mean Algorithm

1. Choose number of clusters
2. Create new random datapoint for each cluster center
3. Start loop
    - Assign each data point to its neares cluster center
    - For each cluster: calcule the mean
    - For each cluster: move center to mean
    - Repeat loop as long at least one center moves

## Konvergenz und Optimalität

- Optimales Clustering minimiert die Gesamtabweichung
- k-Means entspricht daher nur _annähernd_ der optimalen Lösung
- k-Means _konvergieren immer_, aber nicht unbedingt zu einem globalen Minimum, manchmal auch zu einem lokalen Minimum
- In der Praxis wird k-Means mehrfach ausgeführt und das Clustering mit minimaler Abweichung genommen

## Wählen der Anzahl Clusters

- Je mehr Cluster, desto kleiner ist die Gesamtabweichung
- In der Praxis bevorzugt man wenige Cluster, aber auch geringe Abweichung
- Die Ellbogenmethode verwenden, guter Kompromiss
  - Man iteriert über verschiedene Anzahlen von Clusters und berechnet die Gesamtabweichung

## Apriori Algorithmus

- In einer Reihe von Transaktionen alle Regeln mit Support $\geq min_s$ und Confidence $\geq min_c$, wobei $min_s$ und $min_c$ die entsprechenden Support und Confidence Thresholds sind
- Apriori Algorithmus findet association rules in zwei Schritten:
  1. Generieren häufiger Itemsets, welche den Support Threshold erfüllen (z.B. {milk, bread} erfüllt Thresholdminimum vom Support)
  2. Extrahieren der Regeln aus häufigen Itemsets, welche den Confidence Threshold erfüllen (z.B. entweder {milk} $\rightarrow$ {bread} oder {bread} $\rightarrow$ {milk})
- Langsam für grosse Datensets
- Alternativ ein Frequent Pattern Growth (FP-Growth) verwenden, enthält eine spezifische Datenstruktur (FP-Tree)

#### 1. Generieren häufiger Itemsets

- Wenn ein Itemset häufig ist (hoher Supportwert), müssen auch alle Subsets einen hohen Support wert aufweisen
- Wenn ein Itemset nicht häufig ist (tiefer Supportwert), müssen alle Supersets auch nicht häufig sein

#### 2. Generieren der Regeln aus häufigen Itemsets

- Wenn eine Regel den Confidence Threshold nicht erfüllen kann, dann erfüllt auch das Subset den Threshold nicht

## Businessseite

- Wenn eine Regel $X \rightarrow Y$ hohen Support, hohe Confidence und einen Liftwert von > 1 hat, kann man davon profitieren indem man z.B.:
  - $X$ und $Y$ näher im Laden zusammenstellen
  - $X$ und $Y$ zusammenführen (Paket, Angebot)
  - $X$ und $Y$ zusammen mit einem weniger beliebten Item einpacken
  - $X$ oder $Y$ einen Discount geben
  - $X$ Preis erhöhen und $Y$ den Preis verringern
  - $X$ oder $Y$ werben, aber nie zusammen

## Association Rules

- Findet interessante Beziehungen zwischen Attributen in grossen Datensets
- Ist eine Implikation $X \rightarrow Y$, in der $X$ und $Y$ disjunkt sind

## Support

- Support ist der Anteil der Transaktionen, welcher ein spezifisches Itemset enthält

$$ \text{support}({i_1, ..., i_n}) = \frac{\text{\# purchases of }{i_1, ..., i_n}}{\text{\# transactions}} $$

- Support misst **wie oft gewisse Items zusammen gekauft** wurden

### Support einer Association Rule

$$ \text{support}(X \rightarrow Y) = \text{support}(X \cup Y) $$

- Richtungsunabhängig, kann daher die Qualität einer gerichteten Association Rule nicht messen!
- Misst, wie häufig ein Itemset/Assoziation in den Daten vorkommt
- Regeln mit geringem Support können einfach durch Zufall entstehen
- Niedrige Supportregeln können aus geschäftlicher Sicht uninteressant sein
- Eine **gute Association Rule hat ein höhen Support**
  
$$ \text{Support} = \text{Interesse} $$

## Confidence einer Association Rule

$$ \text{confidence}(X \rightarrow Y) = \frac{\text{support}(X \cup Y)}{\text{support}(X)} $$

- Legt fest, wie häufig Elemente in $Y$ in Transaktionen erscheinen, die $X$ enthalten
- Für eine bestimmte Regel $X \rightarrow Y$, je höher die Confidence ist, desto wahrscheinlicher ist es für $Y$, in Transaktionen, die $X$ enthalten, vorhanden zu sein
- Confidence liefert eine **Schätzung der bedingten Wahrscheinlichkeit**
- Confidence misst die **Zuverlässigkeit oder Vertrauenswürdigkeit** einer Association Rule
- Eine **gute Association Rule hat eine hohe Confidence**
  
$$ \text{Confidence} = \text{Vertrauenswürdigkeit} $$

### Lift einer Association Rule

$$ \text{lift}(X \rightarrow Y) = \frac{\text{support}(X \cup Y)}{\text{support}(X) \cdot \text{support}(Y)} $$

- Misst wie oft $X$ und $Y$ zusammen aufgetaucht sind, wenn sie statistisch unabhängig sind
- $\text{Lift} = 1$, $X$ und $Y$ sind statistisch unabhängig
- $\text{Lift} < 1$, $X$ und $Y$ erscheinen seltener zusammen als erwartet, sie sind antikorreliert
- $\text{Lift} > 1$, $X$ und $Y$ erscheinen häufiger zusammen als erwartet, sie sind korreliert
- Je **grösser der Liftwert, desto stärker ist die Assoziation zwischen $X$ und $Y$**

$$ \text{Lift} = \text{Stärke der Assoziation} $$
