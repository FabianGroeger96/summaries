# Dimensionality Reduction

Bei der Dimensionality Reduction geht es darum den Datensatz oder auch deren Features zu verkleinern. So wird die grösse (dimensionalität) des Sets reduziert.

## Data Redundancy

Datenredundanz machen den Datensatz unnötig gross ohne mehr Information zu enthalten. Dabei können teilweise Features entfernt werden, ohne an Informationsgehalt zu verlieren.

- Ein Feature welches immer den selber Wert annimmt, hat Null-Varianz. Somit enthält es keinerlei Information und kann entfernt werden.
- Dabei können auch gleichsagende Features auftauchen (z.B. Fläche in Qudratmeter und Fläche in Qudratcentimeter). Sogenannte Komplett Redundante Features haben eine maximale Kovarianz.
- Falls zwei Features eine Kovarianz über Null besitzen, können sie teilweise redundant sein.
- Idealerweise wird zuerst eine Projektion durchgeführt. Diese kann Kovarianz von Features erhöhen ohne möglicherweise wertvolle Information zu verwerfen.

Dabei können Strategien zur reduktion der Dimensionalität angewandt werden. Zwei behandelte Strategien sind,

- Redundanz eliminieren ohne Informationsverlust
    - Bei komplett Redundanten Features
    - Kombination von Features um die Kovarianz zu verringern/entfernen
- Möglichst wenig Information durch entfernen von Features zerstören
    - Inofrmationsverlust während der Projektion möglichst klein halten. Sprich möglichst kleiner Error oder aber möglichst grosse Varianz der Projektion.

## Projektion zu Basisvektoren und Rotation

Hier wird ein Beispiel für die Projektion eine 2D-Datensatz aufgezeigt. Folgender Datensatz sei in 2D so aufgebaut.

$$ \includegraphics[width=0.3\columnwidth]{images/2d_projection.png} $$

Dieser Datensatz soll jetzt in 1D abgebildet werden und dabei möglichst wenig Informationsgehalt zuverlieren.

### Einfache Projektion zu einem Basis Vektor

Der Datensatz kann auf die Basis der beiden Achsen projeziert werden. Dies würde einer Verteilung der Datenpunkt aus Sicht von Area/Price entsprechen.

$$ \includegraphics[width=0.7\columnwidth]{images/projection_basevectors.png} $$

### Projektion anhand von Transformation

Eine Projektion die den Informationsgehalt weiter konserviert ist die Transformation. Dabei wird ein Punkt des 2D-Plot mit über eine Achse gelegt. Dabei werden die zwei neue Achsen definiert, welche sich über die Winkel der Rotation und den ursprünglichen X/Y-Werten berrechnet wird.

$$ \includegraphics[width=0.5\columnwidth]{images/projection_rotation.png} $$

$$
\begin{aligned}
    x^{\prime} = x \cdot cos \theta + y \cdot sin \theta \\
    y^{\prime} = - x \cdot cos \theta + y \cdot sin \theta
\end{aligned}
$$

Anschliessend kann wieder die Verteilung der Basis Vektoren durchgeführt werden. Diese liegen nun auf der schneideten Achse.

$$ \includegraphics[width=0.5\columnwidth]{images/projection_rotation_base.png} $$

Wenn nun die drei Variationen visualisiert werden. Ergeben sich folgende 1D-Representationen.

$$ \includegraphics[width=0.7\columnwidth]{images/projection_comparsion.png} $$

Dabei wird ersichtlich die Projektion über die Transformation beinhaltet weiter die Werte beider Dimensionen, Area und Price.

### Messen von Informationsgehalt

Dabei stellt sich die Frage wie diese drei Projektionen verglichen werden können. Dies geschieht über den Fehler welcher entsteht von der 1D-Projektion zum Wert in 2D. Dabei gilt,

- Umso kleiner der Fehler umso grösser die Varianz. Sprich umsomehr Informationsgehalt liegt in der Projektion.
- Der behalten Gehalt von Informationen zeigt sich über die Varianz der Projektion.
- So ist die beste Projektion, die Projektion welche den Informationsgehalt am wenigsten verringert. Sprich den kleinsten Error oder aber die grösste Varainz aufweist.

## Base Transformation an Daten Matrizen

- $m$ ist die Anzahl Features. $n$ die Anzahl Datensätze.
- $X$ and $Y$ sind $m \times n$ Matritzen.
- $P$ ist eine $m \times m$ Quadratmatrix.

