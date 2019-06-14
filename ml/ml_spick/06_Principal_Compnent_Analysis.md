# Quiz 6 - Principal Component Analysis

## Correlation

$$ \mathbf{XX^T} = \begin{bmatrix}
\sum_{i=1}^n x_{1i}^2 \ \sum_{i=1}^n x_{1i} \times x_{2i} \ \sum_{i=1}^n x_{1i} \times x_{3i} \\
\sum_{i=1}^n x_{2i} \times x_{1i} \ \sum_{i=1}^n x_{2i}^2  \ \sum_{i=1}^n x_{2i} \times x_{3i} \\
\sum_{i=1}^n x_{3i} \times x_{1i} \ \sum_{i=1}^n x_{3i} \times x_{2i} \ \sum_{i=1}^n x_{3i}^2 
\end{bmatrix}$$

Wird zu $\mathbf{S_x}$

$$\mathbf{S_x} = \frac{1}{n-1}\mathbf{XX^T} = \begin{bmatrix}
Var(x_{1}) \ Cov(x_1,x_2) \ Cov(x_1, x_3) \\
Cov(x_2, x_1) \ Var(x_2) \ Cov(x_2, x_3) \\
Cov(x_3, x_1) \ Cov(x_3, x_2) \ Var(x_3)
\end{bmatrix}$$

$$ \mathbf{S_x} = \text{Kovarianz Matrix} $$

### Pearson Correlation

$$ p(X, Y) = \frac{Cov(X, Y)}{\sigma_X \sigma_Y}
\\
 \sigma_x = \sqrt{Var(x)} $$

## PCA

- PCA Main Components zeigen entlang der linearen Streuung.
- Positiv oder Negativ

