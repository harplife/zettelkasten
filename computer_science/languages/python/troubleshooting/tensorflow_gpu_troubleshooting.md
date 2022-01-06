---
alias: [TF GPU Errors, TF GPU Troubleshooting]
tags: [python, gpu, library, troubleshooting, machine_learning, computer_science, errors]
status: ongoing
edited: 2022-01-06
---

# Tensorflow GPU Troubleshooting
Collection of Tensorflow GPU erros & solutions.

## Tensorflow GPU Installation won't install GPU version
Date of Error: 2022/01/06

Problem: 
`install tensorflow-gpu` won't actually install tensorlfow GPU version (also fails to detect GPU)

Environment:
- Windows 10 Pro
- Anaconda 3 (`conda` package manager)
- Python 3.8
- CUDA 10.1 & CudNN 7.6 (manually installed on PC)

Solution:
`conda install tensorflow-gpu=2.3 tensorflow=2.3=mkl_py38h1fcfbd6_0` 로 tensorflow 설치.

Explanation:
Tensorflow-gpu not detecting GPU seems to be [an ongoing problem](https://github.com/ContinuumIO/anaconda-issues/issues/12194) (as of 2021/01/06).
The cause is the installation engine (conda) selecting a faulty tensorflow build during installation. The workaround is to explicitly specify the corrct tensorflow build.

The post says it's specific to TF version 2.3, but this needs to be verified by installing other TF GPU versions.