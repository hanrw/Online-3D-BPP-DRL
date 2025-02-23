# Online 3D Bin Packing with Constrained Deep Reinforcement Learning

![teaser](pictures/state_architecture.png)

## Introduction
```
This repository contains the implementation of paper [Online 3D Bin Packing with Constrained Deep Reinforcement Learning](https://arxiv.org/pdf/2006.14978.pdf).

Any contribution is welcome! If you have any recurring problems, please contact me at alexfrom0815@gmail.com.
```

## Install

```
To make this project work, there are two things you should do:
* Install python packages in 'requirements.py' (by 'pip install -r requirements.txt').
* Register our binpacking environment(envs/Bpp-v0) in your gym (discussed in https://github.com/openai/gym/issues/626).
```

## Run
We provide an unified interface in 'main.py'. There are examples of running our project.

For training：
```
Example: Train a new model on sequences generated randomly.
You can run 'python main.py --mode train --load-model --use-cuda --item-seq sample'.
It will take about one day to get a model with satisfying performance.

You can run 'python main.py --help' for some information of common parameters.
There are many other parameters of our project in 'config.py', all of them are given default values.You can change it if you like.
```

For test:
```
Example:
If you want to test a model trained on sequences generated by CUT-2 Algorithm(get more details in our article).
You can run 'python main.py --mode test --load-model --use-cuda --data-name cut_2.pt --load-name default_cut_2.pt'.

If you want see how the model work in lookahead setting,
You can run 'python main.py --mode test --load-model --use-cuda --data-name cut_2.pt --load-name default_cut_2.pt --preview x', x is the lookahead number.

Codes of user-study application, multi-bin algorithm, MCTS for comparison are also provided,
Please check 'user_study/', 'multi_bin/', 'MCTS/' for details.
```

## Tips
```
* Different input state sizes need different kinds of CNN for encoding, you can adjust the network architecture in ./acktr/model.py to satisfy your needs. 

* Predicted mask is mainly for reducing MCTS computing costs. If you only need BPP-1 model, you can replace predicted mask with ground-truth mask during the training and it will be easy for training.

* If you relax the constraint of stability rules, you may get a better result, but it may be dangerous in practice.

* The computing overhead of our implementation is sensitive to the length of network layer, you should aviod a large network layer appears in your network architecture. 

* Bin packing problem's difficulty is related to its item set. The trained model's performance is also affected by it.
```

## Statement
```
Hang Zhao and Qijin She are co-authors of this repository.

Some codes are modified from opensource project 'pytorch-a2c-ppo-acktr-gail' (https://github.com/ikostrikov/pytorch-a2c-ppo-acktr-gail).
```

## License
```
Note that this source code is released only for academic use. Please do not use it for commercial purpose without authorization of the authors. The method is being patent protected. For commercial use, please contact Kai Xu (kevin.kai.xu@gmail.com).
```

## Citation

If you are interested, please cite the following paper:

```shell
@article{zhao2020online,
  title={Online 3D Bin Packing with Constrained Deep Reinforcement Learning},
  author={Zhao, Hang and She, Qijin and Zhu, Chenyang and Yang, Yin and Xu, Kai},
  journal={arXiv preprint arXiv:2006.14978},
  year={2020}
}
```
