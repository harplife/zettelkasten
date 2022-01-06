---
alias: [TF GPU Set Up, TF GPU Installation]
tags: [python, gpu, library, guide, HOW-TO, machine_learning, computer_science]
status: ongoing
edited: 2022-01-06
---

# Tensorflow GPU Set Up
Setting up Tensorflow GPU is strangely difficult. There is a whole shenanigan you have to deal with in order to make it work without a error or a warning.

## For Windows 10 (as of 2022/01/06)
1. Install latest GPU Nvidia Drivers
2. Install CUDA Toolkit ([make sure the versions match](https://www.tensorflow.org/install/source#gpu))
3. Install CudNN (again, the versions must match)
4. `conda install cuda -c nvidia` <-- apparently you can install CUDA Toolkit with Conda. Not sure if this makes Steps 2&3 obsolete.
5. Install Tensorflow-GPU (check [[tensorflow_gpu_troubleshooting#Tensorflow GPU Installation won't install GPU version]])

Steps _MUST_ be in order.