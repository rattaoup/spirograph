# Spirograph

This is a PyTorch implementation for generating the Spirograph dataset as in (Improving Transformation Invariance in Contrastive Representation Learning)[https://arxiv.org/abs/2010.09515].

## Generating a Spirograph dataset
The script `generate_spirograph.py` generates two tensor datasets called `spirograph_train.pth` and `spirograph_test.pth` of size 5000 and 2000 respectively. Each element of the dataset is a pair of `(3,32,32)` Spirograph images and its 10 corresponding generative and nuisance transformation parameters. 

### Choosing generative and transformations parameters
The input of the class `DrawSpirograph` contains generative and transformations parameters that we can change. For example, the default setting is as follows

``` spirograph =  DrawSpirograph(['m', 'b', 'sigma', 'rfore'], ['h', 'rback', 'gfore', 'gback', 'bfore', 'bback'])```
Each parameter is sampled from a uniform distribution, `m ~ U(2, 5)`, `b ~ U(0.1, 1.1)`, `h ~ U(0.5, 2.5)`, `sigma ~ U(0.25, 1)`, `foreground_colour ~ U(0.4, 1)`, `background ~ U(0, 0.6)`.


### Differentiable generative process
The generating process of the Spirograph dataset is fully differentiable. When we call a function `spirograph.dataset()` we draw only the generative parameters from the mentioned distribution. We also generate transformations parameters by calling `spirograph.sample_random_numbers()`. Now we can generate the spirograph image by passing these parameters to the function `spirograph(gen_param, trans_param)` to get the generated spirograph image. The final step produces Spirograph sample images with pixel values that are fully differentiable in the input tensors.

## Citation
If you use the Spirograph, please consider citing the following paper
```@article{foster2020improving,
  title={Improving Transformation Invariance in Contrastive Representation Learning},
  author={Foster, Adam and Pukdee, Rattana and Rainforth, Tom},
  journal={arXiv preprint arXiv:2010.09515},
  year={2020}
}```
