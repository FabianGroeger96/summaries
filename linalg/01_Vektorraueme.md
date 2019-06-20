# Vektorräume

## Vektorraum

Menge $V$ heisst **Vektorraum**, wenn zwei Operationen definiert sind:

$$
\begin{aligned}
    v, w \in V &\mapsto v + w \in V &\quad \text{(Addition)} \\
    v \in V, s \in \mathbb{R} &\mapsto sv \in V &\quad \text{(skalare Multiplikation)}
\end{aligned}
$$

- Nullraum $V = {0}$, ist der kleinste Vektorraum
- Menge der reellen Zahlen $V = \mathbb{R}$ ist ein Vektorraum
- Für alle $m,n \in \mathbb{N}$ ist die Menge $V = \mathbb{R}^{m\times n}$ ein Vektorraum

## Unterraum eines Vektorraum

- Teilmenge eines Vektorraums, die ihrerseits wieder ein Vektorraum ist
- Teilmenge $U \subseteq V$ eines Vektorraums $V$ heisst Unterraum, falls:

$$
\begin{aligned}
    &U_1) \quad \vec{0} \in U \\
    &U_2) \quad v,w \in U \mapsto v + w \in U \\
    &U_3) \quad v \in U, s \in \mathbb{R} \mapsto sv \in U
\end{aligned}
$$

## Funktionsräume


Analog zu den Vektorräumen werden die Funktionsräume beschrieben.
- verhalten sich bezüglich der Addition und skalaren Multiplikation genau wie Vektoren
- Der Nullvektor wird im Funktionenraum als Nullfunktion bezeichnet, Funktion welche jedem $x$ den Wert $0$ zuordnet

$$
\begin{aligned}
    f(x + y) &= f(x) + f(y) \qquad &\text{für alle } x \in \mathbb{R} \\
    f(sx) &= sf(x) \qquad &\text{für alle } x \in \mathbb{R}
\end{aligned}
$$

## Unterräume eines Funktionsraum

Analog zu den Unterräumen in Vektorräumen.

$$
\begin{aligned}
    &U_1) \quad \vec{0} \in U \\
    &U_2) \quad f(x),f(y) \in U \mapsto f(x) + f(y) \in U \\
    &U_3) \quad f(x) \in U, s \in \mathbb{R} \mapsto sf(x) \in U
\end{aligned}
$$

### Beispiel

$$
\begin{aligned}
    &U = \left\{
        \begin{bmatrix}
        x_1 \\
        x_2
        \end{bmatrix}
        \in \mathbb{R}^2 \Bigg\vert x_1 + 2x_2 = 0
    \right\} \\
    &\text{Ist $U$ ein Unterraum von $\mathbb{R}^2$?} \\
    \\
    &U_1) \quad x = \begin{bmatrix}
        0 \\
        0
    \end{bmatrix} \\
    &U_1) \quad x_1 + 2x_2 = 0 \quad \rightarrow \quad 0 + 2 \cdot 0 = 0  \quad \checkmark \\
    \\
    &U_2) \quad x = \begin{bmatrix}
        x_1 \\
        x_2
    \end{bmatrix}, \quad y = \begin{bmatrix}
        y_1 \\
        y_2
    \end{bmatrix} \in U \\
    &U_2) \quad f(x) = x_1 + 2x_2, \quad f(y) = y_1 + 2y_2 \\
    &U_2) \quad f(x+y) = (x_1 + y_1) + 2(x_2 + y_2) \\
    &U_2) \quad = x_1 + y_1 + 2x_2 + 2y_2 = (x_1 + 2x_2) + (y_1 + 2y_2) = f(x) + f(y) \quad \checkmark \\
    \\
    &U_3) \quad x = \begin{bmatrix}
        x_1 \\
        x_2
    \end{bmatrix} \\
    &U_3) \quad sf(x) = s(x_1 + 2x_2) \\
    &U_3) \quad f(sx) = s \cdot x_1 + s \cdot 2x_2 \\
    &U_3) \quad = s(x_1 + 2x_2) = sf(x)  \quad \checkmark \\
\end{aligned}
$$



## Lineare Unabhängigkeit

Die Vektoren $v_1,\cdots,v_n$ werden als linear unabhängig bezeichnet wenn eine Linearkombinationen der Vektoren Null ist, dann müssel alle Koeffizieten $s_1,\cdots,s_n$ Null sein. Anderfalls heissen sie linear abhängig.

Also gilt für beliebige $s_1,\cdots,s_n \in{\R}$,

$$ s_1v_1+ \cdots + s_1v_1 = 0 \quad \rArr \quad  s_1 = \cdots = s_n = 0 \rArr s = [0,\cdots,0]^\mathbf{T}$$

