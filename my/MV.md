## MV ##

**Scala:**
```scala
val module = MV(trans: Boolean = false)
```
**Python:**
```python
module = MV(trans=False)
```

It is a module to perform matrix vector multiplication on two mini-batch inputs, producing a mini-batch.

`trans` means whether make matrix transpose before multiplication.


**Scala example:**
```scala
val module = MV()

> module.forward(T(Tensor.range(1, 12, 1).resize(2, 2, 3), Tensor.range(1, 6, 1).resize(2, 3)))
res8: com.intel.analytics.bigdl.tensor.Tensor[Float] =
14.0	32.0
122.0	167.0
[com.intel.analytics.bigdl.tensor.DenseTensor of size 2x2]
```

**Python example:**
```python
Python Code
```
