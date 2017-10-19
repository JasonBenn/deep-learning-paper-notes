## [Residual Networks of Residual Networks: Multilevel Residual Networks](notes/residual-networks-of-residual-networks.md)

tl;dr: This is a hyperparameter search paper for ResNet architectures.

#### Thoughts:

* RoR-3-WRN58-4+SD, with 13.3M parameters, achieved 3.77% test error on CIFAR-10, 19.73% on CIFAR-100, and 1.59% on SVHN, all SOTA as of August 2016, according to this paper.

* Am I missing something here? They claim that their tweaked RoR-3-152 achieved 5.14 top-5 error on ImageNet, and that this was an improvement over the original ResNet (they list ResNets-152 in their own table as achieving 5.21%), but the original ResNet paper shows a 4.49% top-5 error on ImageNet. Perhaps the authors were unable to reproduce the original results.

* The 21-conv+1-fc is a helpful notation - first I've seen it.
