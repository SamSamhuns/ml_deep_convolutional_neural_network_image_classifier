# Deep Neural Network Classifier for the CIFAR-10 dataset

Implementation of a DNN for classifying images in the CIFAR-10 dataset

## Setup

```shell
$ python -m venv venv
$ pip install -r requirements.txt
```

To start a new Jupyter Notebook kernel:

```shell
$ ipython kernel install --name "local-venv" --user
```

To list all kernels:

```shell
$ jupyter kernelspec list
```

To remove a kernel:

```shell
$ jupyter kernelspec uninstall unwanted-kernel
```

### To setup jupyter notebook extensions

`pep8` package is required for auto-linting in the notebook.

```shell
$ pip install -e jupyter_contrib_nbextensions     # For pip
$ conda install -c conda-forge jupyter_contrib_nbextensions # For Anaconda
$ jupyter contrib nbextension install --user
$ pip install pep8                                # For pip, required for auto-linting
$ conda install -c anaconda pep8                  # For Anaconda, required for auto-linting
```

### To setup Jupyter Notebook themes

We use [dunovank/jupyter-themes](https://github.com/dunovank/jupyter-themes)

```shell
$ pip install --upgrade jupyterthemes             # For pip
$ conda install -c conda-forge jupyterthemes      # For Anaconda
$ jt -t chesterish -T -f roboto -fs 12 -cellw 95% # Sets theme to chesterish, enables toolbar, sets font to robot, sets fontsize to 12, set cell width to 95% of screen
```

## Data

We use the CIFAR-10 dataset:

![](img/cifar10.png)

## Preprocessing Data

We apply the following transformations to our training data:

-   Random Horizontal Flips

-   Normalization of the images to a `[-1,1]` range

### Optimizer used

ADAM Optimizer

#### Loss Function

![](img/cross_entropy_loss.png)

## Neural Network

Our DNN is inspired by the Google Le Net architecture

![](img/gnet.png)

We use a modified Google Le Net architecture

![](img/modified_gnet.jpg)

We use the `Inception` blocks from google in our network

|          Naive Block         |     Improved Block     |
| :--------------------------: | :--------------------: |
| ![](img/inception_naive.png) | ![](img/inception.png) |

## Results

After 1500 epochs with the following hyper-parameters and repeated save and load trainings.

For the trained model, we achieve an accuracy of `84.3 %`

And when a new model is trained for 100 epochs only, we get a low accuracy of `9.4 %` that is no better than random guessing.

### Loss curve for training of 100 epochs on an untrained model

![](img/converging_loss.png)

### Loss curve for an already converged model

![](img/non_converging_loss.png)

## Acknowledgements

-   Learning Multiple Layers of Features from Tiny Images, Alex Krizhevsky, 2009.

-   Szegedy, Christian, Wei Liu, Yangqing Jia, Pierre Sermanet, Scott Reed, Dragomir Anguelov, Dumitru Erhan, Vincent Vanhoucke, and Andrew Rabinovich. “Going Deeper with Convolutions.” ArXiv:1409.4842 [Cs], September 16, 2014. <http://arxiv.org/abs/1409.4842>.
