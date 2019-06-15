# Beispielaufgabe - Lineare Regression (Disk I/0 und CPU-Time)

The number of disk I/O’s and processor times of 7 programs were measured as **(14, 2), (16, 5), (27, 7), (42, 9), (83, 20), (50, 13), (39, 10)**. Compute the **regression line**, the **coefficient of determination R2**, the **Pearson correlation coefficient r** and the **Confidence Interval**.

$$
\begin{aligned}
    &X = [14, 16, 27, 42, 83, 50, 39] = \text{Disk I/O} \\
    &Y = [2, 5, 7, 9, 20, 13, 10] = \text{CPU-Time}\\
    \\
    &\bar{x} = \frac{1}{n} \sum_{i=1}^n x^{(i)} = \frac{1}{7} (14+16+27+42+83+50+39) = 38.7143 \\
    &\bar{y} = \frac{1}{n} \sum_{i=1}^n y^{(i)} = \frac{1}{7} (2+5+7+9+20+13+10) = 9.42857 \\
    \\
    &\theta_1 = \frac{\sum_{i=1}^n (x^{(i)} - \bar{x})(y^{(i)} - \bar{y})}
        {\sum_{i=1}^n (x^{(i)} - \bar{x})^2} = \frac{\sum_{i=1}^7 (x^{(i)} - 38.7143)(y^{(i)} - 9.42857)}{\sum_{i=1}^7 (x^{(i)} - 38.7143)^2} = 0.243757 \\
    &\theta_0 = \bar{y} - \theta_1 \cdot \bar{x} = 9.42857 - 0.243757 \cdot 38.7143 = -0.0083 \\
    \\
    &y = \hat{y} = \theta_0 + \theta_1 x = \underline{\underline{-0.0083 + 0.2438x}} \\
    \\
    &SSE = \sum_{i=1}^n (y^{(i)} - \hat{y}^{(i)})^2 = \sum_{i=1}^7 (y^{(i)} - (-0.0083 + 0.2438 \cdot x^{(i)}))^2 = 5.86891 \\
    &SSR = \sum_{i=1}^n (\hat{y}^{(i)} - \bar{y})^2 = \sum_{i=1}^7 ((-0.0083 + 0.2438 \cdot x^{(i)}) - 9.42857)^2 = 199.917 \\
    &SST =  SSE + SSR = 5.86891 + 199.917 = 205.786 \\
    \\
    &R^2 = 1 - \frac{SSE}{SST} = 1 - \frac{5.86891}{205.786} = \underline{\underline{0.9715}} \rightarrow \text{Regression erklährt 97\% der Variation} \\
    \\
    &r = \frac{\sum_{i=1}^n (x^{(i)} - \bar{x}) (y^{(i)} - \bar{y})}
        {\sqrt{\sum_{i=1}^n (x^{(i)} - \bar{x})^2}
        \sqrt{\sum_{i=1}^n (y^{(i)} - \bar{y})^2}}
        = \frac{\sum_{i=1}^7 (x^{(i)} - 38.7143) (y^{(i)} - 9.42857)}
        {\sqrt{\sum_{i=1}^7 (x^{(i)} - 38.7143)^2}
        \sqrt{\sum_{i=1}^7 (y^{(i)} - 9.42857)^2}} = \underline{\underline{0.9856}} \\
    \\
    &MSE = \frac{SSE}{n-2} = \frac{1}{n-2}\sum_{i=1}^{n}(y_{i}-\hat{y}^{}_{i})^2 = \frac{5.86891}{7-2} = 1.17378 \\
    \\
    &s_{\theta_{0}} = \sqrt{MSE} \cdot \sqrt{\frac{1}{n} + \frac{\bar{x}^2}{\sum_{i=1}^{n}{(x^{(i)}-\bar{x})^2}}} = \sqrt{1.17378} \cdot \sqrt{\frac{1}{7} + \frac{38.7143^2}{\sum_{i=1}^{7}{(x^{(i)}-38.7143)^2}}} = 0.831106 \\
    &s_{\theta_{1}} = \sqrt{MSE}\cdot \sqrt{\frac{1}{\sum_{i=1}^{n}{(x^{(i)}-\bar{x})^2}}} = \sqrt{1.17378}\cdot \sqrt{\frac{1}{\sum_{i=1}^{7}{(x^{(i)}-38.7143)^2}}} = 0.018681 \\
    \\
    &t = t[0.95; 7 - 2] = 2.57 \rightarrow \text{aus Tabelle gelesen} \\
    \\
    &\text{Intervall }\theta_0 = [\theta_0 - t \cdot s_{\theta_0}; \theta_0 + t \cdot s_{\theta_0}] = [-0.0083 - 2.57 \cdot 0.831106; -0.0083 + 2.57 \cdot 0.831106] \\
    &= \underline{\underline{[-2.14424; 2.12764]}} \\
    \\
    &\text{Intervall }\theta_1 = [\theta_1 - t \cdot s_{\theta_1}; \theta_1 + t \cdot s_{\theta_1}] = [0.2438 - 2.57 \cdot 0.018681; 0.2438 + 2.57 \cdot 0.018681] \\
    &= \underline{\underline{[0.19579; 0.29181]}}
\end{aligned}
$$
