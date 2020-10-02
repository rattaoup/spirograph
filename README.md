# Spirograph

We propose a new dataset that allows the separation of generative factors of interest from nuisance transformation factors and that is formed from a fully differentiable generative process. Our dataset is inspired by the beautiful spirograph patterns some of us drew as children, which are mathematically hypotrochoids given by the following equations

![eq1](https://github.com/rattaoup/spirograph/blob/main/plots/eq1.png)

To create an image dataset from such curves, we choose 40 equally spaced points `$t_i$` with `$t_1 = 0$ and $t_{40} = 2\pi$`, giving a sequence of points `$(x_1, y_1), ..., (x_{40}, y_{40})$` on the chosen hypotrochoid. For smoothing parameter `$\sigma$`, the pixel intensity at a point `$(u, v)$` is given by

![eq2](https://github.com/rattaoup/spirograph/blob/main/plots/eq2.png)

For a grid of pixel, the intensity values are normalized so that the maximum intensity is equal to 1. Figure~\ref{fig:hypotrochoid}(b) shows the pixel intensity with $\sigma=0.5$. Finally, for a foreground colour with RGB values $(f_r,f_g,f_b)$ and background colour $(b_r,b_g,b_b)$, the final RGB values at a point $(u, v)$ is

![eq3](https://github.com/rattaoup/spirograph/blob/main/plots/eq3.png)

The Spirograph sample is fully specified by the parameters $m, b, h, \sigma, f_r,f_g,f_b,b_r,b_g,b_b$. In our experiments, we treat $m, b, \sigma,f_r$ as parameters of interest. We treat $h$ and the remaining colour parameters as nuisance parameters. That is, we take $\rvx = (m, b, \sigma,f_r)$ and $\rvalpha = (h, f_g,f_b,b_r,b_g,b_b)$ and the transformation $\rvt(\rvx,\rvalpha)$ is the full generative process described above. There are no additional parameters $\rvbeta$ for this dataset. Figure~\ref{fig:spirograph-illustration} shows two sets of four samples from the Spirograph dataset, in each set the generative factors of interest are fixed and the nuisance parameters are varied. In general for the Spirograph dataset, the distinction between generative factors of interest and nuisance parameters can be changed to attempt to learn different aspects of the data. The transformation $\rvt$ is fully differentiable, meaning that we can apply gradient penalization to all the nuisance parameters of the generative process.
In our experiments, we took the following distributions to sample random values of the parameters: $m \sim U(2, 5), b \sim U(0.1, 1.1), h \sim U(0.5, 2.5), \sigma \sim U(0.25, 1), f_r, f_g,f_b \sim U(0.4, 1), b_r,b_g,b_b \sim U(0, 0.6)$.