Dabei kann eine Basis Transformation an Matrizen mit folgender Formel durchgeführt werden.

$$ P \times X = Y $$

- Geometrisch gesehen ist $P$ eine Rotation und Verzerrung von $X$ nach $Y$. Auch ausgedrückt als, $P$ führt eine Basis Transformation auf $X$ aus.
- Die Spalten der Matrix $P$ sind die Basis Vektoren von $Y$. Auch genannt **Principal Components**.

## Principal Component Analysis

### Anwendungsbereich

- Kompression
  - Reduzieren des Speichers, um Daten zu speichern
  - Schnelleres trainieren eines Learning Algorithmus
- Visualisation
- **Nie verwenden um overfitting zu vermeiden!**

### Ziel

- Einen "lower dimensional Surface/Vektoren" (z.B. Fläche/Linie) finden, welcher den Projektionsfehler minimiert
- Dieser Vektor kann negativ oder positiv sein, spielt keine Rolle in welche richtung dieser zeigt

### Recap Varianz und Kovarianz

- Die Varianz eines einzelnen Feature $X$ mit dem Mittelwert Null.

$$ Var(X) = \frac{1}{n-1}\sum_{i=1}^n x_i \cdot x_i $$

- Die Covarainz zweier Feature $X$ und $Y$ mit Mittelwert Null ergibt sich aus.

$$ Cov(X, Y) = \frac{1}{n-1}\sum_{i=1}^n x_i \cdot y_i $$

- Daraus folgt das die Kovarianz-Matrix $\mathbf{S_Y}$ einer Matrix $\mathbf{Y}$ sich ergibt aus.

$$ \mathbf{S_Y} = \frac{1}{n-1}\mathbf{Y}\mathbf{Y^T} $$

- Dabei sind die diagonalen Terme Varianz, und nicht-Diagonale Terme Kovarianz.

$$
\mathbf{S_Y} = \begin{bmatrix}
    Var(Y) && Cov(Y,Y^T) \\
    Cov(Y^T,Y) && Var(Y^T)
    \end{bmatrix}
$$

#### Beispiel

$Y$ ist eine 11 dimensionale Feature Matrix und wurde bereits Mittelwert-Standartisiert.

$$
    YY^T = \begin{bmatrix}
        250 & 20 \\
        20 & 40
    \end{bmatrix}
$$

Berechne die Pearson Korrelation zwischen Feature 1 & Feature 2 von $Y$

1. Berechnen von $S_Y$

$$
\begin{aligned}
    S_Y &= \frac{1}{n-1}YY^T \\
    &= \frac{1}{10}\begin{bmatrix}
        250 & 20 \\
        20 & 40
    \end{bmatrix}
    &= \begin{bmatrix}
        25 & 2 \\
        2 & 4
    \end{bmatrix}
\end{aligned}
$$

2. Berechnen der $Conv(Y, Y^T)$

- Ist gegeben durch die Kovarianz-Matrix $S_Y$

$$ Conv(Y, Y^T) = 2 $$

3. Berechnen der Standardabweichung von $Y$ und $Y^T$

- Durch die Kovarianz-Matrix $S_Y$ wissen wir, wie gross die Varianz von $Y$ und $Y^T$ ist

$$
\begin{aligned}
    \sigma(Y) &= \sqrt{Var(Y)} = \sqrt{25} = 5 \\
    \sigma(Y^T) &= \sqrt{Var(Y^T)} = \sqrt{4} = 2
\end{aligned}
$$

4. Berechnen der Pearson Korrelation $p(Y, Y^T)$

$$ p(Y, Y^T) = \frac{2}{5 \cdot 2} = \frac{2}{10} = \underline{\underline{0.2}}$$

### Vorgehen Principal Component Analysis

1. Off-diagonale Terme von $\mathbf{S_y}$ zeigen die Kovarianz. Diese Terme sollten Null-Wert ergeben.
2. Diagonale Terme von $\mathbf{S_y}$ zeigen die Varianz in der eigenen Dimension. Diese Terme können genutzt werden um Features mit geringer Varianz zu ermitteln.

Betrachten wir nocheinmal das Schema der Principal Component Analysis.
Sei $\mathbf{X}$ eine Mittelwert-Normalisierte Matritze. Wir suchen für diese eine Matrize $\mathbf{P}$. Vor dem Anwenden von PCA müssen die Features immer einen Mittelwert von 0 haben.

