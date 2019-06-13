# Support Vector Machines (SVM)

## Scalar Product

$$ a \bullet b = a_1b_1 + a_2b_2 + ... + a_nb_n = \sum_{j=1}^n a_jb_j $$

Regeln:
$$
\begin{aligned}
    a \bullet b &= b \bullet a \\
    a \bullet (b + c) &= a \bullet b + a \bullet c \\
    \lambda(a \bullet b) &= (\lambda a) \bullet b = a \bullet (\lambda b)
\end{aligned}
$$

## Länge eines Vektors

$$
\begin{aligned}
    ||a|| &= \sqrt{a \bullet a} \\
    ||a||^2 &= a \bullet a \\
    ||n|| &= 1
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

$$ \includegraphics[width=0.4\columnwidth]{images/hessian_normal_form_example.png} $$

Berechne die hessische Normalform von $\vec{n} = \frac{1}{\sqrt{13}}\begin{bmatrix}2 \\3\end{bmatrix}$

$$
\begin{aligned}
    0 = \vec{n} \bullet (\vec{x} - \vec{x_0}) &= \frac{1}{\sqrt{13}}
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
    &= \frac{1}{\sqrt{13}} (2(x-0.5) + 3(y-2)) \\
    &= \frac{1}{\sqrt{13}} (2x + 3y -1 -6) \\
    &= \frac{2}{\sqrt{13}}x + \frac{3}{\sqrt{13}}y - \frac{7}{\sqrt{13}} \\
    &\text{(von der Form ax + by + c = 0)} \\
    \\
    \vec{n} &= \begin{bmatrix}
    \frac{2}{\sqrt{13}} \\
    \frac{3}{\sqrt{13}}
    \end{bmatrix}
\end{aligned}
$$

--> Maybe more detailed

## Einführung

$$ \includegraphics[width=0.4\columnwidth]{images/support_vector_machine_visualisation.png} $$

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
    \text{Linear Classifier } & \text{using unbaised coordinates: } \\
    f(x) &= \theta^Tx \\
    \text{Linear Classifier } & \text{using baised coordinates: } \\
    f(x_b) &= b + w^Tx_b
\end{aligned}
$$

Beide Formen sind gleichwärtig und es wird die gebraucht, die besser passt.

### 2D-Fall

Es sei ein 2D-Problem gegeben und soll mit einem Linearen Klassifikator gelöst werden.

$$ \includegraphics[width=0.4\columnwidth]{images/2d_linearclassificator.png} $$

Dabei gibt es mehrere Lösungen für die Gleichung,

$$f(x) = \mathbf{w^T}x_b + b$$

Welche im 2D Fall mit $\mathbf{w}=\begin{bmatrix}w_1\\w_2\end{bmatrix}$ auch geschreiben werden kann als,

$$f(x) = w_1x_1 + w_2x_2 + b = 0$$

Dabei gilt anschiessend für die klassifizierung,

$$ f(x_1,x_2) = w_1x_1 + w_2x_2 + b \geq 0 \quad\text{Für die Klasse oberhalb der Gerade (Schwarz)}$$

$$ f(x_1,x_2) = w_1x_1 + w_2x_2 + b < 0 \quad\text{Für die Klasse unterhalb der Gerade (Weiss)}$$

Die Funktion $f(x)$ wird auch als **Decision Function** bezeichnet.

## Grundidee einer Support Vector Machine (SVM)

Bei einer Support Vektor Machine wird die Idee dieser **Decision Function** weiter verwendet. Um die beste **Decision Function** aus den möglichen Lösungen zu finden, wird der Abstand zu den Support Vektoren von der **Decision Function** maximiert.

$$ \includegraphics[width=0.4\columnwidth]{images/basicidea_svm.png} $$

Dabei wird die **Decision Function** komplett an diesen Support Vektoren aufgebaut. Diese sind dabei (teilweise) nur Teil der Training Daten. Dieses maximierungs-Problem ist ein quadratisches Problem.

Dabei gilt für die Support Vektoren:

$$\mathbf{w} \ \bullet \mathbf{x_b} + b = 1 \quad \text{bzw.} \quad \mathbf{w} \ \bullet \mathbf{x_b} + b = -1 $$ 

$$ \text{wobei die Decision Function} \quad \mathbf{w} \ \bullet \mathbf{x_b} + b = 0 $$

Die Distanz des Abstand wird dabei durch die Länge des Vektor $\mathbf{w}$ bestimmt.

$$ \frac{2}{\parallel\mathbf{w}\parallel} = \frac{2}{\sqrt{\mathbf{w^T}\mathbf{w}}}$$

Wie bereits erwähnt wird dabei $\frac{2}{\parallel\mathbf{w}\parallel}$ maximiert. Dies ist equivalent wie das minimieren von $\frac{\mathbf{w^Tw}}{2}$. Diese Lösung gilt als **Hard Margin** Lösung.

## Soft Margin Problem

Bei der Hard Margin Lösung gibt es ein entscheidentens Problem. Falls es Outliner gibt welche die Decision Function überschreiten ist das Problem nicht separierbar. Dafür gibt es jedoch eine Lösung welche sich **Soft Margin** nennt. Dabei wird für jeden Datenpunkt $x^{(i)}$ eine sogennante **Slack Variable** (Schlupfvariabel) definiert. Die Slack Variable $\zeta_i$ gibt an um wieviel der Datenpunkt $x^{(i)}$ gegen die Grenze verstossen darf. Dadurch ist es möglich Outliners speziell zu behandeln.

