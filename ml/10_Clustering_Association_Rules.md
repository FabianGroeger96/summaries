# Clustering & Association Rules

## Data Clustering

- Verfahren zur Entdeckung von Ähnlichkeitsstrukturen in grossen Datenbeständen
- Gefundenen Gruppen von ähnlichen Objekten werden als _Cluster_ bezeichnet
- Gruppenzuordnung wird als _Clustering_ bezeichnet
- Ziel _neue_ Gruppen in den Daten zu identifizieren, bei Klassifikation werden nur Daten den bestehenden Gruppen zugeordnet
- uniformiertes Verfahren, nicht angewiesen auf Klassen-Vorwissen
- z.B. für automatisierte Klassifizierung, Erkennung von Mustern in Bildern, Marktsegmentierung oder Zielgruppenanalyse

### k-Means Algorithmus

#### Ablauf

##### 1. Vorbereitung

- Wähle die Anzahl an Clusters (z.B. 3)
- Erstelle zufällig neue Cluster Centers (neue Datenpunkte)

$$ \includegraphics[width=0.7\columnwidth]{images/k_means_clustering_preparation.png} $$

##### 2. Suchen nach dem nächstgelegenen Cluster für jeden Datenpunkt

$$ \includegraphics[width=0.7\columnwidth]{images/k_means_clustering_search_cluster.png} $$

##### 3. Berechnung des Mittelpunktes eines Clusters

- Berechnen des Mittelwerts aller Punkte, welche momentan zu dem selben Cluster angehören
- Verschiebung des Mittelpunktes des Clusters zu dem vorher berechneten Mittelwert aller Punkte

$$ \includegraphics[width=0.7\columnwidth]{images/k_means_clustering_center_cluster.png} $$

##### 4. Berechnung des Mittelpunktes für jedes Cluster

$$ \includegraphics[width=0.7\columnwidth]{images/k_means_clustering_center_all_clusters.png} $$

##### 5. Neustart und Fortfahren bis zur Stabilität der Mittelpunkte

$$ \includegraphics[width=0.7\columnwidth]{images/k_means_clustering_restart_continue.png} $$

#### Pseudo Code

1. Input: number of clusters $k > 0$ and data points $x_1, ..., x_n$
2. Randomly choose $k$ cluster centers $\mu_1, ..., \mu_k$
3. Repeat until convergence
  a. Assign each data point $x_i$ to its nearest cluster center $\mu_j$
  b. Update each cluster center to the mean of all assigned data points

### Clustering Abweichung (Distortion)

- Die Gesamtabweichung (total distortion) kann durch durch Summieren der quadratischen Abstände zwischen jedem Punkt und seinem Clusterzentrum gemessen werden

$$ \sum_{i=1}^n ||x_i - \mu_{ci}||^2 $$

- Die Durchschnittsabweichung (average distortion) jedes Datenpunktes

$$ \frac{1}{n} \sum_{i=1}^n ||x_i - \mu_{ci}||^2 $$

- Die Durchschnittsabweichung ermöglicht den Vergleich von Clusters über verschiedene Datensätze

### Konvergenz und Optimalität

- Optimales Clustering minimiert die Gesamtabweichung
- k-Means entspricht daher nur _annähernd_ der optimalen Lösung
- k-Means _konvergieren immer_, aber nicht unbedingt zu einem globalen Minimum, manchmal auch zu einem lokalen Minimum
- In der Praxis wird k-Means mehrfach ausgeführt und das Clustering mit minimaler Abweichung genommen

### Wählen der Anzahl Clusters

- Je mehr Cluster, desto kleiner ist die Gesamtabweichung
- In der Praxis bevorzugt man wenige Cluster, aber auch geringe Abweichung
- Die Ellbogenmethode verwenden, guter Kompromiss
  - Man iteriert über verschiedene Anzahlen von Clusters und berechnet die Gesamtabweichung

$$ \includegraphics[width=0.7\columnwidth]{images/data_clustering_ellbow_method.png} $$

## Association Rules

- Findet interessante Beziehungen zwischen Attributen in grossen Datensets
- Ist eine Implikation $X \rightarrow Y$, in der $X$ und $Y$ disjunkt sind

### Support eines Satzes von Items

- Support ist der Anteil der Transaktionen, welcher ein spezifisches Itemset enthält

