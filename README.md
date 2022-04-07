## An example BIDS App using Pytorch, CUDA and cuDNN for Deep Learning (template repository)
Every BIDS App needs to follow a minimal set of command arguments common across
all of the Apps. This allows users and developers to easily use and integrate
BIDS Apps with their environment.

This is a minimalist example of a BIDS App consisting of a Dockerfile and a simple
entry point script (written in this case in Python) accepting the standard BIDS
Apps command line arguments. This repository can be used as a template for new BIDS Apps **for Deep Learning applications**.

For more information about the specification of BIDS Apps see [here](https://docs.google.com/document/d/1E1Wi5ONvOVVnGhj21S1bmJJ4kyHFT7tkxnV3C23sjIE/).

### Description
This code can be used as a template to code a BIDS app for Deep Learning applications.

Be sure your machine is equipped with an Nvidia graphics card compatible with CUDA and cuDNN.

**First,** you will have to install [Docker](https://docs.docker.com/get-docker/) and the **Nvidia container toolkit** by following these instructions:
- Linux system: https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html
- Windows system: use WSL 2 : https://developer.nvidia.com/cuda/wsl https://docs.nvidia.com/cuda/wsl-user-guide/index.html#known-limitations-for-linux-cuda-apps Limitations: With the NVIDIA Container Toolkit for Docker 19.03, only --gpus all is supported. On multi-GPU systems it is not possible to filter for specific GPU devices by using specific index numbers to enumerate GPUs.

This template uses CUDA 11.1 and cuDNN 8. Be sure it is compatible with your machine and the packages and dependencies you use.

Otherwise, you may want to change the base in the Dockerfile by [another version](https://hub.docker.com/r/nvidia/cuda/tags?page=1).

You may want to change the package versions in the requirements.txt file too.

Next, try to run :
```
docker run -it --rm --gpus all -v /path/to/BIDS_data/:/data:ro -v /path/to/outdir/:/outdir garciaml/bids-pytorch-cuda /data /outdir participant
```

This should return **True**, showing that CUDA is available in the Docker container you launched. 

If it returns False, verify that you  put the *--gpus* flag when launching the command.
You can also verify that your installation of the Nvidia container toolkit is well done (see the official doc for [GPU](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) or [CPU](https://docs.nvidia.com/cuda/wsl-user-guide/index.html#ch01-introduction)), and that you chose compatible base and dependencies.

### How to report errors
You can directly raise issues with the code here: https://github.com/garciaml/BIDS_Pytorch_CUDA_example/issues
For any question or suggestion you are welcome to use the [bids-pytorch-cuda google group](https://groups.google.com/g/bids-pytorch-cuda).

### Citation
The BIDS-Pytorch-CUDA template was inpired from the version of BrainQCNet for GPU https://github.com/garciaml/BrainQCNet_GPU.

When using the BIDS-Pytorch-CUDA template, please include the following citation:

*BrainQCNet: a Deep Learning attention-based model for multi-scale detection of artifacts in brain structural MRI scans*, Melanie Garcia, Nico Dosenbach, Clare Kelly. bioRxiv 2022.03.11.483983; doi: https://doi.org/10.1101/2022.03.11.483983
