---
sidebar_position: 1
---

# Getting Started

Let's discover **VirtualCity in less than 5 minutes**.

## Install

Get started by **installing the exectuable file** for **[Windows](https://github.com/CSAILVision)** or **[Linux](https://github.com/CSAILVision)**.

Or **try VirtualCity immediately** with **[kswainws02.csail.mit.edu](http://visiongpu24.csail.mit.edu:5000/home)**.

### What you'll need

- [VirtualCity API](https://github.com/CSAILVision) 

- [Windows 11](https://www.microsoft.com/software-download/windows11), [Ubuntu 22.04 LTS](https://ubuntu.com/blog/tag/22-04-lts) or [MacOS Sonoma](https://www.apple.com/macos/sonoma-preview/)

- [AMD 5800X3D](https://www.amd.com/en/products/cpu/amd-ryzen-7-5800x3d), [Intel 12700k](https://www.intel.com/content/www/us/en/products/sku/134594/intel-core-i712700k-processor-25m-cache-up-to-5-00-ghz/specifications.html), [M2 Max](https://www.apple.com/newsroom/2023/01/apple-unveils-m2-pro-and-m2-max-next-generation-chips-for-next-level-workflows/) or better

- [AMD Radeon 6800xt](https://www.techpowerup.com/gpu-specs/radeon-rx-6800-xt.c3694), [Nvidia RTX 3090](https://www.techpowerup.com/gpu-specs/geforce-rtx-3090.c3622), [M2 Max](https://www.apple.com/newsroom/2023/01/apple-unveils-m2-pro-and-m2-max-next-generation-chips-for-next-level-workflows/) or better



## Run VirtualCity

Run the exectuable file by double clicking the file.

If you are running VirtualCity on a headless Ubuntu 22.04 LTS server, use the following bash command to run the exec:

```bash
./VirtualCity
```

The executable will allow you to control the environment using the keyboard and mouse, however of you want to programatically control the environment, you will need to setup the VirtualCity API.


## Intialize the VirtualCity API

Install the VirtualCity API:

```bash
pip install virtualcity
```
The command also installs all necessary dependencies you need to run the VirtualCity API.

To intialize the API:

```python
import virtualcity
```

When you import the virtualcity package, it will initialize the SocketIO server and will allow the SocketIO client in the executable file to automatically connect and enable complete control of the environment via the python interface.