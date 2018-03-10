# CUDA Samples

Samples for CUDA Developers which demonstrates features in CUDA Toolkit. This version supports [CUDA Toolkit 9.2](https://developer.nvidia.com/cuda-downloads).

## Release Notes

This section describes the release notes for the CUDA Samples on GitHub only.

### CUDA 9.2

This is the first release of CUDA Samples on GitHub:
*  Added `vectorAdd_nvrtc`. Demonstrates runtime compilation library using NVRTC of a simple vectorAdd kernel.
*  Added `warpAggregatedAtomicsCG`. Demonstrates warp aggregated atomics using Cooperative Groups.
*  Added `deviceQuery`. Enumerates the properties of the CUDA devices present in the system.
*  Added `matrixMul`. Demonstrates a matrix multiplication using shared memory through tiled approach.
*  Added `matrixMulDrv`. Demonstrates a matrix multiplication using shared memory through tiled approach, uses CUDA Driver API.
*  Added `cudaTensorCoreGemm`. Demonstrates a GEMM computation using the Warp Matrix Multiply and Accumulate (WMMA) API introduced in CUDA 9, as well as the new Tensor Cores introduced in the Volta chip family.
*  Added `simpleVoteIntrinsics` which uses *_sync equivalent of the vote intrinsics _any, _all added since CUDA 9.0.
*  Added `shfl_scan` which uses *_sync equivalent of the shfl intrinsics added since CUDA 9.0.
*  Added `conjugateGradientMultiBlockCG`. Demonstrates a conjugate gradient solver on GPU using Multi Block Cooperative Groups.
*  Added `conjugateGradientMultiDeviceCG`. Demonstrates a conjugate gradient solver on multiple GPUs using Multi Device Cooperative Groups, also uses unified memory prefetching and usage hints APIs.
*  Added `simpleCUBLAS`. Demonstrates how perform GEMM operations using CUBLAS library.
*  Added `simpleCUFFT`. Demonstrates how perform FFT operations using CUFFT library.

## Getting Started

### Prerequisites

Download and install the [CUDA Toolkit 9.2](https://developer.nvidia.com/cuda-downloads) for your corresponding platform.
For system requirements and installation instructions of cuda toolkit, please refer to the [Linux Installation Guide](http://docs.nvidia.com/cuda/cuda-installation-guide-linux/), the [Windows Installation Guide](http://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/index.html), and the [Mac Installation Guide](http://docs.nvidia.com/cuda/cuda-installation-guide-mac-os-x/index.html).

### Getting the CUDA Samples

Using git clone the repository of CUDA Samples using the command below.
```
git clone <GIT_REPO_CLONE_LINK>
```

Without using git the easiest way to use these samples is to download the zip file containing the current version by clicking the "Download ZIP" button on the repo page. You can then unzip the entire archive and use the samples.

## Building CUDA Samples

### Windows

The Windows samples are built using the Visual Studio IDE. Solution files (.sln) are provided for each supported version of Visual Studio, using the format:
```
*_vs<version>.sln - for Visual Studio <version>
```
Complete samples solution files exist at parent directory of the repo:

Each individual sample has its own set of solution files at:
`<CUDA_SAMPLES_REPO>\Samples\<sample_dir>\`

To build/examine all the samples at once, the complete solution files should be used. To build/examine a single sample, the individual sample solution files should be used.
> **Note:** Some samples require that the Microsoft DirectX SDK (June 2010 or newer) be installed and that the VC++ directory paths are properly set up (**Tools > Options...**). Check [DirectX Dependencies](#directx) section for details."

### Linux
The Linux samples are built using makefiles. To use the makefiles, change the current directory to the sample directory you wish to build, and run make:
```
$ cd <sample_dir>
$ make
```
The samples makefiles can take advantage of certain options:
*  **TARGET_ARCH=<arch>** - cross-compile targeting a specific architecture. Allowed architectures are x86_64, ppc64le, armv7l, aarch64.
    By default, TARGET_ARCH is set to HOST_ARCH. On a x86_64 machine, not setting TARGET_ARCH is the equivalent of setting TARGET_ARCH=x86_64.<br/>
`$ make TARGET_ARCH=x86_64` <br/> `$ make TARGET_ARCH=ppc64le` <br/> `$ make TARGET_ARCH=armv7l` <br/> `$ make TARGET_ARCH=aarch64` <br/>
    See [here](http://docs.nvidia.com/cuda/cuda-samples/index.html#cross-samples) for more details on cross platform compilation of cuda samples.
*   **dbg=1** - build with debug symbols
    ```
    $ make dbg=1
    ```
*   **SMS="A B ..."** - override the SM architectures for which the sample will be built, where `"A B ..."` is a space-delimited list of SM architectures. For example, to generate SASS for SM 50 and SM 60, use `SMS="50 60"`.
    ```
    $ make SMS="50 60"
    ```

*  **HOST_COMPILER=<host_compiler>** - override the default g++ host compiler. See the [Linux Installation Guide](http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#system-requirements) for a list of supported host compilers.
    ```
    $ make HOST_COMPILER=g++
    ```

### Mac
The Mac samples are built using makefiles. To use the makefiles, change directory into the sample directory you wish to build, and run make:
```
$ cd <sample_dir>
$ make
```

The samples makefiles can take advantage of certain options:

*  **dbg=1** - build with debug symbols
    ```
    $ make dbg=1
    ```

*  **SMS="A B ..."** - override the SM architectures for which the sample will be built, where "A B ..." is a space-delimited list of SM architectures. For example, to generate SASS for SM 50 and SM 60, use SMS="50 60".
    ```
    $ make SMS="A B ..."
    ```

*  **HOST_COMPILER=<host_compiler>** - override the default clang host compiler. See the [Mac Installation Guide](http://docs.nvidia.com/cuda/cuda-installation-guide-mac-os-x/index.html#system-requirements) for a list of supported host compilers.
    ```
    $ make HOST_COMPILER=clang
    ```

## Samples list

### Samples by OS

#### Linux
**[cudaTensorCoreGemm](./Samples/cudaTensorCoreGemm)** | **[conjugateGradientMultiBlockCG](./Samples/conjugateGradientMultiBlockCG)** | **[warpAggregatedAtomicsCG](./Samples/warpAggregatedAtomicsCG)** | **[matrixMulDrv](./Samples/matrixMulDrv)** |
---|---|---|---|
**[vectorAdd_nvrtc](./Samples/vectorAdd_nvrtc)** | **[simpleCUFFT](./Samples/simpleCUFFT)** | **[simpleCUBLAS](./Samples/simpleCUBLAS)** | **[conjugateGradientMultiDeviceCG](./Samples/conjugateGradientMultiDeviceCG)** |
**[matrixMul](./Samples/matrixMul)** | **[shfl_scan](./Samples/shfl_scan)** | **[simpleVoteIntrinsics](./Samples/simpleVoteIntrinsics)** | **[deviceQuery](./Samples/deviceQuery)** |

#### Windows
**[cudaTensorCoreGemm](./Samples/cudaTensorCoreGemm)** | **[conjugateGradientMultiBlockCG](./Samples/conjugateGradientMultiBlockCG)** | **[warpAggregatedAtomicsCG](./Samples/warpAggregatedAtomicsCG)** | **[matrixMulDrv](./Samples/matrixMulDrv)** |
---|---|---|---|
**[vectorAdd_nvrtc](./Samples/vectorAdd_nvrtc)** | **[simpleCUFFT](./Samples/simpleCUFFT)** | **[simpleCUBLAS](./Samples/simpleCUBLAS)** | **[conjugateGradientMultiDeviceCG](./Samples/conjugateGradientMultiDeviceCG)** |
**[matrixMul](./Samples/matrixMul)** | **[shfl_scan](./Samples/shfl_scan)** | **[simpleVoteIntrinsics](./Samples/simpleVoteIntrinsics)** | **[deviceQuery](./Samples/deviceQuery)** |

#### Mac OSX
**[warpAggregatedAtomicsCG](./Samples/warpAggregatedAtomicsCG)** | **[matrixMulDrv](./Samples/matrixMulDrv)** | **[vectorAdd_nvrtc](./Samples/vectorAdd_nvrtc)** | **[simpleCUFFT](./Samples/simpleCUFFT)** |
---|---|---|---|
**[simpleCUBLAS](./Samples/simpleCUBLAS)** | **[matrixMul](./Samples/matrixMul)** | **[shfl_scan](./Samples/shfl_scan)** | **[simpleVoteIntrinsics](./Samples/simpleVoteIntrinsics)** |
**[deviceQuery](./Samples/deviceQuery)** |

## Dependencies

Some CUDA Samples rely on third-party applications and/or libraries, or features provided by the CUDA Toolkit and Driver, to either build or execute. These dependencies are listed below.

If a sample has a third-party dependency that is available on the system, but is not installed, the sample will waive itself at build time.

Each sample's dependencies are listed in its README's Dependencies section.

### Third-Party Dependencies

These third-party dependencies are required by some CUDA samples. If available, these dependencies are either installed on your system automatically, or are installable via your system's package manager (Linux) or a third-party website.

#### FreeImage

FreeImage is an open source imaging library. FreeImage can usually be installed on Linux using your distribution's package manager system. FreeImage can also be downloaded from the [FreeImage website](http://freeimage.sourceforge.net/). FreeImage is also redistributed with the CUDA Samples.

#### Message Passing Interface

MPI (Message Passing Interface) is an API for communicating data between distributed processes. A MPI compiler can be installed using your Linux distribution's package manager system. It is also available on some online resources, such as [Open MPI](http://www.open-mpi.org/). On Windows, to build and run MPI-CUDA applications one can install [MS-MPI SDK](https://msdn.microsoft.com/en-us/library/bb524831(v=vs.85).aspx).

#### Only 64-Bit

Some samples can only be run on a 64-bit operating system.

#### DirectX

DirectX is a collection of APIs designed to allow development of multimedia applications on Microsoft platforms. For Microsoft platforms, NVIDIA's CUDA Driver supports DirectX. Several CUDA Samples for Windows demonstrates CUDA-DirectX Interoperability, for building such samples one needs to install [Direct X SDK (June 2010 or newer)](http://www.microsoft.com/en-us/download/details.aspx?id=6812) , this is required to be installed on Windows 7, Windows 10 and Windows Server 2008, Other Windows OSes do not need to explicitly install the DirectX SDK.

#### OpenGL

OpenGL is a graphics library used for 2D and 3D rendering. On systems which support OpenGL, NVIDIA's OpenGL implementation is provided with the CUDA Driver.

#### OpenGL ES

OpenGL ES is an embedded systems graphics library used for 2D and 3D rendering. On systems which support OpenGL ES, NVIDIA's OpenGL ES implementation is provided with the CUDA Driver.

#### OpenMP

OpenMP is an API for multiprocessing programming. OpenMP can be installed using your Linux distribution's package manager system. It usually comes preinstalled with GCC. It can also be found at the [OpenMP website](http://openmp.org/).

#### Screen

Screen is a windowing system found on the QNX operating system. Screen is usually found as part of the root filesystem.

#### X11

X11 is a windowing system commonly found on *-nix style operating systems. X11 can be installed using your Linux distribution's package manager, and comes preinstalled on Mac OS X systems.

#### EGL

EGL is an interface between Khronos rendering APIs (such as OpenGL, OpenGL ES or OpenVG) and the underlying native platform windowing system.

#### EGLOutput

EGLOutput is a set of EGL extensions which allow EGL to render directly to the display.

#### EGLSync

EGLSync is a set of EGL extensions which provides sync objects that are synchronization primitive, representing events whose completion can be tested or waited upon.

### CUDA Features

These CUDA features are needed by some CUDA samples. They are provided by either the CUDA Toolkit or CUDA Driver. Some features may not be available on your system.

#### CUFFT Callback Routines

CUFFT Callback Routines are user-supplied kernel routines that CUFFT will call when loading or storing data. These callback routines are only available on Linux x86_64 and ppc64le systems.

#### CUDA Dynamic Paralellism

CDP (CUDA Dynamic Paralellism) allows kernels to be launched from threads running on the GPU. CDP is only available on GPUs with SM architecture of 3.5 or above.

#### Multi-block Cooperative Groups

Multi Block Cooperative Groups(MBCG) extends Cooperative Groups and the CUDA programming model to express inter-thread-block synchronization. MBCG is available on GPUs with Pascal and higher architecture on Linux systems.

#### CUBLAS

CUBLAS (CUDA Basic Linear Algebra Subroutines) is a GPU-accelerated version of the BLAS library.

#### CUDA Interprocess Communication

IPC (Interprocess Communication) allows processes to share device pointers. IPC is only available on Linux x86_64 and ppc64le systems.

#### CUFFT

CUFFT (CUDA Fast Fourier Transform) is a GPU-accelerated FFT library.

#### CURAND

CURAND (CUDA Random Number Generation) is a GPU-accelerated RNG library.

#### CUSPARSE

CUSPARSE (CUDA Sparse Matrix) provides linear algebra subroutines used for sparse matrix calculations.

#### CUSOLVER

CUSOLVER library is a high-level package based on the CUBLAS and CUSPARSE libraries. It combines three separate libraries under a single umbrella, each of which can be used independently or in concert with other toolkit libraries. The intent ofCUSOLVER is to provide useful LAPACK-like features, such as common matrix factorization and triangular solve routines for dense matrices, a sparse least-squares solver and an eigenvalue solver. In addition cuSolver provides a new refactorization library useful for solving sequences of matrices with a shared sparsity pattern.

#### NPP

NPP (NVIDIA Performance Primitives) provides GPU-accelerated image, video, and signal processing functions.

#### NVGRAPH

NVGRAPH is a GPU-accelerated graph analytics library..

#### NVRTC

NVRTC (CUDA RunTime Compilation) is a runtime compilation library for CUDA C++.

#### NVCUVID

NVCUVID (NVIDIA CUDA Video Decoder) provides GPU-accelerated video decoding capabilities.

#### Stream Priorities

Stream Priorities allows the creation of streams with specified priorities. Stream Priorities is only available on GPUs with SM architecture of 3.5 or above.

#### Unified Virtual Memory

UVM (Unified Virtual Memory) enables memory that can be accessed by both the CPU and GPU without explicit copying between the two. UVM is only available on Linux and Windows systems.

#### 16-bit Floating Point

FP16 is a 16-bit floating-point format. One bit is used for the sign, five bits for the exponent, and ten bits for the mantissa.

#### C++11 CUDA

NVCC support of [C++11 features](https://en.wikipedia.org/wiki/C++11).

## Contributors Guide

We welcome your input on issues and suggestions for new samples. At this time we are not accepting contributions from the public, check back here as we evolve our contribution model.

We use Google C++ Style Guide for all the sources https://google.github.io/styleguide/cppguide.html

## Frequently Asked Questions

Answers to frequently asked questions about CUDA can be found at http://developer.nvidia.com/cuda-faq and in the [CUDA Toolkit Release Notes](http://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html).