$$ support({i_1, ..., i_n}) = \frac{\text{\# purchases of }{i_1, ..., i_n}}{\text{\# transactions}} $$

- Support misst wie oft gewisse Items zusammen gekauft wurden

$$ \includegraphics[width=0.7\columnwidth]{images/association_rules_support.png} $$

### Support einer Association Rule

$$ support(X \rightarrow Y) = support(X \cup Y) $$

$$ support(X \rightarrow Y) = support(Y \rightarrow X) $$

- Richtungsunabhängig, kann daher die Qualität einer gerichteten Association Rule nicht messen!

$$ \includegraphics[width=0.7\columnwidth]{images/association_rule_support_association_rule.png} $$

### Interpretation des Supports

- Misst, wie häufig ein Itemset in den Daten vorkommt
- Regeln mit geringem Support können einfach durch Zufall entstehen
- Niedrige Supportregeln können aus geschäftlicher Sicht uninteressant sein
- Eine gute Association Rule hat ein höhen Support
  
$$ Support = Interesse $$

### Confidence einer Association Rule

$$ confidence(X \rightarrow Y) = \frac{support(X \cup Y)}{support(X)} $$

$$ \includegraphics[width=0.7\columnwidth]{images/association_rule_confidence.png} $$

### Interpretation der Confidence

- Legt fest, wie häufig Elemente in $Y$ in Transaktionen erscheinen, die $X$ enthalten
- Für eine bestimmte Regel $X \rightarrow Y$, je höher die Confidence ist, desto wahrscheinlicher ist es für $Y$, in Transaktionen, die $X$ enthalten, vorhanden zu sein
- Confidence liefert eine Schätzung der bedingten Wahrscheinlichkeit
- Confidence misst die Zuverlässigkeit oder Vertrauenswürdigkeit einer Association Rule
- Eine gute Association Rule hat eine hohe Confidence
  
$$ Confidence = Vertrauenswürdigkeit $$

### Lift einer Association Rule

$$ lift(X \rightarrow Y) = \frac{support(X \cup Y)}{support(X) * support(Y)} $$

$$ \includegraphics[width=0.7\columnwidth]{images/association_rule_lift.png} $$

### Interpretation des Lifts

- Misst wie oft $X$ und $Y$ zusammen aufgetaucht sind, wenn sie statistisch unabhängig sind
- $Lift = 1$, $X$ und $Y$ sind statistisch unabhängig
- $Lift < 1$, $X$ und $Y$ erscheinen seltener zusammen als erwartet, sie sind antikorreliert
- $Lift > 1$, $X$ und $Y$ erscheinen häufiger zusammen als erwartet, sie sind korreliert
- Je grösser der Liftwert, desto stärker ist die Assoziation zwischen $X$ und $Y$

$$ Lift = \text{Stärke der Assoziation} $$

### Vertrauenswürdige, aber uninteressante Regeln

- Seltene aber korrekte Regeln werden somit nicht richtig berücksichtigt
- Kann nicht nur eine der beiden Massnahmen (Confidence / Support) in betracht ziehen
- z.B. Regeln welche Milch und Bananen beinhalten, können zufällig auftreten, weil Mich und Bananen sehr oft eingekauft werden

### Apriori Algorithmus

- In einer Reihe von Transaktionen alle Regeln mit Support $\geq min_s$ und Confidence $\geq min_c$, wobei $min_s$ und $min_c$ die entsprechenden Support und Confidence Thresholds sind
- Apriori Algorithmus findet association rules in zwei Schritten:
  1. Generieren häufiger Itemsets, welche den Support Threshold erfüllen (z.B. {milk, bread} erfüllt Thresholdminimum vom Support)
  2. Extrahieren der Regeln aus häufigen Itemsets, welche den Confidence Threshold erfüllen (z.B. entweder {milk} $\rightarrow$ {bread} oder {bread} $\rightarrow$ {milk})
- Langsam für grosse Datensets
- Alternativ ein Frequent Pattern Growth (FP-Growth) verwenden, enthält eine spezifische Datenstruktur (FP-Tree)

#### 1. Generieren häufiger Itemsets

- Wenn ein Itemset häufig ist (hoher Supportwert), müssen auch alle Subsets einen hohen Support wert aufweisen
- Wenn ein Itemset nicht häufig ist (tiefer Supportwert), müssen alle Supersets auch nicht häufig sein

$$ \includegraphics[width=0.7\columnwidth]{images/apriori_itemset_generation.png} $$

#### 2. Generieren der Regeln aus häufigen Itemsets

- Wenn eine Regel den Confidence Threshold nicht erfüllen kann, dann erfüllt auch das Subset den Threshold nicht

$$ \includegraphics[width=0.7\columnwidth]{images/apriori_generate_rules.png} $$

### Businessseite

- Wenn eine Regel $X \rightarrow Y$ hohen Support, hohe Confidence und einen Liftwert von > 1 hat, kann man davon profitieren indem man z.B.:
  - $X$ und $Y$ näher im Laden zusammenstellen
  - $X$ und $Y$ zusammenführen (Paket, Angebot)
  - $X$ und $Y$ zusammen mit einem weniger beliebten Item einpacken
  - $X$ oder $Y$ einen Discount geben
  - $X$ Preis erhöhen und $Y$ den Preis verringern
  - $X$ oder $Y$ werben, aber nie zusammen
