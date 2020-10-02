# Spirograph

This is a pytorch implementation for generating the Spirograph dataset as in Improving Transformation Invariance in Contrastive Representation Learning. The script `generate_spirograph.py` generates two tensor datasets call `spirograph_train.pth` and `spirograph_test.pth` of size 5000 and 2000 respectively. Each element of the dataset is a pair of (3,32,32) spirograph image and its 10 corresponding generative and transformations parameters. 

### Choosing generative and transformations parameters
The input of the class `DrawSpirograph` contains generative and transformations parameters respectively. For example, the default setting is as follows
``` spirograph =  DrawSpirograph(['m', 'b', 'sigma', 'rfore'], ['h', 'rback', 'gfore', 'gback', 'bfore', 'bback'])```
