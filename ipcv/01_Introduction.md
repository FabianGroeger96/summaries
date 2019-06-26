# Introduction

## Bildverarbeitung

Computergrafik $\lrarr$ Bildverarbeitung

- Computergrafik -> Erzeugung von realisitischen bildern aus der Beschreibung von Objekten.
- Bildverarbeitung -> Erkennung von Objekten oder Szenen aus Bildern

Weiter aufgeteilt in drei Stufen,

- Low Level Vision (Image Processing) -> Bildverbesserung, Erkennung -> von Low Level Features
- Mid Level Vision
- High Level Vision (Computer Vision) -> Interpretation des Bildes, Erkennung von Objekten

## Image Pre-Prcessing

- Informationen verstärken, z.B. Wertebereich manipulieren um gewisse, intressanten Strukturen darzustellen
- Reduktion von Störungen (Rauschen, Artefakte, Beleuchtungsfehler)

Unterscheidung zwischen zwei Operatoren

- Punktopreatoren: Operation auf einem Punkt, i.e. nur dieser Pixelwert wird transformiert
- Nachbarschaftsoperatoren: Ergebings hängt von der Umgebung des Punktes ab. (Filteropreationen)

### Punktbildfunktonen

Veränderung der Intensitätswerte durch eine Funktion.

- Schwellwert
- Helligkeitsveränderung
- Kontrast Korrektur
- Gamma Korrektur

Mit $i = \ \text{Intensitätswert}$

$$ i_{neu} = f(i_{alt})$$

#### Helligkeitsveränderung

Bei der Helligkeitsveränderung handelt es sich um eine Verschiebung der Intensitätswerte $i$ Richtung der y-Achse. Dabei werden werte welche die Grenze des Wertebereichs erhalten auf $min$ oder $max$ gesetzt.

#### Kontrastveränderung

Bei der Kontrastveränderung werden die Bildpunkte mithilfe einer Rotation manipuliert. Wieder werden Werte ausserhalb des Wertebereich angepasst.

#### Gamma-Korrektur

Die Gammakorrektur ist eine namentlich im Bereich der Bildverarbeitung häufig verwendete Korrekturfunktion zur Überführung einer physikalisch proportional (d. h. linear) wachsenden Größe in eine dem menschlichen Empfinden gemäß nicht linear wachsende Größe. Mathematisch gesehen handelt es sich bei dieser Funktion um eine Potenzfunktion mit einem oft nur kurz Gamma genannten Exponenten als einzigem Parameter. 

$$ f(i) = i^\gamma $$

### Histogramm

Farbverteilung des Bildes: Wie häufig kommt welche Farbe / Helligkeit vor.

$$ H(k) = |\{x_i | v_k \leq I(x_i) < v_{k+i} \}| $$

- $k$ : Anzahl "Bins" des Histogramms
- $v_k$: Werte der Bins

Bins = Unterteilungen des Wertebereichs

Änderung des Histogramms wenn eine Punktbildfunktion $f(i)$ angewandt wird.

$$ H_{neu}(i) = H_{alt}(i)\cdot\frac{1}{f'(i)}$$

#### Histogrammausgleich

Auch "Auto Contrast" bei Bildverarbeitungstools. Transforamtion der Grauwerte, so dass das Histogramm des neuen Bildes möglichst ausgeglichen ist.

Dabei wird $H_{neu} = constant$ und die Formel zur Berechnung des Histogramms.

$$ f'(i) = \frac{1}{c}H_{alt}(i)
\\
f(i) = \frac{1}{c}\int_0^i H_{alt}(j)dj
\\
f[g] = norm_{max} \cdot \sum_{i=0}^g p[i]
$$

- $f[g]$: Neuer Werte für Pixel mit Wert $g$
- $norm_{max}$: Normalisiertes Maximum des Bildes. $\frac{Höchster Wert}{Anzahl Pixel}$
- $p[i]$: Kummulierte Häufigkeit des Wertes $i$.

Vorgehen für die Berechnung:

1. Vorkommende Pixelwerte von kleinsten Wert bis grösstem Wert notieren
2. Häufigkeit der Pixelwerte
3. Kummulierte Häufigkeit
4. Histrogrammausgleich mit $f[g] = norm_{max} \cdot \sum_{i=0}^g p[i]$
5. Resultate Runden

## Morphologische Operationen

Morphologische Operationen werden zur Bearbeitung von Binärbildern verwendet. Binärbilder können zum Beispiel mit dem Setzen eines Schwellwerts (Threshold) erzeugt werden. Enstandene Regionen müssen jedoch häufig weiterverarbeitet werden.

z.B. die Regionen von "Haut" mithilfe eines Skin-Detect und Schwellwert.

Morhpologische Operationen können durch Mengenoperation dargestellt werden. Dabei wird das Bild mit einenm Strukturelement verknüpft, dieses ist als Matrix definiert, z.B.

$$ S = \begin{pmatrix} 1 \ 1 \ 1 \\ 1 \ 1 \ 1 \\ 1 \ 1 \ 1 \end{pmatrix} $$

### Dilate

Verdickt das Objekt. A ist dabei d

$$ A \oplus S = \{x | A \cap S_x \neq 0  \ \} $$

### Erode

Verdünnt das Objekt. 

$$ A \ominus S = \{x | \bar{A} \cap S_x \neq 0 \} 
\\ = \{x|A \supseteq S_x \}$$