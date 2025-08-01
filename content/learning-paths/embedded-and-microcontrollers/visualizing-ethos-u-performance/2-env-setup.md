---
# User change
title: "Install ExecuTorch"

weight: 3

# Do not modify these elements
layout: "learningpathall"
---

In this section, you will prepare a development environment to compile a machine learning model.

## Introduction to ExecuTorch

ExecuTorch is a lightweight runtime designed for efficient execution of PyTorch models on resource-constrained devices. It enables machine learning inference on embedded and edge platforms, making it well-suited for Arm-based hardware. Since Arm processors are widely used in mobile, IoT, and embedded applications, ExecuTorch leverages Arm's efficient CPU architectures to deliver optimized performance while maintaining low power consumption. By integrating with Arm's compute libraries, it ensures smooth execution of AI workloads on Arm-powered devices, from Cortex-M microcontrollers to Cortex-A application processors.

## Install dependencies

These instructions have been tested on Ubuntu 22.04, 24.04, and on Windows Subsystem for Linux (WSL).

Python3 is required and comes installed with Ubuntu, but some additional packages are needed:

```bash
sudo apt update
sudo apt install python-is-python3 python3-dev python3-venv gcc g++ make -y
```

## Create a virtual environment

Create a Python virtual environment using `python venv`:

```console
python3 -m venv $HOME/executorch-venv
source $HOME/executorch-venv/bin/activate
```
The prompt of your terminal now has `(executorch)` as a prefix to indicate the virtual environment is active.


## Install Executorch

From within the Python virtual environment, run the commands below to download the ExecuTorch repository and install the required packages:

``` bash
cd $HOME
git clone https://github.com/pytorch/executorch.git
cd executorch
```

Run the commands below to set up the ExecuTorch internal dependencies:

```bash
git submodule sync
git submodule update --init --recursive
./install_executorch.sh
```

{{% notice Note %}}
If you run into an issue of `buck` running in a stale environment, reset it by running the following instructions:

```bash
ps aux | grep buck
pkill -f buck
```
{{% /notice %}}

After running the commands, `executorch` should be listed upon running `pip list`:

```bash
pip list | grep executorch
```

```output
executorch         0.8.0a0+92fb0cc
```

## Next Steps

Proceed to the next section to learn about and set up the virtualized hardware.
