# Support Vector Machines (SVM)

## Scalar Product

$$ a \bullet b = a_1b_1 + a_2b_2 + ... + a_nb_n = \sum_{j=1}^n a_jb_j $$

Regeln:
$$
\begin{aligned}
    a \bullet b = b \bullet a \\
    a \bullet (b + c) = a \bullet b + a \bullet c \\
    \lambda(a \bullet b) = (\lambda a) \bullet b = a \bullet (\lambda b)
\end{aligned}
$$

## Länge eines Vektors

$$
\begin{aligned}
    ||a|| = \sqrt{a \bullet a} \\
    ||a||^2 = a \bullet a \\
    ||n|| = 1
\end{aligned}
$$

## Zwei Vektoren senkrecht

Zwei Vektoren $a$ und $b$ sind senkrecht zueinander, wenn ihr Skalarprodukt 0 ist
$$
    a \bullet b = 0 \Leftrightarrow a \perp b
$$

## Hessian Normal Form

$$
    n \bullet (x - x_0) \Leftrightarrow n \perp (x - x_0)
$$

### Beispiel

$$ \includegraphics[width=0.7\columnwidth]{images/hessian_normal_form_example.png} $$

Berechne die hessische Normalform von $\vec{n} = \frac{1}{\sqrt{13}}\begin{bmatrix}2 \\3\end{bmatrix}$

$$
\begin{aligned}
    0 = \vec{n} \bullet (\vec{x} - \vec{x_0}) = \frac{1}{\sqrt{13}}
    \begin{bmatrix}
    2 \\
    3
    \end{bmatrix} \bullet \Bigg(\begin{bmatrix}
    x \\
    y
    \end{bmatrix} - 
    \begin{bmatrix}
    0.5 \\
    2
    \end{bmatrix}\Bigg) =
    \frac{1}{\sqrt{13}}
    \begin{bmatrix}
    2 \\
    3
    \end{bmatrix} \bullet \begin{bmatrix}
    x - 0.5 \\
    y - 2
    \end{bmatrix} \\
    = \frac{1}{\sqrt{13}} (2(x-0.5) + 3(y-2)) \\
    = \frac{1}{\sqrt{13}} (2x + 3y -1 -6) \\
    = \frac{2}{\sqrt{13}}x + \frac{3}{\sqrt{13}}y - \frac{7}{\sqrt{13}} \\
    \text{(von der Form ax + by + c = 0)} \\
    \\
    \vec{n} = \begin{bmatrix}
    \frac{2}{\sqrt{13}} \\
    \frac{3}{\sqrt{13}}
    \end{bmatrix}
\end{aligned}
$$

--> Maybe more detailed

## Einführung

$$ \includegraphics[width=0.7\columnwidth]{images/support_vector_machine_visualisation.png} $$

- Klassifizieren der Daten bedeutet aufspalten der Daten
- Viele verschiedene Arten die Daten aufzuspalten
- Mittlere Linie wird als **Hyperplane** bezeichnet
- Datenpunkte welche am nächsten zu der Hyperplane sind, werden **Support Vektoren** genannt
- Den Margin zu maximieren, ist ein constrained Optimierungsproblem
- Wir sollen den Abstand (Margin) zwischen den beiden Klassen so weit wie möglich haben unter der Bedingung, dass keine Punkte innerhalb dieses Abstands sind
- Diese Optimierungsprobleme werdem mittels **Lagrange Multipliers** gelöst

## Idee und Möglichkeiten von SVM

- Findet die optimale Hyperplane für linear seperierbare Muster
- Nicht linear seperierbare Muster werden transformiert, so dass diese linear seperierbar sind, mittels einer _kernel Funktion_ in eine höhere Dimension
- ist nicht vom Lokalen Minima Problem betroffen
- hat kein Dimensionenproblem
- Support Vektoren sind Datenpunkte, welche
  - am nächsten zu der Decison- / Hyperplane sind
  - am schwierigsten sind zum klassifizieren
  - die Position der Hyperplane direkt beeinflussen
  - wenn gelöscht, zu einer komplett anderen Hyperplane führen
  - die kritischen Elemente im Trainingsset sind

## Lineare Separierbarkeit

$$ \includegraphics[width=0.7\columnwidth]{images/svm_linear_seperability.png} $$

## Linearer Klassifikator

$$
\begin{aligned}
    \text{Linear Classifier using baised coordinates: } \\
    f(x) = \theta^Tx \\
    \text{Linear Classifier using unbaised coordinates: } \\
    f(x_b) = b + w^Tx_b
\end{aligned}
$$

Beide Formen sind gleichwärtig und es wird die gebraucht, die besser passt

## Soft Margin Problem

