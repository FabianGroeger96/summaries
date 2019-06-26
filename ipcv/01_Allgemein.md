# Allgemeines

## Lichtspektrum

$$ \includegraphics[width=0.5\columnwidth]{images/lichtspektrum.jpg} $$

## Umrechnen von Farbsystemen

### RGB zu CMY

$$
\begin{aligned}
    &\text{Vorbedingung: RGB muss in Bereich von $[0,1]$ liegen!} \\
    \\
    &C = 1-R \\
    &M = 1-G \\
    &Y = 1-B
\end{aligned}
$$

### CMY zu RGB

$$
\begin{aligned}
    &R = 1-C \\
    &G = 1-M \\
    &B = 1-Y \\
    \\
    &\text{Nachbedingung: RGB liegt im Bereich von $[0,1]$}
\end{aligned}
$$

### RGB zu CMYK

$$
\begin{aligned}
    &\text{Vorbedingung: RGB muss in Bereich von $[0,1]$ liegen!} \\
    \\
    &K = 1 - max(R,G,B) \\
    \\
    &C = \frac{1-R-K}{1-K} \\
    &M = \frac{1-G-K}{1-K} \\
    &Y = \frac{1-B-K}{1-K}
\end{aligned}
$$

### CMYK zu RGB

$$
\begin{aligned}
    &R = (1-C) \cdot (1-K) \\
    &G = (1-M) \cdot (1-K) \\
    &B = (1-Y) \cdot (1-K) \\
    \\
    &\text{Nachbedingung: RGB liegt im Bereich von $[0,1]$}
\end{aligned}
$$

### RGB zu HSV

$$
\begin{aligned}
    &\text{Vorbedingung: RGB muss in Bereich von $[0,1]$ liegen!} \\
    \\
    &MAX = max(R, G, B) \quad \quad MIN = min(R, G, B) \\
    \\
    &H = \left\{ \begin{matrix}
        0^{\degree}, &\quad \quad \text{falls} \ MAX = MIN \\
        60^{\degree} \cdot (0 + \frac{G-B}{MAX - MIN}), \quad \quad &\text{falls} \ MAX = R \\
        60^{\degree} \cdot (2 + \frac{B-R}{MAX - MIN}), \quad \quad &\text{falls} \ MAX = G \\
        60^{\degree} \cdot (4 + \frac{R-G}{MAX - MIN}), \quad \quad &\text{falls} \ MAX = B \\
    \end{matrix} \right\} \\
    &\text{falls $H < 0^{\degree}$ dann $H = H + 360^{\degree}$} \\
    \\
    &S = \left\{ \begin{matrix}
        0, \quad \quad &\text{falls} \ MAX = 0 \\
        \frac{MAX - MIN}{MAX}, \quad \quad &\text{sonst}
    \end{matrix}\right\} \\
    \\
    &V = MAX \\
    \\
    &\text{Nachbedingung: H liegt im Bereich von $[0^{\degree}, 360^{\degree}]$} \\
    &\text{S, V liegen im Bereich von $[0,1]$}
\end{aligned}
$$

### HSV zu RGB

$$
\begin{aligned}
    &\text{Vorbedingung: H liegt im Bereich von $[0^{\degree}, 360^{\degree}]$} \\
    &\text{S, V liegen im Bereich von $[0,1]$} \\
    \\
    &h_i = \frac{H}{60^{\degree}} \\
    &f = \frac{H}{60^{\degree}} - h_i \\
    \\
    &p = V \cdot (1 - S) \\
    &q = V \cdot (1 - S \cdot f) \\
    &t = V \cdot (1 - S \cdot (1 - f)) \\
    \\
    &(R, G, B) = \left\{ \begin{matrix}
        (V,t,p), \quad \quad &\text{falls} \ h_i = 0 \ \text{oder} \ h_i = 6 \\
        (q,V,p), \quad \quad &\text{falls} \ h_i = 1 \\
        (p,V,t), \quad \quad &\text{falls} \ h_i = 2 \\
        (p,q,V), \quad \quad &\text{falls} \ h_i = 3 \\
        (t,p,V), \quad \quad &\text{falls} \ h_i = 4 \\
        (V,p,q), \quad \quad &\text{falls} \ h_i = 5
    \end{matrix} \right\} \\
    \\
    &\text{Nachbedingung: RGB liegt im Bereich von $[0,1]$}
\end{aligned}
$$