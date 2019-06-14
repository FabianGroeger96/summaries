# Introduction

## Definition Machine Learning

- "Field of study that gives computer the ability to learn without being explicitly programmed."

- "A computer program is said to learn from experience $E$ with respect to some task $T$ and some performance measure $P$, if its performance on $T$, as measured by $P$, improves with experience $E$."

- Diese beiden Definitionen beschreiben das Ziel von Machine Learning, die Strategien um dieses Ziel zu erreichen unterteilt ML in verschiedene Disziplinen.

## Machine Learning Disziplinen

- **Supervised Learning**
  - Algorithmus bekommt gelabelte Trainingsdaten
  - Algorithmus lernt das Label vorherzusagen von ungesehenen Daten
  - Beispiele:
    - Calculating product recommendations with collaborative filtering techniques
    - Medical image analysis for detection of skin diseases based on human expert markings
    - Prediction of selling prices for the real estate market
    - Detecting animals on high-resolution photographs
- **Unsupervised Learning**
  - Algorithmus bekommt ungelabelte Daten
  - Algorithmus erkennt und nützt die grundlegende Struktur der Daten
  - Beispiele:
    - Identifying target groups for marketing campaigns using clustering techniques
    - Market basket analysis using association rules
    - Search query analysis for e-commerce by semantical clustering
    - Dimensionality reduction for data visualization
    - Identifying most-valuable customers on e-commerce platforms using transactions and tracking data
- **Semi-Supervised Learning**
  - Mix aus Supervised und Unsupervised Learning
  - Wird meist gebraucht wenn es nur sehr wenig gelabelte Daten gibt
- **Reinforcement Learning**
  - Keine Daten verfügbar aber der Algorithmus wird durch eine Reward Funktion gelenkt
  - Sucht das optimale Verhalten, welches die Reward Funktion maximiert
  - Beispiel:
    - Learning to play Jass by self-play

## Supervised Learning

### Regression

- Beispiel: Lernen die Autopreise vorherzusagen von **gelabelten** Trainingsdaten.
- Das Attribut welches vorhergesagt werden muss, ist kontinuierlich -> **Regression Problem**

### Classification

- Beispiel 1: Lernen Shoppingverhalten vorherzusagen aufgrund von **gelabelten** Trainingsdaten.
- Das Attribut welches vorhergesagt werden muss, ist kategorisch (binär) -> **Classification Problem**

- Beispiel 2: Lernen gesunde und ungesunde Haut (Ekzeme) zu unterscheiden aufgrund von **gelabelten** Trainingsdaten.
- Das Attribut welches vorhergesagt werden muss, ist kategorisch -> **Classification Problem**

### Recommender Systems

### Angewendet auf Bilder

- einzelnes Objekt
  - Classification (Katze auf Bild oder nicht?)
  - Classification + Localization (Katze auf Bild oder nicht? Wenn ja, wo im Bild?)
- mehrere Objekte
  - Object Detection (Objekte im Bild? Wenn ja, wo im Bild?)
  - Instance Segmentation (Objekte im Bild? Wenn ja, was gehört alles zum Objekt?)

## Unsupervised Learning

### Clustering

- Beispiel: Finde die ideale Anzahl an Zielgruppen in einer Kundendatenbank
- **keine gelabelten** Trainingsdaten vorhanden -> **Clustering Problem**

### Dimensionality Reduction

### Clustering & Natural Language Processing (NLP)

- Beispiel: Gruppiere semantisch ähnliche Suchanfragen
- **keine gelabelten** Trainingsdaten vorhanden -> **Clustering Problem**

## Datenklassifizierung

$$ \includegraphics[width=0.7\columnwidth]{images/datenklassifizierung.png} $$

## Bewertung der Datenqualität

Schlechte Datenqualität kann verschiedene Gründe haben:

- Schlecht gestaltete, unzulängliche oder inkonsistente Datenformate
- Programmierfehler oder technische Probleme (z.B. Sensorausfall)
- Datenverluste (z.B. veraltete E-Mail-Adressen)
- schlecht gestaltete Erhebungsbögen (z.B. Datenfelder ohne Überprüfung)
- Menschliche Fehler beim Datenexport oder bei der Datenvorverarbeitung
- Absichtliche Fehler und falsche Informationen (z.B. Datenschutzbedenken)

Die Überprüfung der Datenqualität kommt immer als erstes!

## Bereinigung der Daten

Daten können verbessert werden, durch bereinigung der Daten:

- doppelte Datensätze können identifiziert und entfernt werden
- entfernen von redundanten Features (welche eine Korrelation von 1 haben), haben keinen neuen Informationsgehalt
- Nullwerte können ersetzt werden
- Datenformate maschinenlesbar machen
- Datum in separate Features aufteilen (Jahr, Monat, Tag)
- Ändern des feature Typs von String zu kategorisch

Auch wenn die Datenqualität manuell verbessert wird, nie vergessen:

- alle Änderungen an den Originaldaten zu dokumentieren
- ein Daten-Repository mit Versionierung zu verwenden
- den Datenanbieter über Probleme mit der Datenqualität zu informieren
- die Ursachen von Problemen mit der Datenqualität zu untersuchen

## Ansätze zur Datenqualitätsbewertung

- Datenquellen und deren Vertrauenswürdigkeit identifizieren
- Statistische Kennzahlen interpretieren
- Ausgewählte Datenteile visualisieren (z.B. Paarplots)
- Datenbereiche manuell überprüfen (z.B. negative Gehälter oder Personen älter 200 Jahre)
- Plausibilisierung von Attributkorrelationen (z.B. Korrelation zwischen Laufleistung und Sitzplätzen)
- Redundanz der Messdaten (Principal Component Analysis)
- Überprüfung auf Anomalien in Syntax und Semantik
- Erkundung von NULL-Werten und doppelten Datensätzen

## Statistische Kennzahlen

### Zentrale Tendenz

- Mittelwert (mean): Durchschnitt einer Reihe von numerischen Beobachtungen
- Modus (mode): Wert der am häufigsten vorkommt
- Median (median): mittlerer Wert einer sortierten Reihe von numerischen Beobachtungen

Der Mittelwert, Modus und Median geben wertvolle Informationen über die Neigung der Daten.

$$ \includegraphics[width=0.7\columnwidth]{images/datenneigung.png} $$

- links-geneigte Daten: $Mittelwert - Modus < 0$
- rechts-geneigte Daten: $Mittelwert - Modus > 0$

### Quartile & Interquartile Range (IQR)

$$ \includegraphics[width=0.5 \columnwidth]{images/quartile.png} $$

### 5 Kennzahlen um eine Datenverteilung zusammenzufassen

- Median Q2
- Quartile Q1 & Q3
- Kleinster und grösster Wert

`pandas_df.describe()`

### Boxplots

$$ \includegraphics[width=0.2\columnwidth]{images/boxplots.png} $$

- Werte welche mindestens 1.5 * IQR oberhalb des dritten Quartils oder unterhalb des ersten Quartils sind gelten als Ausreisser

`plt.boxplot(x=..., labels=...)`

### Pairplots

$$ \includegraphics[width=0.5\columnwidth]{images/pairplots.png} $$

`sns.pairplot()`

### Messen der Datenverteilung

- **Stichprobenvarianz** einer Reihe von numerischen Beobachtungen misst, wie viel die Werte im Durchschnitt verteilt sind, berechnet als die Summe der quadrierten Abweichungen vom Mittelwert

$$
\begin{aligned}
    Var(X) = \frac{1}{n - 1} \sum_{i=1}^n (x_i - \mu_X)^2
\end{aligned}
$$

- Quadratwurzel der Varianz wird als **Standardabweichung** bezeichnet

$$
\begin{aligned}
    \sigma = \sqrt{Var(X)}
\end{aligned}
$$

### Kovarianz

- Probenkovarianz beschreibt die gemeinsame Variabilität von zwei gleich grossen Verteilungen
- Wenn zwei Datenpunkte beide über oder unter ihrem jeweiligen Mittelwert liegen, wird die Kovarianz positiv, d.h. die Verteilungen zeigen eine ähnliche Tendenz
- Wenn ein Datenpunkt über seinem Mittelwert liegt und der andere unten, ist die Kovarianz negativ, d.h. die Verteilung zeigen gegenläufige Tendenz
- Bei unabhängigen Verteilungen heben positive und negative Werte sich gegenseitig auf, so dass die Kovarianz ungefähr Null wird
- Kovarianz Matrix zeigt die Kovarianzen aller Attribute eines Datasets mit jedem anderen Attribut
- Problem der Kovarianz, dass ihre Skala von den Daten abhängt

$$
\begin{aligned}
    Cov(X, Y) =  \frac{1}{n - 1} \sum_{i=1}^n (x_i - \mu_X)(y_i - \mu_Y)
\end{aligned}
$$

`data.cov()`

### Pearson Korrelation

$$ p(X, Y) = \frac{Conv(X, Y)}{\sigma_X \sigma_Y} $$

- Pearson-Korrelation liegt immer zwischen -1 für eine perfekte Anti-Korrelation
und 1 für perfekte Korrelation
- Durch die Normalisierung der Kovarianz können die Korrelationen der verschiedenen Attribute verglichen werden

`data.corr()`

### Ersetzungsstrategien für NULL-Werte

- Viele Machine Learning Algorithmen können nicht mit Null Werten umgehen
- Ersetzungsstrategie je nach Anwendung wählen:
  - Zeilen mit Null Werten löschen -> wenn genügend Daten vorhanden
  - Fehlende Werte manuell eingeben -> Werte aus anderen Quellen übernehmen
  - Füllen der Werte mit einer globalen Konstante -> z.B. UNKNOWN oder $-\infty$
  - Mass für zentrale Tendenz verwenden -> Mittelwert für symmetrische Daten, Median für schiefe Daten
  - Mass für zentrale Tendenz pro Klasse verwenden -> unterschiedlicher Wert für gesunde / kranke Menschen
  - Wahrscheinlichsten Wert verwenden -> z.B. durch Regression