## Basis

Falls es Vektoren $v_1,\cdots,v_n \in{V}$ gibt die eine Basis des Raumes $V$ bilden. Kann jeder im Raum $V$ befindlicher Vektor $v$ mithilfe einer linear Kombination der Basis von $V$, $v_1,\cdots,v_n$, beschrieben werden.

Damit eine die Vektoren $v_1,\cdots,v_n$ eine Basis von $V$ bilden, muss folgendes erfüllt sein.

$$\begin{aligned}
&a) \ \text{Müssen den gazen Vektorraum $V$ erzeugen, d.h. $V = span(v_1,\dots,v_n$)}\\
&b) \ v_1,\dots,v_n \ \text{sind linear uabhängig} 
\end{aligned}
$$

### Beispiel im Vektorraum
Sind die Vektoren,

$$ w_1 = \begin{bmatrix} 2 \\ 1 \\ 0\end{bmatrix} \quad
 w_2 = \begin{bmatrix} 1 \\ 2 \\ 0\end{bmatrix} \quad
 w_3 = \begin{bmatrix} -1 \\ -1 \\ 2\end{bmatrix}$$

eine Basis des Raum $\R^3$. Falls ja stellen Sie den Vektor $v = \begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}$ in dieser Basis dar.

$$
\begin{aligned}
&U_1) \ \text{Beweis der linearen Unabhängigkeit zwischen $w_1,w_2,w_3$}
\\
&U_1) \ s_1v_1+ \cdots + s_1v_1 = 0 \rArr \text{Liefert ein LGS}
\\
&U_1) \ s_1\begin{bmatrix} 2\\1\\0\end{bmatrix} +
s_2\begin{bmatrix} 1\\2\\0\end{bmatrix} +
s_3\begin{bmatrix} -1\\-1\\2\end{bmatrix} = \begin{bmatrix}
0 \\ 0 \\ 0\end{bmatrix} = 0 \lrArr \begin{pmatrix}
2s_1 + s_2 - s_3 = 0 \\
s_1 + 2s_2 - s_3 = 0 \\
2s_3 = 0 \\\end{pmatrix}
\\
&U_1) \ \begin{array}{ccc|c}
2 & 1 & -1 & 0 \\
1 & 2 & -1 & 0 \\
0 & 0 & 2 & 0 \end{array}
Z_{12}(-1/2) \lrArr
\begin{array}{ccc|c}
2 & 1 & -1 & 0 \\
0 & 3/2 & -1/2 & 0 \\
0 & 0 & 2 & 0 \end{array}
\\
&U_1) \ 2s_3 = 0 \rArr s_3 = 0
\\
&U_1) \ 3/2s_2 - 0 = 0 \rArr s_2 = 0
\\
&U_1) \ 2s_1 + 0 - 0 = 0 \rArr s_1 = 0
\end{aligned}
$$

$U_1)$ beweist das die Vektoren $w_1, w_2, w_3$ linear unabhängig sind.

$$
\begin{aligned}
&U_2) \ \text{Beweis das $w_1,w_2,w_3$ den gesamten Raum $\R^3$ aufspannen.}
\\
&U_2) \ \R^3 = span(w_1,w_2,w_3)
\\
&U_2) \ s_1v_1+ \cdots + s_1v_1 = \begin{bmatrix}
x_1 \\ x_2 \\ x_3 \end{bmatrix} \rArr \text{Liefert ein LGS}
\\
&U_2) \ s_1\begin{bmatrix} 2\\1\\0\end{bmatrix} +
s_2\begin{bmatrix} 1\\2\\0\end{bmatrix} +
s_3\begin{bmatrix} -1\\-1\\2\end{bmatrix} = \begin{bmatrix}
x_1 \\ x_2 \\ x_3\end{bmatrix}\lrArr \begin{pmatrix}
2s_1 + s_2 - s_3 = x_1 \\
s_1 + 2s_2 - s_3 = x_2 \\
2s_3 = x_3 \\\end{pmatrix}
\\
&U_2) \ \begin{array}{ccc|c}
2 & 1 & -1 & x_1 \\
1 & 2 & -1 & x_2 \\
0 & 0 & 2 & x_3 \end{array}
Z_{12}(-1/2) \lrArr
\begin{array}{ccc|c}
2 & 1 & -1 & x_1 \\
0 & 3/2 & -1/2 & x_2 - \frac{x_1}{2} \\
0 & 0 & 2 & x_3 \end{array}
\\
&U_2) \ 2s_3 = x_3 \rArr s_3 = \frac{x_3}{2}
\\
&U_2) \ \frac{3}{2}s_2 - \frac{x_3}{4} = x_2 - \frac{x_1}{2} \rArr s_2 = \frac{x_2 - \frac{x_1}{2} + \frac{x_3}{4}}{1.5}
\\
&U_2) \ 2s_1 + \frac{x_2 - \frac{x_1}{2} + \frac{x_3}{4}}{1.5} - \frac{x_3}{2}   = x_1 \rArr s_1 = (\frac{x_2 - \frac{x_1}{2} + \frac{x_3}{4}}{1.5} + \frac{x_3}{2}) / 2
\end{aligned}
$$

