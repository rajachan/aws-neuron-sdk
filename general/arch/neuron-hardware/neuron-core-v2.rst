.. _neuroncores-v2-arch:

NeuronCore-v2 Architecture
--------------------------

NeuronCore-v2 is the second generation of the NeuronCore engine,
powering the Trainium NeuronDevices. Each NeuronCore-v2 is a
fully-independent heterogenous compute-unit, with 4 main engines
(Tensor/Vector/Scalar/GPSIMD Engines), and on-chip
software-managed SRAM memory, for maximizing data locality (compiler
managed, for maximum data locality and optimized data prefetch).


.. image:: /images/nc-v2.png

Just like in NeuronCore-v1, The ScalarEngine is optimized for
scalar-computations, in which every element of the output is dependent
on one element of the input. The ScalarEngine is highly parallelized,
and can perform 1,600 floating point operations per cycle (3x speedup
relative to NeuronCore-v1). The NeuronCore-v2 ScalarEngine can handle
various data-types, including cFP8, FP16, BF16, TF32, FP32, INT8, INT16
and INT32. 

The VectorEngine is optimized for vector-computations, in
which every element of the output is dependent on multiple input
elements. Examples include ‘axpy’ operations (Z=aX+Y), Layer
Normalization, Pooling operations, and many more. The VectorEngine is
also highly parallelized, and can perform 2,500 floating points
operations per cycle (10x speedup vs NeuronCore-v1). The NeuronCore-v2
VectorEngine can handle various data-types, including cFP8, FP16, BF16,
TF32, FP32, INT8, INT16 and INT32.

The TensorEngine is based on a power-optimized systolic-array which is
highly optimized for tensor computations (e.g. GEMM, CONV, Reshape,
Transpose), and supports mixed-precision computations (cFP8 / FP16 /
BF16 / TF32 / FP32 / INT8 inputs, FP32 / INT32 outputs). Each
NeuronCore-v2 TensorEngine delivers over 100 TFLOPS of FP16/BF16 tensor
computations (a 6x speedup from NeuronCore-v1). 

NeuronCore-v2 also introduces a new engine, called
GPSIMD-Engine. This engine consists of 8 fully programmable 512-bit wide
general-purpose processors, which can execute straight-line C-code, and
have direct access to the other NeuronCore-v2 engines, as well as the
embedded on-chip SRAM memory. With these cores, customers can implement
custom-operators and execute them directly on the NeuronCore engines.

NeuronCore-v2 also adds support for control-flow, dynamic-shapes, and
programmable :ref:`rounding mode <neuron-rounding-modes>` (RNE & Stochastic-rounding).
