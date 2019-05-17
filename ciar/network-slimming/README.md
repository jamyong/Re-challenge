
# Network Slimming

This directory contains the pytorch implementation for [network slimming](http://openaccess.thecvf.com/content_iccv_2017/html/Liu_Learning_Efficient_Convolutional_ICCV_2017_paper.html) (ICCV 2017).  



## Train with Sparsity

```shell
python main.py -sr --s 0.0001 --dataset cifar10 --arch vgg --depth 19
python main.py -sr --s 0.00001 --dataset cifar10 --arch resnet --depth 164
python main.py -sr --s 0.00001 --dataset cifar10 --arch densenet --depth 40
```
The model will be named `checkpoint.pth.tar`.
## Prune

```shell
python vggprune.py --dataset cifar10 --depth 19 --percent 0.7 --model [PATH TO THE MODEL] --save [DIRECTORY TO STORE RESULT]
python resprune.py --dataset cifar10 --depth 164 --percent 0.4 --model [PATH TO THE MODEL] --save [DIRECTORY TO STORE RESULT]
python denseprune.py --dataset cifar10 --depth 40 --percent 0.4 --model [PATH TO THE MODEL] --save [DIRECTORY TO STORE RESULT]
```
The pruned model will be named `pruned.pth.tar`.

## Fine-tune

```shell
python main_finetune.py --refine [PATH TO THE PRUNED MODEL] --dataset cifar10 --arch vgg --depth 19
python main_finetune.py --refine [PATH TO THE PRUNED MODEL] --dataset cifar10 --arch resnet --depth 164
python main_finetune.py --refine [PATH TO THE PRUNED MODEL] --dataset cifar10 --arch densenet --depth 40
```

## Scratch-E
```
python main_E.py --scratch [PATH TO THE PRUNED MODEL] --dataset cifar10 --arch vgg --depth 19
python main_E.py --scratch [PATH TO THE PRUNED MODEL] --dataset cifar10 --arch resnet --depth 164
python main_E.py --scratch [PATH TO THE PRUNED MODEL] --dataset cifar10 --arch densenet --depth 40
```

## Scratch-B
```
python main_B.py --scratch [PATH TO THE PRUNED MODEL] --dataset cifar10 --arch vgg --depth 19
python main_B.py --scratch [PATH TO THE PRUNED MODEL] --dataset cifar10 --arch resnet --depth 164
python main_B.py --scratch [PATH TO THE PRUNED MODEL] --dataset cifar10 --arch densenet --depth 40
```