$U_2)$ beweist das es eine eindeutige Lösung für das erstellen eines beliebigen Vektor $x$ gibt.

$$
\begin{aligned}
&U_3) \ \text{Koordinaten von $[1,1,1]^T$ berechnen. Mit $s_1,s_2,s_3$ aus $U_2$}
\\
&U_3) \ \text{oder berechnung mithilfe der Zeilenumformung}
\\
&U_3) \ s_1v_1+ \cdots + s_1v_1 = \begin{bmatrix}
1 \\ 1 \\ 1 \end{bmatrix} \rArr \text{Liefert ein LGS}
\\
&U_3) \ s_1\begin{bmatrix} 2\\1\\0\end{bmatrix} +
s_2\begin{bmatrix} 1\\2\\0\end{bmatrix} +
s_3\begin{bmatrix} -1\\-1\\2\end{bmatrix} = \begin{bmatrix}
1 \\ 1 \\ 1\end{bmatrix}\lrArr \begin{pmatrix}
2s_1 + s_2 - s_3 = 1 \\
s_1 + 2s_2 - s_3 = 1 \\
2s_3 = 1 \\\end{pmatrix}
\\
&U_3) \ \begin{array}{ccc|c}
2 & 1 & -1 & 1 \\
1 & 2 & -1 & 1 \\
0 & 0 & 2 & 1 \end{array}
Z_{12}(-1/2) \lrArr
\begin{array}{ccc|c}
2 & 1 & -1 & 1 \\
0 & 3/2 & -1/2 & \frac{1}{2} \\
0 & 0 & 2 & 1 \end{array}
\\
&U_3) \ 2s_3 = 1 \rArr s_3 = \frac{1}{2}
\\
&U_3) \ \frac{3}{2}s_2 - \frac{1}{4} = \frac{1}{2} \rArr s_2 = \frac{1}{2}
\\
&U_3) \ 2s_1 + \frac{1}{2} - \frac{1}{2} = 1 \rArr s_1 = \frac{1}{2}
\end{aligned}
$$

Aus $U_3$ folgt,

$$ s =  \begin{bmatrix} s_1 \\ s_2 \\ s_3 \end{bmatrix} = \begin{bmatrix} 1/2 \\ 1/2 \\ 1/2 \end{bmatrix}$$

$$ \begin{bmatrix} 1 \\ 1 \\1 \\ \end{bmatrix} = 
\frac{1}{2} \begin{bmatrix}
2 \\ 1 \\ 0\end{bmatrix} + 
\frac{1}{2} \begin{bmatrix}
1 \\ 2 \\ 0\end{bmatrix} +
\frac{1}{2} \begin{bmatrix}
-1 \\ -1 \\ 2\end{bmatrix}$$

## Aufgespannte Unterraum

- Der von einer Menge Vektoren aufgespannte Unterraum ist der Raum welche alle Linearkombination von $U = span(v_1,\cdots,v_n)$ enthält.
- Der aufgespannte Unterraum $U$ durch die Vektoren $v_1,v_2,v_3$ wird als $U = span(v_1,v_2,v_3)$ bezeichnet. 
- Die Basis eines aufgespannten Unterraums lässt sich bilden in dem die Vektoren $v_1,\dots,v_n \in{U}$ in eine Treppenform überführt werden. 
- Alle Spalten mit Pivot-Element $v_1,\dots,v_j$ bilden die Basis von $U = span(v_1,\cdots,v_n)$. -> Vektoren der ursprünglichen Form verwenden!

Daraus folgt,

$$\begin{aligned}
&a) \ \text{Ein Vektor der Form} \quad t_1v_1+\cdots+t_kv_k \quad \text{mit} \quad t_1,\cdots,t_k \in{\R} \\
&\text{heisst Linearkombination von $v_1,\cdots,v_k$.} \\
&b) \ \text{Die Menge der Linearkombinationen von $v_1,\cdots,v_k$ ist $span(v_1,\cdots,v_k)$.} \\
&span(v_1,\cdots,v_k) = {t_1v_1+\cdots+t_kv_k|t_1,\cdots,t_k \in{\R}}

\end{aligned}$$