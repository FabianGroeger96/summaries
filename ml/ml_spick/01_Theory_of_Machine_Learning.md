# Quiz 01 - Theory Questions for Introduction

## Typische Regressions Modelle

- Linear Regression
- Polynomial Regression
- k-Nearest Neighbor Regression
- Support Vector Regression
- Regression Trees
- Neural Networks

## Typische Klassifikations Modelle

- Logistic Regressions
- Naive Bayes
- k-Nearest Neighbors
- Support Vector Machines
- Desicion Trees
- Neural Networks

## 01 - Machine Learning Disciplines
- Supervised Machine Learning
    - Calculating product recommendation with collaborative filtering techniques
    - Medical image analysis for detection of skin disease based on human expert markings
    - Prediction of selling prices for the real estate market
    - Detecting animals on high-resolution images
- Unsupervised Machine Learning
    - Identifying target groups for marketing campaigns using clustering techniques
    - Market basket analysis using association rules
    - Search query analysis for e-commerce by semantical clustering
    - Dimensionality reduction for data visualization
    - Identifying most-valuable customers on e-commerce platforms using transactions and tracking data
- Reinforcement Machine Learning
    - Learning to play Jass by self-play

## 02 - Numerical vs Categorical Variables

- Numerical $\rightarrow$ Represented by a number with actual value
- Categorical $\rightarrow$ Represented as group, can be number's, but without value-assignment

## 03 - Similarity Vector Space Model

- Vector Space Model -> Datenset welches nur aus numerischen Daten besteht
- Kategorische Datensets können einfach in numerische umgewandelt werden -> aus jeder möglichen Option der kategorischen Spalte eine neue Spalte erstellen und eine 1 vergeben wenn die Zeile zu dieser Kategorie gehört

### Pythagoras Distanz

$$ dist(X, Y) = \sqrt{\sum_{i=1}^{n}(x_i - y_i)^2} $$

### Euklidische Distanz (als $L^2$ Norm geschrieben)

$$ \Vert{X - Y}\Vert_2 = \sqrt{\sum_{i=1}^{n}(x_i - y_i)^2} $$

Umso kleiner die Distanz, umso grösser ist die Ähnlichkeit.

### Cosinus Similarity

$$
\begin{aligned}
    sim(X, Y) &= \frac{\sum_{i=1}^n x_i y_i}
                {\sqrt{\sum_{i=1}^n x_i^2} \sqrt{\sum_{i=1}^n y_i^2}} \\
    \\
    dist(X, Y) &= 1 - sim(X, Y)
\end{aligned}
$$

## 04 - Data Cleaning for small Datasets

## Bereinigung der Daten

Bei kleinen Datensets ist Vorischt bei ersetzten von Werten geboten. Das ersetzen mit Mean-Werten kann zu einem Verzug führen, da der Mean ungenau sein könnte. Auch Anomalien sollten beibehalten werden.

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

## 05 - Boxplots for Outlier Detection

### Zentrale Tendenz

- Mittelwert (mean): Durchschnitt einer Reihe von numerischen Beobachtungen
- Modus (mode): Wert der am häufigsten vorkommt
- Median (median): mittlerer Wert einer sortierten Reihe von numerischen Beobachtungen

Der Mittelwert, Modus und Median geben wertvolle Informationen über die Neigung der Daten.

- links-geneigte Daten: $Mittelwert - Modus < 0$
- rechts-geneigte Daten: $Mittelwert - Modus > 0$
- Median Q2
- Quartile Q1 & Q3
- Kleinster und grösster Wert
- Interquantil Range: $IQR = Q_3 - Q_1$
- Werte welche mindestens 1.5 * IQR oberhalb des dritten Quartils oder unterhalb des ersten Quartils sind gelten als Ausreisser

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

### Pearson Korrelation

$$ p(X, Y) = \frac{Cov(X, Y)}{\sigma_X \sigma_Y} $$

- Pearson-Korrelation liegt immer zwischen -1 für eine perfekte Anti-Korrelation
und 1 für perfekte Korrelation
- Durch die Normalisierung der Kovarianz können die Korrelationen der verschiedenen Attribute verglichen werden

