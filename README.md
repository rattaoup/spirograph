# Spirograph

This is a pytorch for generating the Spirograph dataset as in Improving Transformation Invariance in Contrastive Representation Learning. The script `generate_spirograph.py` generates two tensor datasets call `spirograph_train.pth` and `spirograph_test.pth` of size 5000 and 2000 respectively. Each element of the dataset is a pair of (3,32,32) spirograph image and its 10 corresponding generative and transformations parameters. 
