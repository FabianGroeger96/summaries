# Braindump Answers

## Farbsysteme

### RGB - CMY

Mit $R', G', B' = f(x), f(x) = x/255$

$$ \begin{bmatrix}
C \\ M \\ Y
\end{bmatrix} = 
\begin{bmatrix}
1 \\ 1 \\ 1
\end{bmatrix} -
\begin{bmatrix}
R' \\ G' \\ B'
\end{bmatrix} $$

$$ \begin{bmatrix}
R' \\ G' \\ B'
\end{bmatrix} = 
\begin{bmatrix}
1 \\ 1 \\ 1
\end{bmatrix} -
\begin{bmatrix}
C \\ M \\ Y
\end{bmatrix} $$

### CMY - CMYK

$$ \begin{bmatrix}
C \\ M \\ Y
\end{bmatrix} = 
\begin{bmatrix}
C \\ M \\ Y \\ max(C, M, Y)
\end{bmatrix} $$

### RGB - HSV

Mit $R', G', B' = f(x), f(x) = x/255$

$$
\begin{aligned}
    Cmax = max(R', G', B')
\\
Cmin = min(R', G', B')
\\
\triangle = Cmax - Cmin
\\
\\
H = \begin{cases}
0^{\circ} &\quad \triangle = 0 \\
60^{\circ} \times (\frac{G' - B'}{\triangle}mod(6)) &\quad C_{max} = R' \\
60^{\circ} \times (\frac{B' - R'}{\triangle}+2) &\quad  C_{max} = G' \\
60^{\circ} \times (\frac{R' - G'}{\triangle}+4) &\quad C_{max} = B' \\
\end{cases} \\
\\
S = \begin{cases}
0 &\quad C_{max} = 0 \\
\frac{\triangle}{C_{max}} &\quad C_{max} \neq 0
\end{cases} \\
\\
V = C_{max}
\end{aligned}$$

Mit $0 \leq H < 360, 0 \leq S \leq 1, 0\leq V \leq 1$

$$
\begin{aligned}
C = V \times S
\\
X = C \times (1 - |(H / 60^{\circ})*mod(2)-1|)
\\
m = V-C
\\
(R',G',B') = \begin{cases}
(C,X,0) &\quad 0^{\circ} \leq H < 60^{\circ} \\
(X,C,0) &\quad 60^{\circ} \leq H < 120^{\circ} \\
(0,C,X) &\quad 120^{\circ} \leq H < 180^{\circ} \\
(0,X,C) &\quad 180^{\circ} \leq H < 240^{\circ} \\
(X,0,C) &\quad 240^{\circ} \leq H < 300^{\circ} \\
(C,0,X) &\quad 300^{\circ} \leq H < 360^{\circ} \\
\end{cases} \\
\\
(R,G,B) = ((R'+m)*255,(G'+m)*255,(B'+m)*255)
\end{aligned}
$$

## Objekterkennung

### Wie kann ein roter Ball in einem Bild anvisiert werden?

Um diese Aufgabe zu lösen können mehrere Ansätze verwendet werden.

- **Histogrammvergleich**: Vegleichen von Sliding Windows mit einem Histogramm des roten Balles
- **Features**: Ball über Features definieren und Bild nach Feature absuchen.
    - **Feature Detection** -> Feature Punkte auf Bild finden, HoughTransform, Harris Corners, SIFT, SURF, BRIEF
    - **Feature Extraction** -> Bereitstellen für das Matching, SIFT
    - **Feature Matching** -> Finden des Feature auf einem Bild, RANSAC
- Auch könnten ML-Ansätze mit Features verwendet werden
  - k-Nearest Neighbor
  - SVM
  - Boosting
  - Logistic Regression
- Weiter können Kombinationen verwendet werden.
- Wichtig ist ebenfalls das Bild für das Isolieren des entsprechenden Objekts vorubereiten. z.B. in dem nur der Rot-Kanal für den Ball verwendet wird.