$$ \includegraphics[width=0.4\columnwidth]{images/softmargin.png} $$

Dabei gilt für alle Punkte $x^{(l)}$,

$$ y^{(l)}(\mathbf{w^T}x^{(l)}+b) \geq 1 - \zeta_l $$

Dabei gilt für alle Punkte welche separierbar sind $\zeta_l = 0$. Punkte welche nicht separierbar sind haben $\zeta_l > 0$. In diesem Beispiel sind dies $x^{(i)}$, $x^{(j)}$ und $x^{(k)}$. So folgt,

$$ y^{(i)}(\mathbf{w^T}x^{(i)}+b) \geq 1 - \zeta_i $$

$$ y^{(j)}(\mathbf{w^T}x^{(j)}+b) \geq 1 - \zeta_j $$

$$ y^{(k)}(\mathbf{w^T}x^{(k)}+b) \geq 1 - \zeta_k $$

mit $x^{(i)}, x^{(j)}, x^{(k)} > 0$.

Weiter wird eine **Regularisierungs Parameter** $C$ eingeführt. So wird das minimierungs Problem erweitert.

$$ \min_{\mathbf{w},b} \ \frac{1}{2}\mathbf{w^Tw} + C \sum_{i=1}^n \zeta_i \quad \text{bezogen auf} \quad y^{(i)}(\mathbf{w^T}x^{(i)}+b) \geq 1 - \zeta_i $$

Zusammengefasst,

- Der Margin (Grenze) für einen Punkt kann kleiner sein als $1$. Mit hilfe von $\zeta > 0$ kann dies korrigiert werden.
- Der Regularizierungs Parameter $C$ hilft overfitting zu vermeiden. Der Parameter wird mit $\zeta$ multipliziert.
    - Dabei gilt für kleine $C\rightarrow0$, dass die $\zeta$ Parameter ignoriert werden. Dadurch entsteht ein grosser Margin.
    - Für grosse $C\rightarrow\infty$ gilt, dass die $\zeta$ Parameter umso mehr ins gewicht fallen. Dabei entsteht ein kleiner Margin.
    - Falls $C=\infty$ müssen alle Datenpunkte $x^{(i)}$ richtig klassifiziert werden. Wir erhalten wieder einen Hard Margin.
- Die Summe $\sum_{i=1}^n\zeta_i$ gibt die obere Grenze für die Grösse des Trainingfehlers an
- Das Optimierungsproblem bleibt Quadratisch.

$$ \includegraphics[width=0.7\columnwidth]{images/soft_hard_margin.png} $$

Auf dem Bild wird auf der linken Seite ein **Hard Margin** mit $0.1$ und $C=\infty$ gezeigt. Rechts ein **Soft Margin** mit $0.23$ und $C=10$.

Weiter kann das Optimierungsproblem auch als unerzwungenges Problem aufgestellt werden.

$$f(x) = \mathbf{w^T}x_b + b$$
$$ \ $$
$$ y^{(i)}(\mathbf{w^T}x^{(i)}+b) \geq 1 - \zeta_i \quad \text{mit} \quad \zeta_i \geq 0 $$

was equivalent ist zu,

$$ \zeta_i = \max{(0,1-y^{(i)}f(x^{(i)}))} $$

und daraus folgt das ungebundene optimierungs Problem,

$$ \min_{\mathbf{w} \in R^m} \frac{2}{\parallel\mathbf{w}\parallel} + C\sum_{i=1}^n \max{(0,1-y^{(i)}f(x^{(i)}))} $$

## Kernel Trick

Der Kernel-Trick wird angewandt wenn ein Datensatz im vorgegabenen Raum nicht separierbar ist. Mit dem Kernel-Trick wird ein nicht separierbare Funktion auf eine separierbare Funktion abgebildet. Dabei wird die Mapping Funktion als $\phi$ beizeichnet.

Beispiele sind,

Für die Umwandlung von Cartesian Koordinaten zu Polarkoordinaten

$$ \mathbf{\phi}: R^2 \rightarrow R^2, \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} \mapsto \begin{bmatrix} r \\ \Theta \end{bmatrix} = \begin{bmatrix} \sqrt{x_1^2 + x_2^2} \\ \arctan(\frac{x_2}{x_1} \pm \pi) \end{bmatrix}$$

Für die Umwandlung von 2-D Raum in den 3-D Raum

$$ \mathbf{\phi}: R^2 \rightarrow R^3, (x_1, x_2) \mapsto (z_1,z_2,z_31) = (x_1^2, \sqrt{2}x_1x_2,x_2^2) $$

Weitere allgemeine Formen sind,

- linear: $\phi(x_1,x_2) = x_1^Tx_2$
- polynomial: $\phi(x_1,x_2) = (1+x_1^Tx_2)^d \ \text{wobei} \ d = 2,3,4,\ldots$
- radial: $\phi(x_1, x_2)=\exp(-\frac{\parallel x_1 - x_2 \parallel ^2}{2\sigma ^2})$

Dabei erfüllen Kernel-Funktionen $\phi$:

1. positive semidefinitiät, $\forall x_1, x_2 (\phi(x_1,x_2)\geq 0)$
2. symmetrisch, $\phi(x_1,x_2) = \phi(x_2,x_1)$







