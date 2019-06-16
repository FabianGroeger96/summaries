# Quiz 6 - Principal Component Analysis

## Correlation

$$ \mathbf{XX^T} = \begin{bmatrix}
\sum_{i=1}^n x_{1i} \times x_{1i} \ \sum_{i=1}^n x_{1i} \times x_{2i} \ \sum_{i=1}^n x_{1i} \times x_{3i} \\
\sum_{i=1}^n x_{2i} \times x_{1i} \ \sum_{i=1}^n x_{2i} \times x_{2i}  \ \sum_{i=1}^n x_{2i} \times x_{3i} \\
\sum_{i=1}^n x_{3i} \times x_{1i} \ \sum_{i=1}^n x_{3i} \times x_{2i} \ \sum_{i=1}^n x_{3i} \times x_{3i} 
\end{bmatrix}$$

Wird zu $\mathbf{S_x}$

$$\mathbf{S_x} = \frac{1}{n-1}\mathbf{XX^T} = \begin{bmatrix}
Var(x_{1}) \ Cov(x_1,x_2) \ Cov(x_1, x_3) \\
Cov(x_2, x_1) \ Var(x_2) \ Cov(x_2, x_3) \\
Cov(x_3, x_1) \ Cov(x_3, x_2) \ Var(x_3)
\end{bmatrix}$$

$$ \mathbf{S_x} = \text{Kovarianz Matrix} $$

### Pearson Correlation

$$
\begin{aligned}
    p(X, Y) = \frac{Cov(X, Y)}{\sigma_X \sigma_Y} \\
     \sigma_x = \sqrt{Var(x)}
\end{aligned}
$$

## PCA

- PCA Main Components zeigen entlang der linearen Streuung.
- Positiv oder Negativ

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

