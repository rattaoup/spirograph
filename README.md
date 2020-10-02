# Spirograph

The script generates and include 

We propose a new dataset that allows the separation of generative factors of interest from nuisance transformation factors and that is formed from a fully differentiable generative process. Our dataset is inspired by the beautiful spirograph patterns some of us drew as children, which are mathematically hypotrochoids given by the following equations

![eq1](https://github.com/rattaoup/spirograph/blob/main/plots/eq1.png)

To create an image dataset from such curves, we choose 40 equally spaced points $t_i$ with $t_1 = 0$ and $t_{40} = 2\pi$, giving a sequence of points $(x_1, y_1), ..., (x_{40}, y_{40})$ on the chosen hypotrochoid. For smoothing parameter $\sigma$, the pixel intensity at a point $(u, v)$ is given by

![eq2](https://github.com/rattaoup/spirograph/blob/main/plots/eq2.png)

For a grid of pixel, the intensity values are normalized so that the maximum intensity is equal to 1. Figure~\ref{fig:hypotrochoid}(b) shows the pixel intensity with $\sigma=0.5$. Finally, for a foreground colour with RGB values $(f_r,f_g,f_b)$ and background colour $(b_r,b_g,b_b)$, the final RGB values at a point $(u, v)$ is

![eq3](https://github.com/rattaoup/spirograph/blob/main/plots/eq3.png)

