## Dropout ##

**Scala:**
```scala
val module = Dropout(
  initP: Double = 0.5,
  inplace: Boolean = false,
  scale: Boolean = true)
```
**Python:**
```python
module = Dropout(
  init_p=0.5,
  inplace=False,
  scale=True)
```

Dropout masks(set to zero) parts of input using a bernoulli distribution.
Each input element has a probability `initP` of being dropped. If `scale` is
true(true by default), the outputs are scaled by a factor of `1/(1-initP)` during training.
During evaluating, output is the same as input.

It has been proven an effective approach for regularization and preventing
co-adaptation of feature detectors. For more details, plese see
[Improving neural networks by preventing co-adaptation of feature detectors]
(https://arxiv.org/abs/1207.0580)

**Scala example:**
```scala
val module = Dropout()

val x = Tensor.range(1, 8, 1).resize(2, 4)

module.forward(x)
res: com.intel.analytics.bigdl.tensor.Tensor[Float] =
0.0     4.0     6.0     0.0
10.0    12.0    0.0     16.0
[com.intel.analytics.bigdl.tensor.DenseTensor of size 2x4]

module.backward(x, x.clone().mul(0.5f)) // backward drops out the gradients at the same location.
res14: com.intel.analytics.bigdl.tensor.Tensor[Float] =
0.0    2.0    3.0    0.0
5.0    6.0    0.0    8.0
[com.intel.analytics.bigdl.tensor.DenseTensor of size 2x4]

```

**Python example:**
```python
Python Code
```