## Datengeometrie

### Vector Space Model

- Datenset welches nur aus numerischen Daten besteht
- Kategorische Datensets können einfach in numerische umgewandelt werden -> aus jeder möglichen Option der kategorischen Spalte eine neue Spalte erstellen und eine 1 vergeben wenn die Zeile zu dieser Kategorie gehört

### Distanz vs. Ähnlichkeit

- Umso ähnlicher zwei Datenpunkte sind, umso näher sind diese im geometrischen Raum
- Je nach Bedeutung der Daten, muss einen geeigneten Abstand gewählt werden

### Pythagoras

$$ dist(X, Y) = \sqrt{\sum_{i=1}^{n}(x_i - y_i)^2}$$

### Euklidische Distanz (als $L^2$ Norm geschrieben)

$$ \Vert{X - Y}\Vert_2 = \sqrt{\sum_{i=1}^{n}(x_i - y_i)^2} $$

Umso kleiner die Distanz, umso grösser ist die Ähnlichkeit

#### Beispiel

Berechne die Euklidische Distanz von BMW zu Audi. und was sagt die Euklidische Distanz aus?

| Name     | Preis | Meilen | PS  |
| -------- | ----- | ------ | --- |
| Mercedes | 70    | 13     | 394 |
| BMW      | 22    | 18     | 286 |
| Audi     | 183   | 1      | 350 |

$$
\begin{aligned}
    \Vert \text{BMW - Audi} \Vert_2 &=
        \sqrt{(22 - 183)^2 + (18 - 1)^2 + (286 - 350)^2} \\
    &= \underline{\underline{174.086}}
\end{aligned}
$$

Die Euklidische Distanz sagt etwas über die Ähnlichkeit zweier Objekte zueinander aus. Wenn die Distanz sehr gering ist, heist das, das die Objekte sehr ähnlich sind.

### Cosinus Ähnlichkeit

- Betrachtet den Winkel $\theta$ zwischen zwei Vektoren $X$ und $Y$
- im Gegensatz zu der direkten Distanz, welche bei der Euklidischen Ähnlichkeit betrachtet wird

$$
\begin{aligned}
    sim(X, Y) &= \frac{\sum_{i=1}^n x_i y_i}
                {\sqrt{\sum_{i=1}^n x_i^2} \sqrt{\sum_{i=1}^n y_i^2}} \\
    \\
    dist(X, Y) &= 1 - sim(X, Y)
\end{aligned}
$$

#### Beispiel

Berechne die Cosinus Ähnlichkeit zwischen den zwei Datenpunkten $X_1 = (3, 14, 18, 23)$ und $X_2 = (12, 16, 21, 29)$.

$$
\begin{aligned}
    sim(X_1, Y_1) &= \frac{3 * 12 + 14 * 16 + 18 * 21 + 23 * 29}
        {\sqrt{3^2 + 14^2 + 18^2 + 23^2} \sqrt{12^2 + 16^2 + 21^2 + 29^2}} \\
    &= \underline{\underline{0.978261}}
\end{aligned}
$$

### Levenshtein Distanz

Zählen der minimalen Anzahl von Änderungen, die erforderlich sind, um eine Zeichenkette in eine andere umzuwandeln:

- Anzahl +1 beim Löschen eines Zeichens
- Anzahl +1 beim Hinzufügen eines Zeichens
- Anzahl +2 beim Ändern eines Zeichens

### Normalisierung

- Der Prozess, jedes Attribut auf ungefähr die gleiche Skala zu bringen
- Die Skala in jeder Dimension hängt von den Daten ab: der größte Preis in einer Autodatenbank ist 698000 CHF, die größte Anzahl der Türen beträgt nur 6
- Eine Preisabweichung von 15% hat einen viel stärkeren Einfluss auf Ähnlichkeit und Entfernung als eine Abweichung von 15% in der Anzahl der Türen
- Solche starken Einflüsse auf die Attribute verfälschen die Ergebnisse der Algorithmen insbesondere wenn sie auf Distanz oder Ähnlichkeit beruhen
- Strategien:
  - **Min-Max Normalisierung**, transformiert die Daten in einen Intervall [0,1]
  $$ X_{norm} = \frac{X - X_{min}}{X_{max}-X_{min}} $$
  - **Z-Score Normalisierung**, transformiert die Daten so, dass der Mittelwert 0 und die Standardabweichung 1 wird
  $$ z = \frac{x - \mu}{\sigma} $$
- Tipps und Tricks:
  - Die Konstanten in jeder Formel heissen Normalisierungsparameter
  - Normalisierungsparameter immer am Trainingsset bewerten
  - Normalisierungsparameter zur Skalierung zukünftiger Daten beibehalten
  - Min-Max-Normalisierung erfordert, dass Sie den Minimal- und Maximalwert auch für zukünftige Daten schätzen
  - Wenn dies nicht möglich ist, verwenden der Z-Score Normalisierung
