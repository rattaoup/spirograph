# Spirograph

This is a pytorch implementation for generating the Spirograph dataset as in Improving Transformation Invariance in Contrastive Representation Learning. The script `generate_spirograph.py` generates two tensor datasets call `spirograph_train.pth` and `spirograph_test.pth` of size 5000 and 2000 respectively. Each element of the dataset is a pair of (3,32,32) spirograph image and its 10 corresponding generative and transformations parameters. 

### Choosing generative and transformations parameters
The input of the class `DrawSpirograph` contains generative and transformations parameters that we can change. For example, the default setting is as follows

``` spirograph =  DrawSpirograph(['m', 'b', 'sigma', 'rfore'], ['h', 'rback', 'gfore', 'gback', 'bfore', 'bback'])```
Each parameter is sampled from a uniform distribution, m ~ U(2, 5), b ~ U(0.1, 1.1), h ~ U(0.5, 2.5), sigma ~ U(0.25, 1), foreground_colour ~ U(0.4, 1), background ~ U(0, 0.6).


### Differentiable generative process
The generating process of the spirograph dataset is fully differentiable. When we call a function `spirograph.dataset()` we draw only the generative parameters from the mentioned distribution. We also generate transformations parameters by calling `spirograph.sample_random_numbers()`. Now we can generate the spirograph image by passing these parameters to the function `spirograph(gen_param, trans_param)` to get the generated spirograph image(We start recording the computation graph now).
