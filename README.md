Vulkan Flocking: compute and shading in one pipeline!
======================

**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Project 6**

* Liang Peng
* Tested on: **54.0.2840.87 m (64-bit)** on
  Windows 10, i7-6700HQ @ 2.6GHz 8GB, GTX 960 (Personal Laptop)

## Overview

![](img/1.gif)

![](img/2.gif)

## Analysis

* Vulkan expects explicit descriptors for generating pipelines and commands because it needs to know how data such as vertex attributes (position, normal, texcoord, index, etc.) are stored in GPU memory and bound to uniforms and variables in shader code so that vs, cs, ps can get correct data to do computation or shading and pass over data to next stage in the pipeline.
* A situation in which processing algorithm is the same but input data sources are different, such as rendering a textured cube and a textured sphere, with different color maps.
* Problems to keep in mind when using multiple Vulkan queues
  * Synchronization. Use fences to make sure a queue is finished processing before other queues denpendent on it.
  * Race condition. Use mutex to avoid simultanious read/write operations at same address in same buffer.
* Avoiding the time and memory cost of copying output data of compute stage to input of render stage.

### Credits

* [Vulkan examples and demos](https://github.com/SaschaWillems/Vulkan) by [@SaschaWillems](https://github.com/SaschaWillems)
