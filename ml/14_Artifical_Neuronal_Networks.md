# Artifical Neuronal Networks

## Types of Artifical Neuronal Networks

Künstliche Neuronale Netzwerke unterscheiden sich in

- ihrer Architektur, welche sehr oft aus Ebenen bestehnt und Feed Forward
- wie sie "lernen" 
- den Anwendungsfall (Face, Object, Voice Recognition, Classification)
- Input und dem gewünschten Output-Layer
 
 Dabei gibt es drei Typen von ANN.

 - Single-layer feedforward networks
 - Multi-layer feedforward networks
 - Recurrent Networks (nicht behandelt)

 $$ \includegraphics[width=0.7\columnwidth]{images/anns.png} $$

Dabei versuchen ANN biologische Neuronen zu abstrahieren. Dies soll anhand von einem Beispiel aufgezeigt werden.

 $$ \includegraphics[width=0.7\columnwidth]{images/neurons.png} $$

 Dabei wird für jeden Output Node $j$ die Funktion $net_j$ berechnet. Dabei entsteht eine gewichtete Summe der Input Signale.

 $$ net_1 = w_{10}x_0+w_{11}x_1+w_{12}x_2 = \sum_{i=0}^2 w_{1i}x_i $$
 $$ net_1 = w_{20}x_0+w_{21}x_1+w_{22}x_2 = \sum_{i=0}^2 w_{2i}x_i $$

 Dabei "feuert" (fires) das Neuron falls $net > 0$. Oder aber wenn der gewichtete Input des Output Nodes $y_i$ den Threshold $\Theta_1$ überschreitet. Auch, wenn wir $N_i \geq 0$ Input-Neuronen haben, die Output-Neurone $j$ einen Threshold von $\Theta = -w_{j0}$ ist der net-Input (input des Neuronalen-Netzwerk) gegeben durch.

 $$ net_j = w_{j0}x_0 + w_{j1}x_1 + w_{j2}x_2 + \ldots w_{jN_i}x_{N_i} = \sum_{i=0}^{N_i}w_{ji}x_i $$

- $x_i$: Input des Input-Node $i$. (wobei $x_0 = +1$ fix ist)
- $w_{ji}$: Gewicht des Signals der Verknüpfung von Node $i$ zu Node $j$
- $w_{j0}$: Bias ($\Theta = -w_{j0}$ ist der Threshold von Node $j$)

Damit das Model nun auf dem richtigen Output-Node $j$ feuert müssen wir die **Activation Function* auf den net-Input anwenden.

$$ y_j = \sigma(net_j) = \sigma(\sum_{i=0}^{N_i}w_{ji}x_i) = \sigma(w_{j0}x_0 + w_{j1}x_1 + w_{j2}x_2 + \ldots w_{jN_i}x_{N_i}) $$

Dies kann auch in der Matrix-Form notiert werden.

$$ y_1  = \sigma(w_{10}x_0 + w_{11}x_1 + w_{12}x_2 + \ldots w_{1N_i}x_{N_i}) = \sigma(\sum_{i=0}^{N_i}w_{1i}x_i) $$

$$ y_2  = \sigma(w_{20}x_0 + w_{21}x_1 + w_{22}x_2 + \ldots w_{2N_i}x_{N_i}) = \sigma(\sum_{i=0}^{N_i}w_{2i}x_i) $$

$$ \begin{bmatrix}
y_1 \\
y_2
\end{bmatrix} = \sigma\begin{pmatrix}
\begin{bmatrix}
w_{10} w_{11} w_{12} \\
w_{20} w_{21} w_{22}
\end{bmatrix}
\begin{bmatrix}
x_0 \\
x_1 \\
x_2 \end{bmatrix}
\end{pmatrix} \quad \text{kurz} \quad \mathbf{y} = \sigma(\mathbf{Wx}) $$

## Aktivierungs Funktion