$$\mathbf{PX = Y}\qquad \text{und} \qquad \mathbf{S_y} = \frac{1}{n-1}\mathbf{Y}\mathbf{Y^T}$$

So ist $\mathbf{S_y}$ eine Diagonal Matrix. Die Spalten von $\mathbf{P}$ die Principal Components von $\mathbf{X}$.

Die Principal Component Analysis kann so auch ohne $\mathbf{S_y}$ und $\mathbf{Y}$ geschrieben werden. Da $\mathbf{Y} = \mathbf{PX}$.

$$ \mathbf{S_y} = \frac{1}{n-1}\mathbf{YY^T} = \frac{1}{n-1}\mathbf{(PX)}\mathbf{(PX)^T} = \frac{1}{n-1}\mathbf{PXX^TP^T} = \frac{1}{n-1}\mathbf{P(XX^T)P^T}$$

Dabei ist zu beachten das $\mathbf{XX^T}$ symmetrisch ist.

So wird für die Principal Component Analysis nur eine othonormale Matritze $\mathbf{P}$ benötigt, so dass $\mathbf{S_y} = \mathbf{P(XX^T)P^T}$ eine Diagonal Matrix ergibt.

### Einbezug von Eigenvektoren und Eigenwerten

Die Principal Component Analysis kann auch mit den Prinzipien der Eigenvektoren und Eigenvalues erweitert werden. Dabei werden folgende Definitionen beigezogen.

1. $\mathbf{A}$ ist eine Quadratische Matrize mit den Werten
2. Ein Vektor $\mathbf{v \ne 0}$ wird Eigenvektor genannt wenn $Av = \lambda v$
3. Dabei ist $\lambda$ Eigenwert für den Eigenvektor $\mathbf{v}$

Um Eigenvektoren zu errechnen muss die Gleichung $(A-\lambda l)v = 0$ gelöst werden.

Eine symmetrisch Matrize $\mathbf{A}$ kann immer zu $\mathbf{A = EDE^T}$ faktorisiert werden. Wobei $\mathbf{D}$ eine Diagonal Matrix der Eigenwerte ist. Die Matritze $\mathbf{E}$ die Eigenvektoren in den Spalten darstellt. Dies wird als **Eigendekomposition** bezeichnet.

Dies wird nun in der Principal Component Analysis miteinbezogen. Wie bereits beschrieben ist für die PCA ein $\mathbf{X}$ gegeben dazu muss ein $\mathbf{P}$ gefunden werden welches $\mathbf{P(XX^T)P^T}$ diagonalisiert. Nun kann mithilfe der Eigendekomposition wie folgt vorgegangen werden.

1. Eigenvektoren von $\mathbf{XX^T}$ bestimmen
2. Eigenvektoren in eine Matritze $\mathbf{E}$ als Spalten erstellen
3. Anschliessend ist $\mathbf{P=E^T}$.
4. Nun kann die eigentlich gesuchte Matrize $\mathbf{Y}$ einfach berechnet werden durch $\mathbf{Y = PX}$ 

Dabei gilt für die PCA folgendes zu beachten.

- Die Matritze $\mathbf{Y}$ besitzt die gleiche Anzahl Features wie die Originaldaten von $\mathbf{X}$ 
- Jedes Feature in $\mathbf{Y}$ ist eine linear Kombination der original Features in $\mathbf{X}$ 
- Die Transformations Matritze $\mathbf{P}$ beinhaltet die Gewichtung der linear Kombination

## Dimensionality Reduction mit Eigenvalues und Eigenvektoren

### Dimensionalitäts Reduktion ohne Informationsverlust

- Die diagonale Kovarianz Matritze $\mathbf{S_y}$ besteht aus den Eigenwerten von $\mathbf{XX^T}$ 
- Jeder Eigenwert gehört zu einer Varianz der Features in  $\mathbf{Y}$
- Features mit Varianz $0$ besitzen keinen Informationsgehalt
- So können alle Features mit Varianz $0$ entfernt werden.

### Dimensionalitäts Reduktion ohne Informationsverlust

- Die Summe der Eigenwerte in $\mathbf{S_y}$ korrespondiert mit der totalen Varianz der Daten
- Es kann errechnet werden wie viel $\%$ ein Feature zur totalen Varianz beiträgt
- So kann bestummen werden wie viel $\%$ der Infromationen verloren gehen, wenn ein Feature entfernt wird





