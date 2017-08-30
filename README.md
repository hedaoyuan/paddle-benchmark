# Paddle Benchmark
Inference benchmark of deep learning models implemented by paddlepaddle.

## Mobilenet
Benchmark for [Mobilenet](https://github.com/PaddlePaddle/Mobile/tree/master/flowers102/mobilenet) inference.

Environment: MI 5, Android 7.0, Snapdragon 820 1.8GHz, gcc version 4.9.x

- The convolution layer of the **Base** version is achieved by `im2col + gemm` way.
- The depthwise convolution layer of the [**Depthwise** version](https://github.com/PaddlePaddle/Paddle/pull/3718) is optimized. The inference time of the mobilenet can be reduced from 219.367ms to 147.953ms.

| Layer | Base(ms) | Depthwise(ms) |
| ----- |--------- | ----------------- |
| image | 0.01 | 0.008 |
| conv_0 | 6.551 | 6.716 |
| conv_1 | 16.77 | 3.366 |
| conv_2 | 11.096 | 10.641 |
| conv_3 | 9.073 | 2.902 |
| conv_4 | 7.147 | 7.175 |
| conv_5 | 17.08 | 3.865 |
| conv_6 | 10.908 | 11.017 |
| conv_7 | 4.925 | 1.443 |
| conv_8 | 5.595 | 5.562 |
| conv_9 | 9.134 | 1.729 |
| conv_10 | 10.095 | 10.083 |
| conv_11 | 2.374 | 0.834 |
| conv_12 | 4.967 | 4.915 |
| conv_13 | 4.536 | 1.074 |
| conv_14 | 10.204 | 9.754 |
| conv_15 | 4.75 | 0.993 |
| conv_16 | 10.507 | 9.818 |
| conv_17 | 4.552 | 0.955 |
| conv_18 | 10.422 | 9.746 |
| conv_19 | 4.756 | 0.936 |
| conv_20 | 10.66 | 9.73 |
| conv_21 | 4.593 | 0.944 |
| conv_22 | 10.963 | 10.021 |
| conv_23 | 1.547 | 0.526 |
| conv_24 | 7.317 | 6.854 |
| conv_25 | 3.078 | 0.621 |
| conv_26 | 15.17 | 15.137 |
| pool_0 | 0.313 | 0.317 |
| fc | 0.274 | 0.271 |
| **SUM** | **219.367** | **147.953** |

