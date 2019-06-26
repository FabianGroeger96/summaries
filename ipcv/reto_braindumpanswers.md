
# Farbsysteme

## RGB - CMY

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

## CMY - CMYK

$$ \begin{bmatrix}
C \\ M \\ Y
\end{bmatrix} = 
\begin{bmatrix}
C \\ M \\ Y \\ max(C, M, Y)
\end{bmatrix} $$

## RGB - HSV

Mit $R', G', B' = f(x), f(x) = x/255$

$$ Cmax = max(R', G', B')
\\
Cmin = min(R', G', B')
\\
\triangle = Cmax - Cmin
\\
H = \begin{cases}
0° &\quad \triangle = 0 \\
60° \times (\frac{G' - B'}{\triangle}mod(6)) &\quad C_{max} = R' \\
60° \times (\frac{B' - R'}{\triangle}+2) &\quad  C_{max} = G' \\
60° \times (\frac{R' - G'}{\triangle}+4) &\quad C_{max} = B' \\
\end{cases}
\\
S = \begin{cases}
0 &\quad C_{max} = 0 \\
\frac{\triangle}{C_{max}} &\quad C_{max} \neq 0
\end{cases}
\\
V = C_{max} $$

Mit $0 \leq H < 360, 0 \leq S \leq 1, 0\leq V \leq 1$

$$
C = V \times S
\\
X = C \times (1 - |(H / 60°)*mod(2)-1|)
\\
m = V-C
\\
(R',G',B') = \begin{cases}
(C,X,0) &\quad 0° \leq H < 60° \\
(X,C,0) &\quad 60° \leq H < 120° \\
(0,C,X) &\quad 120° \leq H < 180° \\
(0,X,C) &\quad 180° \leq H < 240° \\
(X,0,C) &\quad 240° \leq H < 300° \\
(C,0,X) &\quad 300° \leq H < 360° \\
\end{cases}
\\
(R,G,B) = ((R'+m)*255,(G'+m)*255,(B'+m)*255)
$$

# Objekterkennung

## Wie kann ein roter Ball in einem Bild anvisiert werden?

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



