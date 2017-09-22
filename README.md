# Paddle Benchmark
Inference benchmark of deep learning models implemented by paddlepaddle.

Environment
- MI 5, Android 7.0, Snapdragon 820 1.8GHz
- android-ndk-r13b
  - gcc version 4.9.x 20150123 (prerelease) (GCC)
  - Android clang version 3.8.256229  (based on LLVM 3.8.256229)

## Mobilenet
Benchmark for [Mobilenet](https://github.com/PaddlePaddle/Mobile/tree/master/flowers102/mobilenet) inference(input image 3x224x224).

**Currently, on MI 5 phones, single-threaded inference takes 127.032ms.**

| version | times(ms) | mem(MB) |optimization(accelerate) |
|---------|-----------|------------|--------------|
| d2258a4 | 321.682 | - | base |
| d2258a4 | 225.044 | - | merge bn(30%) |
| b45d020 | 148.201 | - | depthwise convolution(34.1%) |
| 0146e8b | 127.032 | - | clang compile(14.3%) |
| d59295f | 122.607 | 48 | neon::relu(4.5%) |

- The convolution layer of the **Base** version is achieved by `im2col + gemm` way.
- The **merge bn** optimization is merge the parameters of batch normalization layer's into the parameters of convolution layer.
- The [**depthwise convolution**](https://github.com/PaddlePaddle/Paddle/pull/3718) is a depthwise convolution optimization base on arm neon intrinsics.
- The **clang compile** is better than gcc compile.
